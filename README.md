# rsmod-sqlservice
Integrate SQL into your game engine easily with an SQL Service.
Currently at version 1.0.1

# Introduction
An SQL wrapper for RS MOD designed to get rid of flat file saves. Using a Database to save information allows for cross platform integration. Finally, you'll be able to display highscores and player data on your webapp or equivilent.

# Getting Started
- Clone the repository and upload the files into their corresponding places in your RS MOD local project.
- Inside of your `game.yml` or, for distributing, `game.example.yml` remove the following in your services:

```
services:
  - class: gg.rsmod.game.service.serializer.json.JsonPlayerSerializer
```

- Inside of your `game.yml` or, for distributing, `game.example.yml` add the following to your services:

```
services:
  - class: gg.rsmod.plugins.service.sql.SQLService
    driver: "com.mysql.jdbc.Driver" # Your JBCD connector as explained in Gradel Depdendencies.
    password: "pswd"
    dbname: "db"
    user: "user"
```

There are many configurations you can alter based on your needs. Here are a list of configurations you can change when declaring the class:

- `driver` - Gradel Dependency for your Database, Default `com.mysql.jdbc.Driver`
- `port` - Port your Database is running on, Default `3306`
- `host` - The host your Database is running on, Default `127.0.0.1`
- `user` - The username of your Database user, Default `root`
- `password` - The password for your Database user, Default `NULL`
- `dbname` - The Database name you are using, Default `NULL`

# Gradel Dependencies
By default, the `build.gradle` contains all JBCD connectors. You can remove the ones that you do not need.

```
compile "org.postgresql:postgresql:42.2.2"
compile "mysql:mysql-connector-java:5.1.46"
compile "com.microsoft.sqlserver:mssql-jdbc:6.4.0.jre7"
```
