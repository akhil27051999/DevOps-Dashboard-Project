# ----------------------
# Stage 1: Build the React app
# ----------------------
FROM node:18-alpine AS build

# Set working directory
WORKDIR /app

# Copy only package.json and package-lock.json first
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy all project files (src/, public/, etc.)
COPY . .

# Build the app
RUN npm run build || (echo "BUILD FAILED: Dumping logs" && ls -la && cat /app/npm-debug.log || true)


# ----------------------
# Stage 2: Serve the app using a lightweight web server
# ----------------------
FROM node:18-alpine

# Install 'serve' globally
RUN npm install -g serve

# Set working directory
WORKDIR /app

# Copy build output from the previous stage
COPY --from=build /app/build ./build

# Expose the port (change if your app uses a different one)
EXPOSE 3000

# Serve the production build
CMD ["serve", "-s", "build", "-l", "3000"]
