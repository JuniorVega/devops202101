# lab06-docker-03

### Tag images

1. Limpiar (opcional)
    ```bash
    docker system prune
    ```

1.  Generar website:1.0.0
    ```bash
    docker build -t website -f ./1.0/Dockerfile ./1.0/
    docker build -t website .
    docker build -t website:latest .
    docker build -t website:1.0.0 .

    docker tag website:latest website:1.0.0
    docker tag website:latest mzegarra/website:1.0.0

    docker build -t website -f ./2.0/Dockerfile ./2.0/
    docker build -t modventas:2.0.0 .
    docker tag modventas:2.0.0 mzegarra/modventas:2.0.0
    docker tag modventas:2.0.0 mzegarra/modventas:latest

    docker tag website:latest website:2.0.0
    docker tag website:latest mzegarra/website:2.0.0

    docker tag website:0.0.1 mzegarra/website:0.0.1
    docker tag website:0.0.2 mzegarra/website:0.0.2
    docker tag website:0.0.3 mzegarra/website:0.0.3
    docker tag website:0.0.3 mzegarra/website:latest

    ```

1. Docker hub login
    ```bash
        docker login docker.io
        <<user>>/<<repository name>>:<<tag>>
    
        docker push mzegarra/website:0.0.3
        docker push mzegarra/website:latest
    ```

1. Push Azure Registry
    ```bash
    docker login galaxytraining01.azurecr.io -u galaxytraining01
    <<url repository>>/<<repository name>>:<<tag>>

    docker tag website:latest galaxytraining01.azurecr.io/website:1.0.0
    docker tag website:latest galaxytraining01.azurecr.io/website:2.0.0

    docker tag modventas:2.0.0 galaxytraining01.azurecr.io/modventas:mzegarra
    docker push galaxytraining01.azurecr.io/modventas:mzegarra

    ```