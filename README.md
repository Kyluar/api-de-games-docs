# Api de games

Esta api foi criada para aplicar os conceitos aprendidos no curso "Formação Node.js" ministrado por Victor Lima do "Guia do Programador".


## Endpoints

### GET /games
Esse endpoint é responsável por retornar um array de objetos com todos os games armazenados no banco de dados.

#### Parâmetros
Nenhum

#### Respostas

##### OK | 200
O processo foi um sucesso e os dados serão retornados. Exemplo de resposta:
```
[
    {
        "id": 23,
        "title": "Call of Duty MW",
        "year": 2019,
        "price": 60
    },
    {
        "id": 15,
        "title": "DragonQuest Legends",
        "year": 2024,
        "price": 59.99
    },
    {
        "id": 22,
        "title": "CyberTech Warfare",
        "year": 2023,
        "price": 69.99
    },
    ...
]
```

##### Falha na autenticação | 401
Ocorreu um erro durante o processo de validação do token,
possíveis causas podem ser: 
* token vazio;
* token inválido.

Retornos:
* res.send('Token vazio.')
* res.send('Token inválido.')


### POST /auth
Esse endpoint é responsável por realizar o processo de login de um usuário já cadastrado, permitindo o acesso aos dados protegidos por autenticação.

#### Parâmetros
email: email do usuário.
password: senha do usuário.

Ex.:
```
{
    "email": "email@example.com",
    "password": "P@ssWordExample123"
}
```

#### Respostas

##### OK | 200
Retorna o token para autenticação dos endpoints.
Ex.:
```
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MCwiZW1haWwiOiJhZG1pbiIsImlhdCI6MTczMjAzNDg0OCwiZXhwIjoxNzMyMTIxMjQ4fQ.9S8VeKcgO2rcsMJau4U0j5jzHDZY0svNY0PbkO110N0"
}
```

##### Email não cadastrado no banco de dados | 404
Esse erro ocorre quando o processo é incapaz de localizar o email passado por parâmetro no banco de dados. Ex.:

```
{
    err: `O email "${email}" não foi encontrado.`
}
```

##### Senha inválida | 400
Esse erro ocorre quando a senha do usuário cadastrado no banco de dados difere com a senha passada por parâmetro. Ex.:

```
{
    err: `Senha inválida.`
}
```

##### Falha interna | 500
Esse erro ocorre quando há uma falha interna do servidor. Ex.:

```
{
    err: `Falha interna.`
}
```

