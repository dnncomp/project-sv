# WebApp

## Docker Build and Run
``` bash
docker build -t web-app .
```
``` bash
docker run -d -p 4200:80 --name web-app web-app:latest
```
visit http://localhost:4200/ to access the application.
