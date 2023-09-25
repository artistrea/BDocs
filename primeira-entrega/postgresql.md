---
icon: database
order: 1
---

# PostgreSQL

Não é necessário instalar o PostgreSQL, pois ele será executado em um container Docker. Instale o Docker seguindo as instruções em [primeira-entrega/docker.md](./docker.md).

## Rodando o PostgreSQL

### Iniciando o container

Esteja na pasta que possui o `docker-compose.yml` e execute o comando abaixo para iniciar o container:

```bash
sudo docker-compose up
```

Esse comando inicia o container de acordo com o `docker-compose.yml`:

```yml
version: "3.3"

services:
  db:
    container_name: bd_container
    image: postgres:15.4-alpine
    restart: always
    environment:
      POSTGRES_PASSWORD: 123456
      POSTGRES_USER: bd_projeto
      POSTGRES_DB: bd_projeto_db
      TZ: "America/Sao_Paulo"
    ports:
      - 5436:5432
    volumes:
      # map initialization scripts:
      - ./docker-entrypoint-initdb.d:/docker-entrypoint-initdb.d
#
# Use this PostgreSQL url to connect to the database:
# postgresql://bd_projeto:123456@localhost:5436/bd_projeto_db
```

### Executando comandos no container

É possível executar comandos no container, como `psql`. Para isso entramos no `bash` do container usando o comando `docker-compose exec`:

```bash
sudo docker exec -it bd_container /bin/bash
```

E de dentro do terminal rodamos o comando `psql`:

```bash
psql -U bd_projeto -d bd_projeto_db
```

#### Testando se tudo está funcionando

Usando o que foi visto até agora, podemos testar a conexão com o banco de dados:

Rode em um terminal o banco de dados:

```bash
sudo docker-compose up
```

Em outro terminal veja se os scripts de inicialização foram executados:

```bash
sudo docker exec -it bd_container /bin/bash
psql -U bd_projeto -d bd_projeto_db
\dt
```

Deve ser mostrada a tabela com nome `sometable`:

```bash
            List of relations
 Schema |   Name    | Type  |   Owner
--------+-----------+-------+------------
 public | sometable | table | bd_projeto
(1 row)
```

### Limpando o container

Para limpar totalmente o container, removendo todos os dados, schemas, etc., execute:

```bash
sudo docker-compose down --volumes
```

```bash
psql -h localhost -U bd_projeto -d bd_projeto_db
```
