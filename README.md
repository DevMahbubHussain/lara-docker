docker exec -it laravel_app bash
composer install

Run this command inside your Laravel container (laravel_app):
chown -R www-data:www-data storage bootstrap/cache
chmod -R 775 storage bootstrap/cache

cd /var/www
chown -R www-data:www-data storage bootstrap/cache
chmod -R 775 storage bootstrap/cache



RUN chown -R www-data:www-data /var/www/storage /var/www/bootstrap/cache \
 && chmod -R 775 /var/www/storage /var/www/bootstrap/cache
docker-compose down -v
docker-compose up -d --build



php artisan key:generate
php artisan migrate

php artisan config:clear
php artisan cache:clear



docker exec -it laravel_app bash