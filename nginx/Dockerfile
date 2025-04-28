# Start from the official nginx image
FROM nginx:alpine

# Install Node.js and PM2 if needed (optional - can remove if not running node inside nginx)
RUN apk add --no-cache nodejs npm && \
    npm install -g pm2

# Set working directory
WORKDIR /app

# Copy custom nginx config to replace default
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Create directory for SSL certificates
RUN mkdir -p /etc/nginx/ssl

# Copy SSL certificate and private key
COPY fullchain.pem /etc/nginx/ssl/fullchain.pem
COPY privkey.pem /etc/nginx/ssl/privkey.pem

# Expose HTTP and HTTPS ports
EXPOSE 80
EXPOSE 443

# Start Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]

