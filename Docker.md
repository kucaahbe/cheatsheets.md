## Docker
### build an image
```bash
docker build -t image-name .
```
### run bash
```bash
docker run -ti image-name [bash]
```
### remove dangling images
```bash
docker image prune [-f]
```
## Docker compose
### compose up
```bash
docker compose up [--build] [-d]
```
### run specific container
```bash
docker compose run --rm server bash
```