
# Documentação para Uso da Ferramenta de Automação

## Introdução
Esta ferramenta permite que os usuários criem Automações que são injetadas e executados em tempo de execução.
A seguir, detalhamos as variáveis de contexto, funções disponíveis e classes utilitárias que você pode utilizar dentro dos seus snippets.

## Variáveis de Contexto
Ao criar um snippet, você terá acesso às seguintes variáveis de contexto:

- **CURRENT_DATE**: Data atual no formato `dd/MM/yyyy`.
  - Exemplo: `24/05/2024`

- **CURRENT_DATETIME**: Data e hora atuais no formato `dd/MM/yyyy, HH:mm:ss`.
  - Exemplo: `24/05/2024, 15:42:19`

- **CURRENT_USERNAME**: Nome de usuário atual.
  - Exemplo: `wendell.vieira`

- **CURRENT_USER_EMAIL**: E-mail do usuário atual.
  - Exemplo: `wendell.vieira@qwst.co`

- **CURRENT_USER_RESOURCE_ROLES**: Funções de recurso do usuário atual.
  - Exemplo: `["admin", "contributor"]`

- **CURRENT_WEEKDAY**: Dia da semana atual.
  - Exemplo: `sexta-feira`

- **CURRENT_YEAR**: Ano atual.
  - Exemplo: `2024`

- **PROJECT_NAME**: Nome do projeto.
  - Exemplo: `Santander`

- **PUBLISH_VERSION**: Versão de publicação.
  - Exemplo: `v13`

- **SELECTED_ITEM_DESCRIPTION**: Descrição do item selecionado.
  - Exemplo: `-`

- **SELECTED_ITEM_NAME**: Nome do item selecionado.
  - Exemplo: `Conteúdo 1`

## Funções Disponíveis
Além das variáveis de contexto, as seguintes funções estão disponíveis para uso:

### `getCustomVar(name: string): any`
Retorna o valor de uma variável customizada pelo nome.
- Exemplo de uso: `ctx.getCustomVar("minhaVariavel")`

### `setCustomVar(name: string, value: any): void`
Define o valor de uma variável customizada.
- Exemplo de uso: `ctx.setCustomVar("minhaVariavel", "novoValor")`

### `getDataSource(name: string): any`
Retorna a fonte de dados especificada pelo nome.
- Exemplo de uso: `ctx.getDataSource("minhaFonteDeDados")`

### `getUrlParam(name: string): any`
Retorna o valor de um parâmetro de URL especificado pelo nome.
- Exemplo de uso: `ctx.getUrlParam("meuParametro")`

## Classes Utilitárias
Estas classes fornecem métodos para gerenciamento de usuários, papéis e recursos.

### `AdvScript_Context_Users`
Classe para gerenciamento de usuários.
- **Métodos**:
  - `get(username: string)`: Retorna informações de um usuário pelo `username`.
  - `list(params: iTableReadParams)`: Lista usuários com base nos parâmetros fornecidos. [Ver detalhes de `iTableReadParams`](./interfaces.md#itableReadParams).
  - `create(user: CreateUserDto)`: Cria um novo usuário. [Ver detalhes de `CreateUserDto`](./interfaces.md#createuserdto).
  - `update(user: Partial<UpdateUserDto>)`: Atualiza informações de um usuário. [Ver detalhes de `UpdateUserDto`](./interfaces.md#updateuserdto).
  - `delete(username: string)`: Deleta um usuário pelo `username`.
  - `resetPassword(username: string)`: Reseta a senha de um usuário.
  - `setRole(username: string, role: iRealmRolesOptions)`: Define o papel do usuário. [Ver detalhes de `iRealmRolesOptions`](./interfaces.md#irealmrolesoptions).
  - `setResources(username: string, resources: string[])`: Define os recursos de um usuário.

### `AdvScript_Context_Roles`
Classe para listagem de papéis disponíveis.
- **Métodos**:
  - `list()`: Retorna a lista de papéis disponíveis. [Ver detalhes de `iRealmRolesOptions`](./interfaces.md#irealmrolesoptions).

### `AdvScript_Context_Resources`
Classe para gerenciamento de recursos.
- **Métodos**:
  - `getResources()`: Retorna todos os recursos disponíveis.

## Exemplo de Código
Abaixo estão exemplos detalhados de como utilizar as variáveis de contexto, funções e classes dentro de um snippet:

### Exemplo 1: Gerenciamento de Usuários
```javascript
async function manageUser(ctx) {
    const usersContext = new AdvScript_Context_Users();

    // Criando um novo usuário
    const newUser = {
        username: "johndoe",
        enabled: true,
        emailVerified: true,
        updatePassword: false,
        firstName: "John",
        lastName: "Doe",
        email: "johndoe@example.com",
        locale: "en",
        default_role: "contributor"
    };
    await usersContext.create(newUser);

    // Listando usuários
    const userList = await usersContext.list({ search: "john" });
    console.log("Usuários encontrados:", userList);

    // Atualizando um usuário
    await usersContext.update({ id: userList[0].id, email: "john.new@example.com" });

    // Resetando senha de um usuário
    await usersContext.resetPassword("johndoe");

    // Deletando um usuário
    await usersContext.delete("johndoe");
}
```

### Exemplo 2: Listagem de Papéis
```javascript
async function listRoles(ctx) {
    const rolesContext = new AdvScript_Context_Roles();

    // Listando papéis disponíveis
    const roles = await rolesContext.list();
    console.log("Papéis disponíveis:", roles);
}
```

### Exemplo 3: Gerenciamento de Recursos
```javascript
async function manageResources(ctx) {
    const resourcesContext = new AdvScript_Context_Resources();

    // Obtendo todos os recursos disponíveis
    const resources = await resourcesContext.getResources();
    console.log("Recursos disponíveis:", resources);
}
```

## Considerações Finais
Esta ferramenta oferece uma maneira flexível e poderosa de personalizar o comportamento do seu aplicativo em tempo de execução.
Utilize as variáveis de contexto e funções disponíveis para obter informações dinâmicas e interagir com os dados de forma eficiente.

Para quaisquer dúvidas ou mais informações, entre em contato com o suporte técnico.
