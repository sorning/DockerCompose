Nextjs Tutorials 

安装nvm，node，npm
先在mnt文件夹下安装nvm，通过nvm安装node和npm（通过nvm安装node时已经安装了npm，因为npm是绑定在node里的）
https://docs.npmjs.com/downloading-and-installing-node-js-and-npm
https://github.com/nvm-sh/nvm

创建nextjs项目
https://nextjs.org/docs/getting-started/installation


操作指南v1
1，在nextjs 项目目录下创建Dockfile and docker-compose.yaml
2, 在项目目录下运行   
1-1，sudo docker compose build  (先build image)
1-2，sudo docker compose up (run service)

1-5, sudo docker exec nextjsshopify1-web-1 npm install @headlessui/react
1-6, sudo docker exec nextjsshopify1-web-1 npm run build
1-7,"start": "next start --port 3001", (nextjs package.js)
1-8, sudo docker exec nextjsshopify1-web-1 npm run build

更改端口
更改docker port, 先把nextjs 里的scripts 改了，再改docker compose 里的port
 "scripts": { 
       "dev": "next dev -p 8080",
       "start": "next start -p 8080",
},




注意：sudo docker compose up -d    (后台运行)

Dockerfile

FROM node:20

WORKDIR /app

COPY . .
RUN npm install

docker-compose.yaml
version: '3.9'
services:
  web:
    build:
      context: ./
    volumes:
      - .:/app
    command: npm run dev
    ports:
      - "3000:3000"
      - “3001:3001”
    
