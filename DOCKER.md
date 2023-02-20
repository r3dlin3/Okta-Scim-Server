# Docker

Some commands to use Docker

## Develop

Prompt Windows:

```
docker run -it --rm -v %pwd%:/app node:16 bash
```

PowerShell:

```
docker run -it --rm -v ${pwd}:/app node:16 bash
```

```
docker run -it --rm -v ${pwd}:/app -p 49160:8080 node:16 bash
```

## Build

```
docker build -t nodejs-scim-server:latest .
```

## Run

```
docker run --rm -p 49160:8080 nodejs-scim-server:latest
```