# Teste para casa - Engenharia de Dados - Pipelines Junior

### Proposta

Temos a seguinte tabela de sellers que contém os cadastros de todos os lojistas do PicPay. 

[exemplo tabela]
| Column | Type | Descrição |
| ------ | ------ | ------ |
| id_seller | long | Identificador da tabela |
| seller_name | varchar | Nome do estabelecimento |
| cnpj | varchar | CNPJ do lojista |
| seller_address | varchar | Endereço do lojista |
| created_at | date | Data de criação do cadastro do lojista |
| updated_at | date | Data de atualização do cadastro do lojista |

&nbsp;

Temos a seguinte tabela de users que contém os cadastros de todos os usuários Pessoa Física do PicPay. 

[exemplo tabela]

| Column | Type | Descrição |
| ------ | ------ | ------ |
| id_user | long | Identificador da tabela |
| user_name | varchar | Nome do usuário |
| cpf | varchar | CPF do usuário |
| dt_nasc | date | Data de nascimento do usuário |
| user_address | varchar | Endereço do usuário |
| created_at | date | Data de criação do cadastro do usuário |
| updated_at | date | Data de atualização do cadastro do usuário |

&nbsp;

### Modelagem

Modele as mesmas, para gerar uma tabela com as transações dos respectivos usuários/lojistas, levando em consideração que um usuário pode realizar o pagamento para um ou mais lojistas e/ou usuários. E um lojista pode realizar o pagamento para um ou mais lojistas e/ou usuários. 

Vamos precisar de algumas informações adicionais como data em que o pagamento foi realizado, quem recebe e quem realiza o pagamento, a localização, se houve cashback para quem realizou aquele pagamento, seja criativo!

### Dúvidas

Caso tenha dúvidas, pode entrar em contato pelo email **data.engineering@picpay.com**, utilizando o título **[DÚVIDA] Nome do Candidato - Data Pipelines Junior**.

### Submissão

 O teste deverá ser entregue em até 7 dias a partir da data de recebimento. Tudo deve estar contido em um único notebook, que deverá ser exportado do Databricks (File > Export > Source File) e enviado para o email **data.engineering@picpay.com**, utilizando o título **[TESTE] Nome do Candidato - Data Pipelines Junior**.





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