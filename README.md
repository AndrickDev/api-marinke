1 - Criar projeto:
npm init -y

2 - Instalando typescript:
npm install typescript --save-dev

3 - Gerar arquivo de configuração para o typescript tsconfig.json:
npx tsc --init

conteúdo:
{
  "compilerOptions": {
    "target": "ES6",
    "module": "commonjs",
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true
  },
  "exclude": ["node_modules"]
}


4 - instalar o express
- instalar biblioteca nodemon para arquivos typescript serem executados diretamente, sem precisar traspilar manualmente.
npm install express
npm install @types/express --save-dev
npm install ts-node-dev --save-dev


5 - Configurar scripts no package.json

 "scripts": {
    "dev": "ts-node-dev --respawn --transpile-only src/app.ts",
    "build": "tsc",
    "start": "node dist/index.js"
  },

6 - Arquivo App.ts

import express, { Request, Response } from 'express';

const app = express();
const port = 3000;

app.get('/', (req: Request, res: Response) => {
    res.send('Hello World!');
});

app.listen(port, () => {
    console.log(`erver is running at http://localhost:${port}`);
});
