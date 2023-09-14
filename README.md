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

3. Criar um produto

   ```
   curl --location --request POST 'http://endpointaqui/product' \
   --header 'Authorization: seuTokenAqui' \
   --header 'Content-Type: application/json' \
   ```
   Enviar no body:
   
   | Campo        | Descrição                             |
   |--------------|---------------------------------------|
   | sku          | sku do produto  (String)              |
   | gtin         | gtin do produto  (String)             |
   | title        | Título do produto  (String)           |
   | price        | Preço do produto   (Number)           |
   | stock        | Estoque do produto   (Number)         |
   | cest         | CEST do produto   (String)            |
   | ncm          | NCM do produto    (String)            |
   | image        | Enviar URL da imagem                  |
   | weight       | Peso do produto   (Number)            |
   | width        | Largura do produto   (Number)         |
   | height       | Altura do produto   (Number)          |
   | depth        | Profundidade do produto   (Number)    |
   | description  | Descrição do produto  (String)        |
   
   Endereço: endpointaqui
   
5. Alterar um produto
   4.1. É obrigatório passar o sku do produto no Params da chamada. Abaixo segue exemplo dos campos a serem enviados para alterar o produto.

   ```
   curl --location --request PUT 'http://endpointaqui/product/:id' \
   --header 'Authorization: seuTokenAqui' \
   --header 'Content-Type: application/json' \
   ```
   Enviar no body:
   
   | Campo                  | Descrição                             |
   |------------------------|---------------------------------------|
   | title(opcional)        | Título do produto  (String)           |
   | price(opcional)        | Preço do produto   (Number)           |
   | stock(opcional)        | Estoque do produto   (Number)         |
   | cest(opcional)         | CEST do produto   (String)            |
   | ncm(opcional)          | NCM do produto    (String)            |
   | image(opcional)        | Enviar URL da imagem                  |
   | weight(opcional)       | Peso do produto   (Number)            |
   | width(opcional)        | Largura do produto   (Number)         |
   | height(opcional)       | Altura do produto   (Number)          |
   | depth(opcional)        | Profundidade do produto   (Number)    |
   | description(opcional)  | Descrição do produto  (String)        |
   
   Endereço: endpointaqui
