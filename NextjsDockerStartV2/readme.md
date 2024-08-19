Nextjs Tutorials 


1, npm run dev 在项目文件夹下执行该命令

2, docker nextjs dockerfile 参考
https://www.youtube.com/watch?v=7vBUbpbl-JA&list=WL&index=1&t=15s

docker nextjs dockerfile 和 docker-compose 参考
https://geshan.com.np/blog/2023/01/nextjs-docker/


docker compose build 参考
prompt: how to use docker compose build
https://chat.openai.com/c/bff528ec-62f9-4610-af22-80c508bc0306


操作指南v1
1，在nextjs 项目目录下创建Dockfile and docker-compose.yaml
2, 在项目目录下运行   
sudo docker compose build  (先build image)
sudo docker compose up (run service)
3, 在dev或start模式下，都可以在另一个teminal运行
sudo docker exec nextjsshopify1-web-1 npm run build
sudo docker exec nextjsshopify1-web-1 npm run start
4，可以通过更改docker-compose.yaml中的command: npm run start(dev)来切换运行的模式，在dev下不会通过域名访问，因为nginx没配置相应的端口。


注意：sudo docker compose up -d    (后台运行)

FROM node:20

WORKDIR /app

COPY . .
RUN npm install

操作指南v2
1-2, docker-compose.yaml
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
    
1-3, sudo docker compose build
1-4, sudo docker compose up
1-5, sudo docker exec nextjsshopify1-web-1 npm install @headlessui/react
1-6, sudo docker exec nextjsshopify1-web-1 npm run build
1-7,"start": "next start --port 3001", (nextjs package.js)
1-8, sudo docker exec nextjsshopify1-web-1 npm run build

注意：docker 会操作读写项目文件，因为dockerfile的COPY . .
<!-- 
先在linux创建nextjs app， 然后在projext 文件下创建dockerfile,
FROM node:20

WORKDIR /usr/src/app

COPY . .
RUN npm install --production
RUN npm run build
CMD ["npm", "run", "dev"]

Sudo docker built -t nextjsimagename .

Sudo docker run nextjsimagename

3, 更改docker port, 先把nextjs 里的scripts 改了，再改docker compose 里的port
 "scripts": { 
       "dev": "next dev -p 8080",
       "start": "next start -p 8080",
}, -->
