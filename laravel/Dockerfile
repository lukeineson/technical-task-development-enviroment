# BUILD STAGE
# Base Image
FROM composer as builder

# Set the working directory
WORKDIR /app

# Copy the Composer files
COPY composer.json composer.lock ./

# Install dependencies
RUN composer install --no-scripts --no-autoloader

# Copy the rest of the application code
COPY . . 

# Generate the autoloader
RUN composer dump-autoload --no-scripts --optimize

# Build the production assets
RUN php artisan optimize 


# FINAL STAGE
# Intermediate image for the runtime
FROM php:8.0-apache

# Set the working directory
WORKDIR /var/www/html

# Copy the built application code
COPY --from=builder /app .

# Expose the Apache port
EXPOSE 80

# Set the entrypoint command
CMD ["apache2-foreground"]

