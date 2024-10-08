
# Gerenciamento de Usuários

Neste exemplo, demonstramos como criar, listar, atualizar e deletar usuários utilizando o contexto.

```javascript
async function Main(ctx, event_data) {
    const usersContext = ctx.user; // Acessando o contexto de usuários
    const username = "johndoe-2024";
    // Criando um novo usuário
    const newUser = {
        username,
        emailVerified: true,
        enabled: true,
        firstName: "John",
        lastName: "Doe",
        email: "johndoe@example.com",
        locale: "en",
        default_role: "contributor"
    };
    await usersContext.create(newUser);

    // Listando usuários
    const userList = await usersContext.list({ username });
    console.log("Usuários encontrados:", userList);

    // Atualizando um usuário
    await usersContext.update(username, { email: "john.new@example.com" });

    // Resetando senha de um usuário
    await usersContext.resetPassword(username);

    // Deletando um usuário
    await usersContext.delete(username);
}
```
