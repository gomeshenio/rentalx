## Criando projeto com typescript

- Criar pasta
- yarn init -y (cria package.json)
- yarn add express
- yarn add @types/express -D
- yarn add typescript -D
- yarn tsc --init
- yarn add uuid
- yarn add @types/uuid -D
- yarn add ts-node-dev -D **para start**
## Ler arquivos vsc
- yarn add csv-parse   
## Documentação com SWAGGER
- yarn add swagger-ui-express
- yarn add @types/swagger-ui-express -D

- yarn add 
- yarn add 
- yarn add 
- yarn add 
- yarn add 
- yarn add 

## UPLOADS DE ARQUIVOS

- yarn add multer
- yarn add @types/multer -D

## SCRIPTS package.json

"scripts": {
    "dev": "ts-node-dev --inspect --transpile-only --ignore-watch node_modules --respawn src/server.ts"
  },

- Desabilitar o "strict": true, no arquivo tsconfig.json

## CRIANDO IMAGEM NO DOCKER
**Depois de criar o arquivo dockerfile rodar o DOCKER no terminal com o comando abaixo**

- docker build -t rentx .
**para rodar o projeto na porta 3333:3333**
- docker run -p 3333:3333 rentx

**para saber o nome do container**
- docker ps

**Para acessar o container**
- docker exec -it "nome" /bin/bash

**O resultado tem que ser esta linha**
root@6a6699d79107:/usr/app#

**para saber se as informações estão lá**
- ls

## DOCKER COMPOSE 
**Criar arquivo docker-compose.yml**

para executar o docker compose
- docker-compose up

**Se der erro**
- docker ps 
para pegar o CONTAINER ID 6a6699d79107 digitar o inicio do container e dar um tab

**rodar**
- docker stop 6a6699d79107

**remover o container**
- docker rm 6a6699d79107 

**e rodar novamente**
- docker-compose up

**para rodar em background**
- docker-compose up -d

**para ver os logs**

- docker logs rentx -f

## COMANDOS DOCKER 

**lista todos os containers**
 docker ps 

**lista todos os containers parados e startados**
docker ps -a 

**remover um container**
docker rm e ID do container ou nome do container, tem que parar o container para remover

**iniciar um container** 
docker start ID do container 7c647e06d456 depois docker ps para verificar se realmente está rodando

**parar o container**
docker stop ID do container 7c647e06d456

## PARA RODAR DOCKER COMPOSE
**subir em back ground**
docker-compose up -d 

**para parar**
docker-compose stop

****ATEÇÃO****
**remove tudo que foi criado dentro do docker compose. remove tudo que estiver criado dentro do serviço**
docker-compose down

**para iniciar**
docker-compose start

**ACESSAR OUTRA MÁQUINA/CONTAINER/IMAGEM**
**inicia o container com nome ou ID do container/imagem** 
docker start rentx

**nome ou ID do container/imagem** 
docker exec -it rentx /bin/bash

**para listar o que tem dentro**
ls

**para sair do container**
Ctrl+c 

**ultimos logs**
docker logs rentalx

**observar logs**
docker logs rentalx -f

**para sair do container**
Ctrl+c 

## BANCO DE DADOS

yarn add typeorm reflect-metadata

4. install a database driver POSTGRES

yarn add pg

**configurações do banco no tsconfig.json descomentar as duas linhas abaixo**
 "experimentalDecorators": true,
 "emitDecoratorMetadata": true, 

criar arquivo ormconfig.json

**criar imagem do banco**
arquivo docker-compose.yml

**para startar depois das alterações**

docker-compose up --force-recreate

**em caso de erro**
docker-compose down
docker-compose stop
docker ps
docker ps -a

**para recriar/restart**
docker-compose up

**SABER OS IP's**
**quando a aplicação roda em um IP diferente do IP do banco de dados**
docker inspect --format='{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' rentx
docker inspect --format='{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' database_ignite

**mostra o IP na ultima linha**
docker exec rentx cat /etc/hosts
docker exec database_ignite cat /etc/hosts

**adicionar no arquivo docker-compose.yml abaixo de volumes na ultima linha para trabalhar na msm rede**
network_mode: host

**depois das configurações acima dar um**
docker-compose down

**para depois subir tudo novamente com**
docker-compose up -d 

**para ver os logs se estão rodando**
docker logs rentx -f















## DEBUG
- Arquivo do debug *escolher:* **To customize Rum and Debug create a launch.json file**
Opção Node.js que abrirá o arquivo para colocarmos as configurações que estão abaixo.

{
  // Use IntelliSense to learn about possible attributes.
  // Hover to view descriptions of existing attributes.
  // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "attach",
      "name": "Launch Program",
      "skipFiles": ["<node_internals>/**"],
      // "program": "${workspaceFolder}\\src\\server.ts",
      "outFiles": ["${workspaceFolder}/**/*.js"]
    }
  ]
}
<!-- - yarn tsc para inicializar 
- Ir na no arquivo tsconfig.json procurar a linha "outDir": "./", e criar a pasta dist "outDir": "./dist",
- node dist/server.js **para startar o back-end**
- Para não ter que rodar o yarn tsc e depois o node dist/server.js após uma alteração -->