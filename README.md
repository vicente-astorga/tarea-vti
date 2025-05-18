# Tarea VTI

Este repositorio contiene la solución a la tarea, la cual consiste en desplegar una aplicación Django con Docker y configurar automatización mediante GitHub Actions.

## Requisitos y Consideraciones

- Se debe contar con Docker, Docker Compose y GitHub
- Para ejecutar fast-forward-pr (/ff), es necesario configurar un secret con el nombre *GH_TOKEN* con un *Personal Access Token* que tenga permisos repo, workflow, pull_requests.
- Dependiendo del entorno, el comando puede ser **docker compose** sin guión (ARM) y en otros puede ser **docker-compose**


## Instalación y ejecución de la aplicación

1. Clonar el repositorio:

```bash
git clone https://github.com/usuario/tarea-devops.git
cd tarea-devops
```

2. Iniciar la aplicación
```
docker compose up
```

3. Verificar que la app esté funcionando:
```bash
curl -i http://localhost:3005/
# Debe devolver HTTP/1.1 200 OK y el mensaje "Hello World!"
```

## Ejecución de tests

1. En local (con Docker):
```bash
docker compose run web pytest
```
2. En GitHub Actions:
Los tests se ejecutan automáticamente en cada push o pull request a la rama main utilizando un runner de GitHub.

## Fast Forward en Pull Requests (/ff)

Este permite propagar automáticamente cambios a la rama main (si el historial permite un fast-forward).

1. **Sin conflictos**. Al crear un Pull Request hacia main, basta con comentar **/ff** en el PR. Si no hay conflictos, se propaga automáticamente con el mensaje *"Código propagado correctamente"*

2. **Con conflictos**. Si el historial de ramas no permite un fast-forward (ej. cuando ambas ramas tienen commits diferentes), al comentar /ff la acción falla y se muestra *No se pudo propagar el código*



## Supuestos

- Los test se ejecutan automáticamente cuando hay un push o pull request dirigido a **main**.
- La rama default del proyecto es **main**

## Extra
Se adjunta un anexo visual en PDF con imágenes de la ejecución.
