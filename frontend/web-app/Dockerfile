# Use an official Node runtime as a parent image
FROM node:21-alpine as build

# Set the working directory to /app
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install Angular CLI and project dependencies
RUN npm install -g @angular/cli@latest \
    && npm install

# Copy the rest of the application code to the working directory
COPY . .

# Build the Angular application
# RUN ng build --configuration production
RUN npm run build


# Use an official Nginx runtime as a parent image
FROM nginx:1.25-alpine

# Copy the built Angular application to the default Nginx public folder
COPY --from=build /app/dist/ /usr/share/nginx/html

# Copy the Nginx configuration file to the default Nginx configuration folder
COPY nginx.conf /etc/nginx/conf.d/default.conf
