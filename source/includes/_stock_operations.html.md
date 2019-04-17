# Operações de estoque

Todas as operações de atualização do estoque são feitas em processos assíncronos. Para ter informações do progresso e estado atual da operação, é fornecido um identificador único da operação no fim de toda ação de atualização da API.

Com esse ID, é possível saber o estado atual da operação, quantas inserções foram feitas com sucesso, quantas inserções tiveram falhas ao serem executadas, entre outras informações.

## Atributos de operações de estoque

As entidades de operação de estoque possuem atributos que seguem padrões de preenchimento. Nessa seção, vamos conferir quais são esses atributos e os valores possíveis de cada um.

### Status

As operações de estoque têm um estado e esse estado muda conforme a operação é executada.

Lista de valores possíveis do campo `status`:

| Valor | Descrição |
| ----- | --------- |
| created | Operação criada |
| validating | Operação em processo de validação |
| validation_ok | Operação validada com sucesso |
| validation_error | Erro ao validar a operação |
| applying | Aplicando operação na base de dados |
| success | Operação aplicada com sucesso |
| error | Erro ao aplicar operação |

## Informações de uma operação de estoque específica

> Exemplo de requisição

```shell
curl "https://stock.querobolsa.com.br/api/stock_operations/4e8c23c3-fab1-486d-9c0e-c49301305d94" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json'
```

> Exemplo de retorno JSON para esta requisição:

```json
{
  "id": "4e8c23c3-fab1-486d-9c0e-c49301305d94",
  "status": "success",
  "success_count": 2,
  "error_count": 0,
  "validation_success_count": 2,
  "validation_error_count": 0,
  "created_at": "2019-04-10T03:15:44Z",
  "finished_at": "2019-04-10T03:16:15Z"
}
```

Retorna dados de operação de estoque específica.

### Requisição HTTP

`GET https://stock.querobolsa.com.br/api/stock_operations/<STOCK_OPERATION_ID>`

### Parâmetros da requisição

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| STOCK_OPERATION_ID | path | ID da universidade onde deseja realizar a ação |

### Parâmetros da resposta

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| id | string | Código identificador de operação de estoque |
| status | string | Estado atual da operação de estoque |
| success_count | integer | Número de operações no banco de dados realizadas com sucesso |
| error_count | integer | Número de operações no banco de dados realizadas que falharam |
| validation_success_count | integer | Número de operações no banco de dados que foram validadas com sucesso |
| validation_error_count | integer | Número de validações de operações no banco de dados que falharam |
| created_at | string | Data e hora combinadas da criação da operação de estoque em formato UTC [ISO 8601](https://pt.wikipedia.org/wiki/ISO_8601) |
| finished_at | string | Data e hora combinadas da finalização da operação de estoque em formato UTC [ISO 8601](https://pt.wikipedia.org/wiki/ISO_8601) |
