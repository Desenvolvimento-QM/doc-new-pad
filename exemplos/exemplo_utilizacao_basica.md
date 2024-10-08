
# Exemplo de Utilização Básica

Este exemplo demonstra como acessar variáveis de contexto e utilizar funções básicas dentro de um snippet.

```javascript
function Main(ctx, event_data) {
    // Exibindo o contexto completo no console
    console.log(ctx);

    // Utilizando variáveis de contexto
    console.log("Data Atual: " + ctx.CURRENT_DATE);
    console.log("Usuário Atual: " + ctx.CURRENT_USERNAME);

    // Utilizando funções de contexto
    let customVar = ctx.getCustomVar("minhaVariavel");
    console.log("Valor da Variável Customizada: " + customVar);

    ctx.setCustomVar("minhaVariavel", "novoValor");
    console.log("Novo Valor da Variável Customizada: " + ctx.getCustomVar("minhaVariavel"));

    let dataSource = ctx.getDataSource("minhaFonteDeDados");
    console.log("Fonte de Dados: " + dataSource);

    let urlParam = ctx.getUrlParam("meuParametro");
    console.log("Parâmetro de URL: " + urlParam);
}
```
