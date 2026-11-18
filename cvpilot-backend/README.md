# CVPilot backend

The backend connects to the local MySQL database `cvpilot` as user `root`.
Set `DB_PASSWORD` in the environment before starting the application:

```powershell
$env:DB_PASSWORD = "your-mysql-password"
.\mvnw.cmd spring-boot:run
```
