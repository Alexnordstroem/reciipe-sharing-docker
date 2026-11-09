
# Build the React frontend using Node.js.
FROM node:18-alpine AS build

WORKDIR /app

# Install the application dependencies.
COPY package*.json ./
RUN npm install

# Accept the deployed backend URL.
ARG VITE_API_URL
ENV VITE_API_URL=${VITE_API_URL}

# Copy the frontend source files.
COPY . .

# Create the production build.
RUN npm run build

# Serve the production files using nginx.
FROM nginx:alpine

COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
