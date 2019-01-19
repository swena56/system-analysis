docker pull composer
docker-composer up -d

## alias
alias composer="docker run -it composer"
alias phpd="docker-compose exec app php"

# setup
cp .env.example .env

phpd artisan migrate --seed



docker-compose exec app php artisan key:generate
docker-compose exec app php artisan optimize

docker-compose exec app php artisan migrate --seed
docker-compose exec app php artisan make:controller MyController