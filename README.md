<div align="right">

### ⚡ RMM ⚡

</div>
# Docker | **`Mysql`**

![License](https://img.shields.io/badge/license-MIT-green?style=plastic) ![Github](https://img.shields.io/badge/-Github-000?style=plastic&logo=github) ![Docker](https://img.shields.io/badge/-Docker-blue?style=plastic&logo=docker) ![Mysql](https://img.shields.io/badge/-MySql-fefefe?style=plastic&logo=mysql)


Banco de dados Mysql rodando em Docker. Imagem a partir do Mysql oficial com pequenos ajustes para subir um banco de dados de exemplo.

Este repo utilizo para desenvolvimento, POCs e testes ou aprendizado de novas tecnologias e não recomendo utilizar em produção.

## Características

- Mysql > 8.x
- Script exemplo `Sakila`
## Requerimentos

- Docker Desktop versão maior que 18.x

## Instalando

Primeiro o clone

```
$ git clone git@github.com:ricardo-melo-martins/docker-mysql.git
```

acesse o diretório `docker-mysql` 

```
$ cd docker-mysql
```

Para gerar a imagem do Mysql, digite então:

```bash
$ ./.rmm/docker build mysql
```
`ou`
```bash
$ sh .rmm/docker build mysql
```

Deverá ter um resultado como
```
INFO: Docker Build

docker build
[+] Building 2.1s (10/10) FINISHED
 => [internal] load build definition from Dockerfile                                                    0.0s  => => transferring dockerfile: 32B                                                                     0.0s  => [internal] load .dockerignore                                                                       0.0s  => => transferring context: 2B                                                                         0.0s  => [internal] load metadata for docker.io/library/mysql:8.0                                            1.8s  => [internal] load build context                                                                       0.0s  => => transferring context: 334B                                                                       0.0s  => [1/5] FROM docker.io/library/mysql:8.0@sha256:0eb33f0094ef5351639d9d9847c963ee9f22f5631cde046babd4  0.0s  => CACHED [2/5] COPY /.rmm/.docker/mysql/script/sakila/sakila-schema.sql /docker-entrypoint-initdb.d/  0.0s  => CACHED [3/5] COPY /.rmm/.docker/mysql/script/sakila/sakila-data.sql /docker-entrypoint-initdb.d/02  0.0s  => CACHED [4/5] RUN ln -snf /usr/share/zoneinfo/UTC /etc/localtime && echo UTC > /etc/timezone && cho  0.0s  => CACHED [5/5] RUN apt-get update  && apt-get install --no-install-recommends -y   locales  && rm -r  0.0s  => exporting to image                                                                                  0.1s  => => exporting layers                                                                                 0.0s  => => writing image sha256:7841e3757dd097184e6e440492698aa255690319945d240974f13e5269351d76            0.0s  => => naming to docker.io/library/rmm_mysql                                                            0.0s

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them

SUCCESS: Docker Build OK

```

Em seguida, para "subir" um container usando a imagem criada, digite:

```
$ .rmm/docker up mysql
```

## Banco de dados Sakila

Base de dados Sakila é um modelo criado para testes.  Veja mais em [mysql.com/doc/sakila/en](https://dev.mysql.com/doc/sakila/en)


## Tabelas

Tabelas disponíveis (em ordem alfabética)
```
- actor
- address
- category
- city
- country
- customer
- film
- film_actor
- film_category
- film_text
- inventory
- language
- payment
- rental
- staff
- store
```
# Esquemas

Visão geral EER 

![Imagem](/docs/images/sakila-er.png 'Esquema do Banco de dados Sakila')

Visão geral EER Documentada pelo Workbench

![Imagem](/docs/images/wb-sakila-eer.png 'Esquema do Banco de dados Sakila')


# Problemas Possíveis

## Erro: MySQL 8: Public Key Retrieval is not allowed
Pode acontecer de falhar na conexão usando um aplicativo ou linguagem, percebi que alterando dois parâmetros.
- useSSL=false
- allowPublicKeyRetrieval=true

Um exemplo para o uso com java:
```
url="jdbc:mysql://localhost:3306?useUnicode=true&characterEncoding=UTF-8&useSSL=false&allowPublicKeyRetrieval=true"
```

## Licença

É gratuito sob licença MIT e para mais informações veja [aqui](LICENSE).

Com diversão e :heart: por [Ricardo Melo Martins](https://github.com/ricardo-melo-martins).
