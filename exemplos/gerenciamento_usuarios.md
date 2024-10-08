
# Gerenciamento de Usuários

Neste exemplo, demonstramos como criar, listar, atualizar e deletar usuários utilizando o contexto.

```javascript
async function Main(ctx, event_data) {
    const usersContext = ctx.users; // Acessando o contexto de usuários

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
