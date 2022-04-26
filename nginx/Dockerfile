FROM registry.access.redhat.com/ubi8/nginx-120:latest

# Add application sources
ADD content/nginx.conf "${NGINX_CONF_PATH}"
ADD content/nginx-default-cfg/*.conf "${NGINX_DEFAULT_CONF_PATH}"
ADD content/nginx-cfg/*.conf "${NGINX_CONFIGURATION_PATH}"
ADD content/*.html .

# Run script uses standard ways to run the application
CMD nginx -g "daemon off;"
