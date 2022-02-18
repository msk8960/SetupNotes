# Setting up MSSQL Server for Spring Boot (or for any Java Programming)

### Summary
- Configure ports of MS-SQL server
- Choose `SQL Server and Windows Authentication Mode` instead of `Windows Authentication Mode`
- Enable user `sa`
- Configure the application


### Configuring ports of MS-SQL server
- Open `SQL Server Configuration Manager`
- Expand `SQL Server Network Configuration` on the left panel
- Select `Protocols for $ServerName` under it
- Select `TCP/IP` on right side and right click on it (make sure `TCP/IP` is **Enabled**)
- Click on `Properties`
- Select `IP Addresses` tab on the new window
- Scroll down and under `IPAll` click on field infront of `TCP Port`
- Type a port number like **1434**
- Press `OK`
- You need to restart the `SQL Server` from `Task Manager`


### Choosing "SQL Server and Windows Authentication Mode"
- Open `Microsoft SQL Server Management Studio`
- Connect your SQL Server
- Right click on the **server instance** and select `Properties`
- Select `Security` page on left side
- Select `SQL Server and Windows Authentication Mode` under `Server Authentication`
- Press `OK` and restart the server


### Enabling User "sa"
- Open `Microsoft SQL Server Management Studio`
- Connect your SQL Server
- Expand **server instance** and then expand `Security` and then expand `Logins`
- Select user `sa` and Right click and select `Properties`
- Select `Status` on left side and select `Enabled` under `Login` (which is under `Settings`).
- Press `OK` and reconnect to server


### Configuring the Application

```
spring.application.name=account-mssql
server.port=8090
spring.datasource.url=jdbc:sqlserver://localhost:1434;databaseName=testdb
spring.datasource.username=sa
spring.datasource.password=password
spring.datasource.driver-class-name=com.microsoft.sqlserver.jdbc.SQLServerDriver
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.SQLServer2016Dialect
spring.jpa.hibernate.ddl-auto=update
```
