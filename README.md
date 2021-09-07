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

## UPLOADS DE ARQUIVOS

- yarn add multer
- yarn add @types/multer -D

## SCRIPTS package.json

"scripts": {
    "dev": "ts-node-dev --inspect --transpile-only --ignore-watch node_modules --respawn src/server.ts"
  },

- Desabilitar o "strict": true, no arquivo tsconfig.json

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
