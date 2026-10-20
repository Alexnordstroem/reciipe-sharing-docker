# Build the React frontend using Node.js.
FROM node:18-alpine

WORKDIR /app

# Install the application dependencies.
COPY package*.json ./
RUN npm install

# Copy the frontend source files.
COPY . .

# Set the API address before Vite builds the application.
ARG VITE_API_URL=http://localhost:5000
ENV VITE_API_URL=${VITE_API_URL}

# Create the production build.
RUN npm run build

# Serve the production files using nginx.
FROM nginx:alpine

COPY --from=0 /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
