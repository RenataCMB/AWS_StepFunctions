# Automação de Workflow com AWS Step Functions

## Descrição

Este projeto tem como objetico demonstrar o uso do AWS Step Functions para orquestrar as funções aprendidas até agora em um fluxo automatizado. O fluxo criado simula um processo de validação e aprovação de pedidos com consulta no estoque de produtos.

## Arquitetura

- Serviços usados: Lambda, DynamoDb e SNS

- Fluxo:

  - O cliente faz a requisição de um pedido;
  - O pedido chega ao primeiro Lambda (Recebe o Pedido e Valida o Estoque)
  - Ele faz a consulta ao banco de dados para verificar a quantidade disponível em estoque de determinado produto
  - Tendo estoque como 'true', o fluxo segue para o Lambda (Processar Pagamento) e o pedido fica como 'Pedido Concluído'
  - Caso o estoque seja 'false', será ativado o SNS para encaminhar uma mensagem ao cliente informando que o produto está sem estoque.

  Confira o fluxo completo aqui: [Processar Pedido](./images/processar_pedido.png)
