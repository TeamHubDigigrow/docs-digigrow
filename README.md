<p align="center">
    <img src="https://github.com/TeamHubDigigrow/docs-digigrow/assets/9470353/20c36c7d-1fec-46db-95bb-c4d6e00ab20b" width="500px"/>
</p>
<br/>

✍🏻 Documentação da API pública do Digigrow Hub

💬 A API pública da Digigrow é uma interface que permite que desenvolvedores e usuários acessem dados e funcionalidades de nossos produtos e serviços. Com a API, é possível construir aplicativos integrados que oferecem uma experiência personalizada aos usuários.

Ao consumir uma API pública, é importante entender como interagir com os endpoints. Os endpoints esperam receber um corpo de solicitação que contenha os dados necessários para concluir a solicitação.

## Como configurar?

1. Crie uma conta na [Digigrow](https://app.digigrow.com.br/), cadastre sua empresa e aguarde aprovação;
2. Após ter sua empresa aprovada, acesse a [Digigrow](https://app.digigrow.com.br/), selecione no menu de navegação a tela "Configurações" e copie o seu "Token para integrações";
3. Insira o Token copiado como valor do parâmetro "Authorization" de sua chamada, **dentro do Header da requisição**.

## Pedidos

1. Listar um pedido (GET)
   
   1.1 passar número da venda no endereço como "id"

   ```
   curl --location --request GET 'https://api.digigrow.com.br/public/order/:id' \
   --header 'Authorization: seuTokenAqui' \
   --header 'Content-Type: application/json' \
   ```
   
   Endereço: https://api-v1.digigrow.com.br/order/:id
   

2. Listar vários pedidos (GET)

   ```
   curl --location 'https://api.digigrow.com.br/public/orders?page=1&status=paid&dateStart=2023-01-2&dateEnd=2023-05-3' \
   --header 'Authorization: seuTokenAqui' \
   ```
   
   Endereço: https://api-v1.digigrow.com.br/orders

   Enviar no Params:
   
    | Campo        | Descrição                             |
    |--------------|---------------------------------------|
    | page               | Número da página (paginação)    |
    | dateStart(opcional)| Data inicial (ano-mês-dia)      |
    | dateEnd(opcional)  | Data final (ano-mês-dia)        |
   
   Retorno:
```
   [
    {
        "_id": string,
        "externalId": number,
        "packId": null,
        "createdAt": "string",
        "updatedAt": "string",
        "sellerId": "string",
        "status": "string",
        "buyer": {
            "buyerId": number,
            "name": "string",
            "email": "string",
            "document": "string",
            "documentType": "string",
            "phone": "string"
        },
        "gross": number,
        "receivement": number,
        "items": [
            {
                "title": "string",
                "sku": "string",
                "unitPrice": number,
                "gross": number,
                "amount": number,
                "saleFee": number
            }
        ],
        "payments": [
            {
                "paymentId": number,
                "method": "string",
                "status": "string",
                "installments": number,
                "value": number
            }
        ],
        "shipping": {
            "status": null,
            "estimateDeliveryDate": "string",
            "city": "string",
            "state": "string",
            "country": "BR",
            "street": "string",
            "neighborhood": "string",
            "number": "string",
            "comment": "string",
            "address": "string",
            "zipCode": "string",
            "trackingNumber": ?
        }
    }
```

## Produtos

1. Get de produto (GET)
   
   1.1. Passar o valor do sku no endereço da chamada
   ```
     curl --location --request GET 'https://api.digigrow.com.br/public/product/:id' \
      --header 'Authorization: seuTokenAqui'
   ```
   
   Endereço: https://api-v1.digigrow.com.br/product/:id
   

2. Listar vários produtos (GET)
   
   ```
   curl --location 'https://api.digigrow.com.br/public/products?page=1' \
   --header 'Authorization: seuTokenAqui' \
   --data ''
   ```
   
   Endereço: https://api-v1.digigrow.com.br/products
   

   Enviar no Params:
   
    | Campo        | Descrição                             |
    |--------------|---------------------------------------|
    | page         | Número da página (paginação)          |

   
   Retorno:
```
       {
        "_id": "6500ba4265e46de1d9cdc3ff",
        "sellerId": "650074a1cfd124b873fa0616",
        "sku": "P123",
        "attributes": [
            {
                "id": "BRAND",
                "value_type": "string",
                "value_name": "string",
                "values": "",
                "name": "string",
                "tags": [
                    "catalog_listing_required",
                    "catalog_required",
                    "required"
                ]
            },
            {
                "id": "MODEL",
                "value_type": "string",
                "value_name": "Modelo",
                "values": "",
                "name": "Modelo",
                "tags": [
                    "hidden"
                ]
            }
        ],
        "category": "string",
        "depth": number,
        "description": "string",
        "height": number,
        "invoiceInvento": {
            "CfopInterno": ?,
            "CfopInterestadual": ?,
            "CfopInternoDevolucao": ?,
            "CfopInterestadualDevolucao": ?,
            "OrigemMercadoria": ?,
            "CofinsCst": ?,
            "DadosAdicionais": ?,
            "IcmsCst": ?,
            "IpiCst": ?,
            "PisCst": ?,
            "ncm": number,
            "cest": number
        },
        "isActive": boolean,
        "title": "string",
        "updatedAt": "string",
        "virtual": boolena,
        "warning": ?,
        "warrantyTime": "string",
        "warrantyTimeUnit": "string",
        "warrantyType": "string",
        "weight": number,
        "width": number,
        "stagedPic": boolean
    }
   ```

3. Criar um produto (POST)

   ```
   curl --location --request POST 'https://api.digigrow.com.br/public/product' \
   --header 'Authorization: seuTokenAqui' \
   --header 'Content-Type: application/json' \
   ```
   
   Endereço: https://api-v1.digigrow.com.br/product
   

   Enviar no body:

 ```
    {
    "sku": "string",
    "gtin": "string",
    "title": "string",
    "price": number,
    "stock": number,
    "cest": "string",
    "ncm": "string",
    "image": ["string dentro de um array"],
    "weight": number,
    "width": number,
    "height": number,
    "depth": number,
    "perPackage": number,
    "description": "string",
    "brand": "string",
    "attributes" : [
     {
        "string": "string"
     }
   ]
}
   ```
   
4. Alterar um produto (PUT)
   
   4.1. É obrigatório passar o sku do produto no Params da chamada. Abaixo segue exemplo dos campos a serem enviados para alterar o produto.

   ```
   curl --location --request PUT 'https://api.digigrow.com.br/public/product/:id' \
   --header 'Authorization: seuTokenAqui' \
   --header 'Content-Type: application/json' \
   ```

   Endereço: https://api-v1.digigrow.com.br/product/:id

   
   Enviar no body:
```
{
    "title": "(opcional, string)",
    "price": (opcional, number),
    "stock": (opcional, number),
    "cest": "(opcional, string)",
    "ncm": "(opcional, string)",
    "image": (opcional, [url da imagem dentro de array]),
    "weight": (opcional),
    "width": (opcional),
    "height": (opcional),
    "depth": (opcional),
    "perPackage": (opcional),
    "description": "(opcional)",
    "brand": "(opcional, string"),
    "status": boolean
}
```
