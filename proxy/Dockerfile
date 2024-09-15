FROM nginx:alpine

# Copy the custom Nginx configuration file to the container
# This will override the default configuration with the one specified in default.conf
COPY default.conf /etc/nginx/conf.d/default.conf

# Create a directory for SSL certificates
# The -p flag ensures that no error is reported if the directory already exists
RUN mkdir -p /etc/nginx/ssl

# Copy the SSL certificate and key into the container
# These are used to enable HTTPS for the Nginx server
COPY /ssl/nginx.crt /etc/nginx/ssl
COPY /ssl/nginx.key /etc/nginx/ssl
