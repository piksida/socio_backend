# backend_api

#### Development (```docker-compose.yml```):
- remove volumes:  
 ```docker-compose down -v```
 - build:  
 ```docker-compose up -d --build```
- run migrations:  
 ```docker-compose exec web python manage.py migrate --noinput```
- inspect postgres_data volume:  
```docker volume ls``` - list volumes,   
```docker volume inspect backend_template_django_postgres_data```
- check db:  
```docker-compose exec db psql --username=postgres_sample --dbname=postgres_sample```  
```#``` ```\l``` (list of databases), ```\c``` (connection), ```\dt``` (list of relations), ```\q``` (quit)

  
#### Production (```docker-compose.prod.yml```):
- remove volumes:  
 ```docker-compose -f docker-compose.prod.yml down -v```
- build:  
 ```docker-compose -f docker-compose.prod.yml up -d --build```
- run migrations:  
 ```docker-compose -f docker-compose.prod.yml exec web python manage.py migrate --noinput```
- place static files to the "static" directory:  
 ```docker-compose -f docker-compose.prod.yml exec web python manage.py collectstatic --no-input --clear```
