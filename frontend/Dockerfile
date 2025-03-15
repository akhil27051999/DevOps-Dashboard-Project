# Use a Node image
FROM node:18

# Set working directory
WORKDIR /app

# Copy only package.json and package-lock.json first
COPY package*.json ./

# Install dependencies first (cache layer)
RUN npm install

# Now copy all project files (including src/public etc.)
COPY . .

# Build the app
RUN npm run build

# Serve the app
CMD ["npm", "start"]
