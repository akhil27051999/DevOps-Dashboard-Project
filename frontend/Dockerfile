FROM node:18

WORKDIR /app
COPY . .

RUN npm install

RUN npm run build || cat /app/npm-debug.log

CMD ["npm", "start"]
