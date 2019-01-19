## start docker-compose
docker-composer up -d

## alias
alias phpd="docker-compose exec app php"

# setup - install composer
composer update --no-scripts  
composer dump-autoload
cp .env.example .env
phpd artisan migrate --seed
phpd artisan key:generate
phpd artisan optimize
phpd artisan migrate --seed
phpd artisan make:controller MyController