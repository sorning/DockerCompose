Nextjs Tutorials 

1, npm run dev 在项目文件夹下执行该命令

2, docker next’s
https://www.youtube.com/watch?v=7vBUbpbl-JA&list=WL&index=1&t=15s

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
},
