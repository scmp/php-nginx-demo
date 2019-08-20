ARG PHP_CONTAINER_IMAGE
FROM $PHP_CONTAINER_IMAGE

FROM nginx:1.17-alpine

# Copy built files from php image to shared volume dir
COPY --from=0 /app /var/www/html
