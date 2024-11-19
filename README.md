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
    }
]
```

##### Falha na autenticação | 401
Ocorreu um erro durante o processo de validação do token,
possíveis causas podem ser: 
* token vazio;
* token inválido.





