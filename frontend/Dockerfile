# Step 1: Build Stage
FROM node:18 AS builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .    # Copy AFTER install so build can access src/public
RUN npm run build

# Step 2: Serve Stage
FROM node:18-slim

WORKDIR /app

RUN npm install -g serve

COPY --from=builder /app/build ./build

EXPOSE 3000

CMD ["serve", "-s", "build", "-l", "3000"]
