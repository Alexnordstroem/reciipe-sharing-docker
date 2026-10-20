# Use the required Node.js image.
FROM node:18-alpine

# Set the application directory.
WORKDIR /app

# Copy dependency files and install packages.
COPY package*.json ./
RUN npm install

# Copy the backend application.
COPY . .

# Store the SQLite database in the persistent data directory.
RUN mkdir -p /app/data \
    && ln -s /app/data/recipes.db /app/recipes.db

# Make the backend port available.
EXPOSE 5000

# Start the API server.
CMD ["npm", "start"]
