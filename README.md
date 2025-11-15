# Edge Impulse - Docker Environment (Ubuntu 18.04 / Jetson)

Ambiente Docker configurado para rodar o **Edge Impulse CLI** em sistemas baseados em **Ubuntu 18.04**  ideal para uso em dispositivos **NVIDIA Jetson TX2** ou ambientes legados sem suporte direto.

### Verificar versão do docker no TX2

```bash
docker --version
```

## Listar diretório 

```bash
 ls 
```

## Listar containers existentes
```bash
 docker ps -a
```

## Iniciar o container

```bash
 docker start edge-impulse-tx2

```

## Entrar no container em modo interativo

```bash
 docker exec -it edge-impulse-tx2 /bin/bash

```

## Rodar o Edge Impulse Linux Runner com servidor HTTP

```bash
 edge-impulse-linux-runner --force-target runner-linux-aarch64 --run-https-server 1337

```

<img width="1920" height="1080" alt="Screenshot from 2025-11-15 02-59-00" src="https://github.com/user-attachments/assets/80eb6dc8-cd9f-41fb-a7d4-dc6c6a737ace" />





