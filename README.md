This is a boilerplate for using ASPNET IDENTITY for cookie-based authentication/authorization. It uses PostgreSQL running in a Docker container with a volume
mounted to it for data persistence. Can run on win, mac, linux

make sure you have the following installed: 
dotnet 8 sdk, entity framework CLI, docker

Steps to reproduce:
1- clone repo <br>
2- delete "Migrations" folder <br>

3- in your terminal/cmd line run the following command to create docker volume: <br>
 <code>docker volume create volume02</code>

4- then type in this command to create and run the PostgreSQL container:
"docker run --name postgres -e POSTGRES_PASSWORD=password123 \
-p 5432:5432 -v volume02:/var/lib/postgresql/data -d postgres"

5- run dotnet ef migrations "name of your migration"
       dotnet ef database update

 These will populate the postgres DB with the Identity library-provided tables for authentication. 

To connect to postgreSQL db, open an interactive terminal and run this command: psql -U postgres
then: \c auth_db; (to connect to the db ef created)
then: \dt; (to show the tables that ef created)

                 List of relations
 Schema |         Name          | Type  |  Owner   
--------+-----------------------+-------+----------
 public | AspNetRoleClaims      | table | postgres
 public | AspNetRoles           | table | postgres
 public | AspNetUserClaims      | table | postgres
 public | AspNetUserLogins      | table | postgres
 public | AspNetUserRoles       | table | postgres
 public | AspNetUserTokens      | table | postgres
 public | AspNetUsers           | table | postgres
 public | __EFMigrationsHistory | table | postgres

 
