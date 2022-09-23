# docker-dev - continers for development
# Sql Server Container 2019
docker run -d --name=sql2 -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=admin1234" -p 1444:1433 -v c:/db/sqlserver/data:/var/opt/mssql/data  -d mcr.microsoft.com/mssql/server:2017-latest
# with persistent data in volumes
docker run --name=sql1 -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=admin1234" \\
	-p 1433:1433 \\
	-v c:/db/sqlserver/data:/var/opt/mssql/data \\
	-v c:/db/sqlserver/log:/var/opt/mssql/log \\
	-v c:/db/sqlserver/secrets:/var/opt/mssql/secrets \\
	-d mcr.microsoft.com/mssql/server:2019-latest
  
 # Sql Server Container 2017
docker run --name=sql1 -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=admin1234" \\
	-p 1433:1433 \\
	-v c:/db/sqlserver2017/data:/var/opt/mssql/data \\
	-v c:/db/sqlserver2017/log:/var/opt/mssql/log \\
	-v c:/db/sqlserver2017/secrets:/var/opt/mssql/secrets \\
	-d mcr.microsoft.com/mssql/server:2017-latest
  
 # Postgres
 docker run --name pg1 -e POSTGRES_PASSWORD=admin1234 -d postgres
 
 # Potgres docker compose
version: '3.7'
services:
  postgres1:
    image: postgres
    container_name: pg2
    environment:
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=admin1234
      - POSTGRES_DB=postgres
    ports:
      - '5444:5432'
    volumes:
      - c:/db/postgresql/data:/var/lib/postgresql/data
      - c:/db/postgresql/backups:/var/backups
