docker pull aparnaghegde10917/bookstore:latest


docker images

docker network create bookstore-network

docker network ls

docker run -d \
--name mysql-db \
--network bookstore-network \
-e MYSQL_ROOT_PASSWORD=root \
-e MYSQL_DATABASE=bookstore \
-p 3307:3306 \
mysql:8

Verify MySQL Is Running

docker ps

docker logs mysql-db

docker run -d \
--name bookstore-app \
--network bookstore-network \
-p 8081:8080 \
-e SPRING_DATASOURCE_URL=jdbc:mysql://mysql-db:3306/bookstore \
-e SPRING_DATASOURCE_USERNAME=root \
-e SPRING_DATASOURCE_PASSWORD=root \
aparnaghegde10917/bookstore:latest

docker ps

http://localhost:8081

If it still exits, run:

docker logs bookstore-app
