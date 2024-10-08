
# Gerenciamento de Recursos

Neste exemplo, mostramos como acessar e listar recursos usando o contexto.

```javascript
async function Main(ctx, event_data) {
    const resourcesContext = ctx.resources; // Acessando o contexto de recursos

    // Obtendo todos os recursos disponíveis
    const resources = await resourcesContext.getResources();
    console.log("Recursos disponíveis:", resources);
}
```
