# Instrucciones para clonar submódulos y levantar el contenedor

Este proyecto utiliza **submódulos** de Git, por lo que es necesario inicializarlos y actualizarlos antes de construir el contenedor.

## Clonar e inicializar los submódulos

Ejecuta los siguientes comandos en el orden indicado:

```bash
git submodule init
```
> Inicializa la configuración de los submódulos del proyecto. Prepara Git para saber qué submódulos debe gestionar.

```bash
git submodule update --remote
```
> Descarga el contenido más reciente de cada submódulo desde sus repositorios remotos.

```bash
git submodule foreach git pull
```
> Recorre todos los submódulos y ejecuta un `git pull` dentro de cada uno para asegurarse de traer los últimos cambios.

```bash
git submodule update
```
> Actualiza los archivos del proyecto según las últimas versiones de los submódulos configuradas en el repositorio principal.

## Construir y levantar el contenedor Docker

Una vez que los submódulos estén actualizados, ejecuta:

```bash
sudo docker compose up --build
```
> Este comando construye las imágenes Docker necesarias (forzando la reconstrucción para capturar los cambios recientes) y levanta los servicios definidos en el archivo `docker-compose.yml`.
