# Stage 1: Build React App
FROM node:18-alpine AS build

WORKDIR /app

# Copy dependencies first
COPY package*.json ./

# Install dependencies
RUN npm ci

# Copy the rest of the code
COPY . .

# Build the frontend
RUN npm run build

# Stage 2: Serve React Build
FROM node:18-alpine

WORKDIR /app

# Install serve globally
RUN npm install -g serve

# Copy build output from previous stage
COPY --from=build /app/build ./build

# Expose port
EXPOSE 3000

# Start app
CMD ["serve", "-s", "build", "-l", "3000"]
