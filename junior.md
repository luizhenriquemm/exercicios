### Minha solução

Tabela transactions
| Column | Type | Descrição |
| ------ | ------ | ------ |
| id_transaction | long | Identificador da tabela (PK) |
| payer_type | integer | 1: quando o pagador for pessoa fisica, 2: quando o pagador for lojista |
| payer_id | long | Identificador do pagador, seja qual for o tipo |
| payee_type | integer | 1: quando o pagador for pessoa fisica, 2: quando o pagador for lojista |
| payee_id | long | Identificador do recebedor |
| value | float | Valor pago |
| payed_at | date | Data do pagamento feito pelo pagador |
| status | integer | 0: quando a transacao foi efetivada ou o código do erro ocorrido |
| payer_location_lat | float | Coordenadas geograficas do pagador no momento da transação |
| payer_location_long | float | Coordenadas geograficas do pagador no momento da transação |
| cashback_percentual | float | Percentual do cashback pago ao pagador, quando a transação é elegivel, o percentual é registrado aqui e o cashback já é pago e registrado em outra tabela |
