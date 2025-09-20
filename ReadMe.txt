Как подключиться правильно

В pgAdmin создайте (или отредактируйте) сервер:

Name: local_postgres (любое)

Host name/address: db_serv ← это имя сервиса из compose
(можно и local_postgre, т.к. это container_name, но лучше — имя сервиса)

Port: 5432

Maintenance DB: postgres

Username: postgres

Password: 2015

SSL mode: Disable (если не настраивали TLS)


Проверки, если вдруг не коннектится

Посмотреть, что Postgres запустился:

docker logs -f local_postgre


Должно быть что-то вроде database system is ready to accept connections.

Из контейнера pgAdmin пропинговать Postgres:

docker exec -it pgadmin4_app ping -c1 db_serv


Зайти в psql внутри контейнера Postgres:

docker exec -it local_postgre psql -U postgres