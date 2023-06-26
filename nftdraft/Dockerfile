FROM node:latest

WORKDIR /app

COPY /draft-score /app

RUN npm install

EXPOSE 3333

CMD ["npm", "run", "dev"]
