
FROM node:22-bookworm-slim

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN mkdir -p /app/data \
    && rm -f /app/recipes.db \
    && ln -s /app/data/recipes.db /app/recipes.db

EXPOSE 5000

CMD ["npm", "start"]
