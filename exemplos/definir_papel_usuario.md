
# Exemplo: Definir Papel de um Usuário

Este exemplo demonstra como definir um papel para um usuário específico utilizando o contexto.

```javascript
async function Main(ctx, event_data) {
    const usersContext = ctx.users; // Acessando o contexto de usuários
    const rolesContext = ctx.roles; // Acessando o contexto de papéis

    // Verificando os papéis disponíveis após a alteração
    const availableRoles = await rolesContext.list();
    console.log('Papéis disponíveis:', availableRoles);

    // Definindo um papel para o usuário 'johndoe'
    const roleToSet = availableRoles[0].value; // Papel desejado 'admin'
    await usersContext.setRole('johndoe', roleToSet);

    console.log(`Papel '${roleToSet}' definido para o usuário 'johndoe'`);

}
```
