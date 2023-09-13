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
   passar número da venda no endereço como "id"

   ```
   curl --location --request GET 'http://endpointaqui/order/:id' \
   --header 'Authorization: seuTokenAqui' \
   --header 'Content-Type: application/json' \
   ```
   
   Endereço: endpointaqui

3. Listar vários pedidos

   ```
   curl --location 'http://endpointaqui/orders?page=1&status=paid&dateStart=2023-01-2&dateEnd=2023-05-3' \
   --header 'Authorization: seuTokenAqui' \
   ```
   
   Endereço: endpointaqui

   Enviar no Params:
   
    | Campo        | Descrição                             |
    |--------------|---------------------------------------|
    | page               | Número da página (paginação)    |
    | dateStart(opcional)| Data inicial (ano-mês-dia)      |
    | dateEnd(opcional)  | Data final (ano-mês-dia)        |
   
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

1. Get de produto
   1.1. Passar o valor do sku no endereço da chamada
   ```
     curl --location --request GET 'http://endpointaqui.com/product/:id' \
      --header 'Authorization: "seutoken"'
   ```
   
   Endereço: endpointaqui

   

2. Listar vários produtos
   
   ```
   curl --location 'http://endpointaqui/products?page=1' \
   --header 'Authorization: seuTokenAqui' \
   --data ''
   ```
   
   Endereço: endpointaqui

   Enviar no Params:
   
    | Campo        | Descrição                             |
    |--------------|---------------------------------------|
    | page         | Número da página (paginação)          |

   
   Retorno:
   
    | Campo        | Descrição                             |
    |--------------|---------------------------------------|
    | title        | Título do produto                     |
    | sku          | Código de identificação do produto    |
