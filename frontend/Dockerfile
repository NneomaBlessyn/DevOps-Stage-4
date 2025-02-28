# Use Node.js 14 as base
FROM node:14

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json before installing dependencies
COPY package*.json ./

# Install dependencies only (no cache clearing needed)
RUN npm ci --only=production

# Copy the rest of the application code
COPY . .

# Expose the port
EXPOSE 8080

# Use a better command for production
CMD ["node", "server.js"]
