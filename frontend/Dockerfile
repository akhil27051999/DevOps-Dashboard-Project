# Step 1: Build Stage
FROM node:18 AS builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .    # NOW copy all code AFTER install so build can find src/
RUN npm run build

# Step 2: Serve Stage (Production)
FROM node:18-slim

WORKDIR /app

# Install only the "serve" package for serving the static build
RUN npm install -g serve

COPY --from=builder /app/build ./build

EXPOSE 3000

CMD ["serve", "-s", "build", "-l", "3000"]
