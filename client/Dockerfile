# Stage 1: Build the React app with Vite
FROM node:18-alpine as builder
WORKDIR /app

COPY package.json ./
COPY package-lock.json ./
RUN npm install

COPY . .
RUN npm run build  # This will generate /dist

# Stage 2: Serve the app with Nginx
FROM nginx:stable-alpine

# Copy the built Vite output
COPY --from=builder /app/dist /usr/share/nginx/html

# Optional: remove default NGINX config and add your own if needed
# COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
