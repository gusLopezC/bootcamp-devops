
# Manual Práctico de Docker

## 1. Introducción a Docker
Este manual incluye una serie de ejercicios para familiarizarse con Docker. Se recomienda completar cada sección para obtener una comprensión progresiva de la herramienta.

---

## 2. Ejercicio 1: Instalar Docker
Si no tienes Docker instalado, sigue la guía oficial de instalación:

- [Guía de instalación de Docker](https://docs.docker.com/get-docker/)

---

## 3. Ejercicio 2: Verificar la instalación de Docker

Verifica la instalación de Docker con el siguiente comando:

```bash
docker --version
```

Para comprobar que Docker funciona correctamente, ejecuta:

```bash
docker run hello-world
```

---

## 4. Ejercicio 3: Ejecutar tu primer contenedor

Ejecuta un contenedor simple de Nginx:

```bash
docker run -d -p 8080:80 nginx
```

Visita `http://localhost:8080` en tu navegador para ver la página por defecto de Nginx.

---

## 5. Ejercicio 4: Explorar contenedores en ejecución

Comprueba los contenedores activos con:

```bash
docker ps
```

Para ver todos los contenedores, incluidos los detenidos:

```bash
docker ps -a
```

---

## 6. Ejercicio 5: Crear un Dockerfile

1. Crea un directorio y un archivo `Dockerfile`:

    ```bash
    mkdir myapp
    cd myapp
    nano Dockerfile
    ```

2. Añade el siguiente contenido al `Dockerfile`:

    ```Dockerfile
    FROM python:3.9-slim
    WORKDIR /app
    COPY . .
    RUN pip install flask
    EXPOSE 5000
    CMD ["python", "app.py"]
    ```

3. Crea un archivo `app.py`:

    ```bash
    nano app.py
    ```

    Agrega el siguiente código:

    ```python
    from flask import Flask
    app = Flask(__name__)

    @app.route('/')
    def hello():
        return "¡Hola, Docker!"

    if __name__ == "__main__":
        app.run(host='0.0.0.0', port=5000)
    ```

4. Construye la imagen:

    ```bash
    docker build -t myapp .
    ```

5. Ejecuta el contenedor:

    ```bash
    docker run -d -p 5000:5000 myapp
    ```

Visita `http://localhost:5000` en tu navegador.

---

## 7. Ejercicio 6: Gestionar volúmenes

Crea un contenedor de MySQL con un volumen:

```bash
docker run -d -p 3306:3306 --name mysql-db -e MYSQL_ROOT_PASSWORD=secret -v mysql_data:/var/lib/mysql mysql:latest
```

Verifica el volumen creado:

```bash
docker volume ls
```

---

## 8. Ejercicio 7: Inspeccionar y depurar contenedores

1. Inspecciona un contenedor:

    ```bash
    docker inspect <container_id>
    ```

2. Revisa los logs de un contenedor:

    ```bash
    docker logs <container_id>
    ```

3. Inicia sesión dentro del contenedor:

    ```bash
    docker exec -it <container_id> /bin/bash
    ```

---

## 9. Ejercicio 8: Publicar imágenes en Docker Hub

1. Inicia sesión en Docker Hub:

    ```bash
    docker login
    ```

2. Etiqueta la imagen que creaste:

    ```bash
    docker tag myapp <tu_usuario>/myapp:1.0
    ```

3. Sube la imagen a Docker Hub:

    ```bash
    docker push <tu_usuario>/myapp:1.0
    ```

4. Cualquier persona puede descargar y ejecutar la imagen:

    ```bash
    docker pull <tu_usuario>/myapp:1.0
    docker run -d -p 5000:5000 <tu_usuario>/myapp:1.0
    ```

---

## 10. Ejercicio 9: Docker Compose

1. Crea un archivo `docker-compose.yml`:

    ```yaml
    version: '3'
    services:
      web:
        image: nginx
        ports:
          - "8080:80"
      app:
        build: .
        ports:
          - "5000:5000"
    ```

2. Levanta los servicios con Docker Compose:

    ```bash
    docker-compose up
    ```

3. Para detener y eliminar los contenedores:

    ```bash
    docker-compose down
    ```

---

## 11. Ejercicio 10: Limpiar recursos

1. Elimina contenedores detenidos:

    ```bash
    docker container prune
    ```

2. Elimina imágenes no utilizadas:

    ```bash
    docker image prune
    ```

3. Elimina volúmenes no utilizados:

    ```bash
    docker volume prune
    ```

---

## Conclusión

Estos ejercicios cubren los aspectos fundamentales de Docker. ¡Esperamos que los disfrutes y aprendas mucho!
