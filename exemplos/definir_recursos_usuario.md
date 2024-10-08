
# Exemplo: Definir Recursos de um Usuário

Este exemplo demonstra como definir recursos para um usuário específico utilizando o contexto.

```javascript
async function Main(ctx, event_data) {
    const usersContext = ctx.users; // Acessando o contexto de usuários
    const resourcesContext = ctx.resources; // Acessando o contexto de recursos

    // Definindo recursos para o usuário 'johndoe'
    const resourcesToSet = ['resource1', 'resource2', 'resource3']; // Recursos desejados
    await usersContext.setResources('johndoe', resourcesToSet);

    console.log(`Recursos '${resourcesToSet.join(', ')}' definidos para o usuário 'johndoe'`);

    // Listando todos os recursos disponíveis
    const availableResources = await resourcesContext.getResources();
    console.log('Recursos disponíveis:', availableResources);
}
```
