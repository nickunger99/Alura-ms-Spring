# Rodar aplicação via Terminal

& "c:\alura-food\pedidos\mvnw.cmd" spring-boot:run -f "c:\alura-food\pedidos\pom.xml"

# Comandos RabbitMQ
rabbitmq-plugins enable rabbitmq_shovel rabbitmq_shovel_management
<br>

docker network create alura
<br>
docker run -d --rm --net alura --hostname rabbit1 --name rabbit1 -p 8085:15672 -e RABBITMQ_ERLANG_COOKIE=alura_secret rabbitmq:3.10-management
<br>
localhost:8085
<br>
docker run -d --rm --net alura --hostname rabbit2 --name rabbit2 -p 8086:15672 -e RABBITMQ_ERLANG_COOKIE=alura_secret rabbitmq:3.10-management
<br>
localhost:8086
<br>
docker run -d --rm --net alura --hostname rabbit3 --name rabbit3 -p 8087:15672 -e RABBITMQ_ERLANG_COOKIE=alura_secret rabbitmq:3.10-management
<br>
localhost:8087
<br>

docker exec -it rabbit2 rabbitmqctl stop_app
<br>
docker exec -it rabbit2 rabbitmqctl reset
<br>
docker exec -it rabbit2 rabbitmqctl join_cluster rabbit@rabbit1
<br>
docker exec -it rabbit2 rabbitmqctl start_app
<br>
docker exec -it rabbit3 rabbitmqctl stop_app
<br>
docker exec -it rabbit3 rabbitmqctl reset
<br>
docker exec -it rabbit3 rabbitmqctl join_cluster rabbit@rabbit1
<br>
docker exec -it rabbit3 rabbitmqctl start_app
<br>
### NODES
rabbit@rabbit1
<br>
rabbit@rabbit2
<br>
rabbit@rabbit3
