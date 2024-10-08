
# Listagem de Papéis

Este exemplo demonstra como listar os papéis disponíveis utilizando o contexto.

```javascript
async function Main(ctx, event_data) {
    const rolesContext = ctx.roles; // Acessando o contexto de papéis

    // Listando papéis disponíveis
    const roles = await rolesContext.list();
    console.log("Papéis disponíveis:", roles);
}
```
