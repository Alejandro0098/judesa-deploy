FROM node:20.18.0-alpine

CMD ["mkdir", "/app/www/"]

WORKDIR /app/www/

COPY ./apps/www/ .

RUN npm install 
RUN npm i pm2-runtime
RUN npm i sharp

RUN npm run build

EXPOSE 3000

CMD ["npm", "start"]