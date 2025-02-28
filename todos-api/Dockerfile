# Use a lightweight Node.js base image
FROM node:16-alpine

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json first (for caching optimization)
COPY package*.json ./

# Install dependencies efficiently
RUN npm ci --only=production

# Copy the rest of the application
COPY . .

# Expose the required port
EXPOSE 8082

# Use a more efficient startup command
ENTRYPOINT ["node", "server.js"]
