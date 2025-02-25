![alt text](https://www.impacta.edu.br/themes/wc_agenciar3/images/logo-new.png)
# Sistema de Gestão de Endereço

Este é um sistema de gestão de endereço. O objetivo principal é permitir que o usuário se cadastre, faça login e gerencie seus endereços.

## Funcionalidades

- **Cadastro de Usuário**: O usuário deve se registrar no sistema, fornecendo informações como nome, e-mail, CPF e outros dados necessários.
- **Ativação de Conta**: Após o cadastro, o sistema envia um e-mail de ativação. O usuário precisa clicar no link enviado para ativar a conta.
- **Login**: Após ativação da conta, o usuário pode fazer login no sistema com e-mail e senha, recebendo um token JWT para autenticação.
- **Gestão de Endereços**: O usuário pode cadastrar, listar, visualizar detalhes e excluir endereços.
- **Logout**: O usuário pode fazer logout do sistema.

## Endpoints da API

### Cadastro de Usuário
- **Requisição**
    ```bash
    curl -X POST http://<API_URL>/register \
        -H "Content-Type: application/json" \
        -d '{
            "name": "Leanna",
            "email": "leanna1454@uorak.com",
            "user_type_id": 1,
            "password": "123456",
            "cpf_cnpj": "69172804025",
            "terms": 1,
            "birthday": "2000-10-12"
        }'
    ```
- **Resposta**: Envio de um e-mail de ativação.

### Login
- **Requisição**
    ```bash
    curl -X POST http://<API_URL>/login \
        -H "Content-Type: application/json" \
        -d '{
            "email": "carlosr.m.fernandes@gmail.com",
            "password": "123456",
            "user_type_id": 1
        }'
    ```
- **Resposta**
    ```json
    {
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodtZWZjOWM5NTgyNjg3Lmhlcm9rdWFwcC5jb20vYXBpL2xvZ2luIiwiaWF0IjoxNzEyMDc4Mjg0LCJuYmYiOjE3MTIwNzgyODQsImp0aSI6ImRPajVkTng4WEgxdVJ5TVkiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.oBAOYBcADNUiwFKgM",
    "token_type": "bearer",
    "expires_in": null,
    "user": {
        "id": 1,
        "name": "xxxxxxxxxx",
        "is_active": true,
        "is_socialite": false,
        "terms": true,
        "cpf_cnpj": "xxxxxxxxxx",
        "email": "xxxxxxxxx@gmail.com",
        "user_type_id": 1,
        "birthday": "xxxx-xx-xx",
        "phone": "xxxxxxxxx",
        "avatar": null,
        "attachment": null,
        "document_status": null,
        "created_at": "2024-03-14T15:08:44.000000Z"
    }

### Gestão de Endereços

#### Cadastro de Endereço
- **Requisição**
    ```bash
    curl -X POST http://<API_URL>/addresses \
        -H "Content-Type: application/json" \
        -H "Authorization: Bearer <JWT_TOKEN>" \
        -d '{
            "title": "Minha Casa",
            "cep": "03730000",
            "address": "Rua Brazópolis Jardim Jaú (Zona Leste)",
            "number": "8A",
            "complement": ""
        }'
    ```

#### Listar Endereços
- **Requisição**
    ```bash
    curl -X GET http://<API_URL>/addresses \
        -H "Authorization: Bearer <JWT_TOKEN>"
    ```

#### Visualizar Detalhes de Endereço
- **Requisição**
    ```bash
    curl -X GET http://<API_URL>/addresses/{id} \
        -H "Authorization: Bearer <JWT_TOKEN>"
    ```

#### Deletar Endereço
- **Requisição**
    ```bash
    curl -X DELETE http://<API_URL>/addresses/{id} \
        -H "Authorization: Bearer <JWT_TOKEN>"
    ```

### Logout
- **Requisição**
    ```bash
    curl -X POST http://<API_URL>/logout \
        -H "Authorization: Bearer <JWT_TOKEN>"
    ```

## Estrutura de Diretórios

Aqui está um exemplo da estrutura de diretórios do projeto:

