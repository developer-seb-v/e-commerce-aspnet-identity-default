<p>This is a boilerplate for using ASPNET IDENTITY for cookie-based authentication/authorization. It uses PostgreSQL running in a Docker container with a volume mounted to it for data persistence. Obviously, this project has no controller endpoints. You still need to create your controllers or minimal API style endpoints. You can also add JWT as well if you'd like. Can run on win, mac, linux.</p>

Make sure you have the following installed: <br>
<em>dotnet 8 sdk, entity framework CLI, docker</em>

Steps to reproduce: <br>
1- clone repo <br>
2- delete "Migrations" folder <br>

3- in your terminal/cmd line run the following command to create docker volume: <br>
 <code>docker volume create volume02</code> 
 <br>

4- then type in this command to create and run the PostgreSQL container:<br>
<code>docker run --name postgres -e POSTGRES_PASSWORD=password123 \ <br>
-p 5432:5432 -v volume02:/var/lib/postgresql/data -d postgres</code> <br>

5- run <code>dotnet ef migrations "name of your migration"</code> <br>
     <code> dotnet ef database update </code> <br>
 These will populate the postgres DB with the Identity library-provided tables for authentication. 
<br>
To connect to postgreSQL db, open an interactive terminal and run this command:<br>
<code>psql -U postgres</code> <br>
then: <code> \c auth_db; </code>(to connect to the db ef created)<br>
then: <code>\dt; </code> (to show the tables that ef created) <br>

 Schema |         Name          | Type  |  Owner   <br>
--------+-----------------------+-------+---------- <br>
 public | AspNetRoleClaims      | table | postgres <br>
 public | AspNetRoles           | table | postgres <br>
 public | AspNetUserClaims      | table | postgres <br>
 public | AspNetUserLogins      | table | postgres <br>
 public | AspNetUserRoles       | table | postgres <br>
 public | AspNetUserTokens      | table | postgres <br>
 public | AspNetUsers           | table | postgres <br>
 public | __EFMigrationsHistory | table | postgres <br>

 
