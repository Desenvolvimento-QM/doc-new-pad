
# Exemplo: Definir Recursos de um Usuário

Este exemplo demonstra como definir recursos para um usuário específico utilizando o contexto.

```javascript
async function Main(ctx, event_data) {
    const usersContext = ctx.user; // Acessando o contexto de usuários
    const resourcesContext = ctx.resources; // Acessando o contexto de recursos
   
    // Listando todos os recursos disponíveis
    const availableResources = await resourcesContext.getResources();
    console.log('Recursos disponíveis:', availableResources);

    // Pega apenas os nomes
    const resources_names = availableResources.map(({name})=> name)

    // Definindo todos os recursos para o usuário 'johndoe'
    await usersContext.setResources('johndoe', resources_names);

    console.log(`Recursos '${resources_names.join(', ')}' definidos para o usuário 'johndoe'`);

}
```
