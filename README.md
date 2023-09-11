# API Digigrow Hub

✍🏻 Documentação da API pública do Digigrow Hub (Work in progress)

💬 A API pública da Digigrow é uma interface que permite que desenvolvedores e usuários acessem dados e funcionalidades de nossos produtos e serviços. Com a API, é possível construir aplicativos integrados que oferecem uma experiência personalizada aos usuários.

Ao consumir uma API pública, é importante entender como interagir com os endpoints. Os endpoints esperam receber um corpo de solicitação que contenha os dados necessários para concluir a solicitação.

## Como configurar?

1. Crie uma conta no [Digigrow Hub](https://app.digigrow.com.br/), cadastre sua empresa e aguarde aprovação;
2. Após ter sua empresa aprovada, acesse o [Digigrow Hub](https://app.digigrow.com.br/), selecione no menu de navegação a tela "Configurações" e copie o seu "Token para integrações";
3. Insira o Token copiado como valor do parâmetro "Authorization" de sua chamada, **dentro do Header da requisição**.

## Pedidos

1. Listar um pedido

   ```
   curl --location --request GET 'http://endpointaqui/order' \
   --header 'Authorization: seuTokenAqui' \
   --header 'Content-Type: application/json' \
   --data '{
       "id": 202312345678910
   }'
   ```
   
   Endereço: endpointaqui

   1.1. Inserir o valor do campo "externalId", passar como "id"
   ```json
    {
      "id": 202312345678910
    }
    ```

2. Listar vários pedidos

   ```
   curl --location 'http://endpointaqui/orders?page=1&status=paid&dateStart=2023-01-2&dateEnd=2023-05-3' \
   --header 'Authorization: seuTokenAqui' \
   --data ''
   ```
   
   Endereço: endpointaqui

   Enviar no Params:
   
    | Campo        | Descrição                             |
    |--------------|---------------------------------------|
    | page         | Número da página (paginação)          |
    | status       | Status do pedido                      |
    | dateStart    | Data inicial (ano-mês-dia)            |
    | dateEnd      | Data final (ano-mês-dia)              |
   
   Retorno:
   
    | Campo        | Descrição                             |
    |--------------|---------------------------------------|
    | _id          | Número de identificação do pedido     |
    | externalId   | ?                                     |
    | packId       | ?                                     |
    | createdAt    | Data de início do pedido              |
    | updatedAt    | Data da última atualização do pedido  |
    | status       | Status do pagamento                   |
    | buyer        | Objeto com os dados do comprador      |
    | gross        | ?                                     |
    | receivement  | ?                                     |
    | items        | Objeto com os dados do produto        |
    | payments     | Objeto com os dados de pagamento      |
    | shipping     | Objeto com os dados de envio          |


## Produtos

1. Listar um produto
   
   curl: linkaqui
   
   Endereço: endpointaqui

   ```json
    {
      "id": 202312345678910
    }
    ```

2. Listar vários produtos
   
   curl: linkaqui
   
   Endereço: endpointaqui

   ```json
    {
      "nome": "Exemplo de JSON",
      "descricao": "Isso é um exemplo de um bloco de código JSON em Markdown.",
      "data": "2023-09-06",
      "ativo": true,
      "valores": [10, 20, 30]
    }
    ```

    | Campo        | Descrição                             |
    |--------------|---------------------------------------|
    | Nome         | Nome do cliente                       |
    | Idade        | Idade do cliente                      |
    | Email        | Endereço de e-mail do cliente         |
    | Telefone     | Número de telefone do cliente         |
    | Endereço     | Endereço físico do cliente            |
