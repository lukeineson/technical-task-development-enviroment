# BUILD STAGE
# Base image
FROM node:14 as builder

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the React application
RUN npm run build

# FINAL STAGE
# Intermediate image for the runtime
FROM nginx:1.21-alpine

# Copy the built application code
COPY --from=builder /app/build /usr/share/nginx/html

# Expose the Nginx port
EXPOSE 80

# Set the entrypoint command
CMD ["nginx", "-g", "daemon off;"]