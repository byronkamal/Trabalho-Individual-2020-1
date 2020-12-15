## Solução do Trabalho Individual

[![Build Status](https://travis-ci.com/byronkamal/Trabalho-Individual-2020-1.svg?branch=master)](https://travis-ci.com/byronkamal/Trabalho-Individual-2020-1)

[![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=byronkamal_Trabalho-Individual-2020-1&metric=sqale_rating)](https://sonarcloud.io/dashboard?id=byronkamal_Trabalho-Individual-2020-1)

[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=byronkamal_Trabalho-Individual-2020-1&metric=alert_status)](https://sonarcloud.io/dashboard?id=byronkamal_Trabalho-Individual-2020-1)

[![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=byronkamal_Trabalho-Individual-2020-1&metric=security_rating)](https://sonarcloud.io/dashboard?id=byronkamal_Trabalho-Individual-2020-1)

[![Code Smells](https://sonarcloud.io/api/project_badges/measure?project=byronkamal_Trabalho-Individual-2020-1&metric=code_smells)](https://sonarcloud.io/dashboard?id=byronkamal_Trabalho-Individual-2020-1)

[![Duplicated Lines (%)](https://sonarcloud.io/api/project_badges/measure?project=byronkamal_Trabalho-Individual-2020-1&metric=duplicated_lines_density)](https://sonarcloud.io/dashboard?id=byronkamal_Trabalho-Individual-2020-1)


## Conteinerização

O projeto possui três ambientes dockerizados: **client, api, db**. Os ambiente **api e client** possuem seu próprio arquivo `Dockerfile`, localizado nas suas respectivas
pastas. Para execução e criação das imagens e containers, foi criado um arquivo `docker-compose`, que está na raiz do projeto.

#### Executando o projeto: 
Para executar todo o projeto e, para que este fique executando em segundo plano,
temos o seguinte comando:
```
sudo docker-compose up -d --build
```
Após executar o comando acima, rode os seguintes comandos para configurar o banco de dados:
```
 sudo docker-compose run api rake db:create
 sudo docker-compose run api rake db:migrate
```
Após executar um dos comandos acima, as aplicações estarão disponíveis nos endpoints:
- Front-end: `http://localhost:8080`
- Back-end: `http:localhost:3000`

#### Testes
Após realizar os passos do "Executando o projeto", é possível executar os testes no projeto 
e para isso temos os seguintes comandos:
- Fron-end
```
sudo docker-compose run client yarn test:unit
```
- Back-end
```
sudo docker-compose run api bundle exec rails test
```

## Continuos Integration
### Build e Testes
A ferramenta utilizada para a execução dessa etapa foi o Travis CI. Foram definidos 
os estágios de **build, tests, Push docker image", estando essa configuração no arquivo 
`.travis.yml`. A coleta de métricas de qualidade é realizada com a ferramenta **Sonar Cloud**.

Foram adicionadas regras à branch `master` para que ela fosse protegida. Para que um novo código
seja integrado a branch default, é necessário  que seja relaizado um PR e 
que os **status checks** sejam aprovados atráves da correta execução dos estágios de 
build, testes e análise de métricas.
