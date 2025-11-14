# Edge Impulse - Docker Environment (Ubuntu 18.04 / Jetson)

Ambiente Docker configurado para rodar o **Edge Impulse CLI** em sistemas baseados em **Ubuntu 18.04**  ideal para uso em dispositivos **NVIDIA Jetson TX2** ou ambientes legados sem suporte direto.

### Verificar versão do docker no TX2

```bash
docker --version
```

## Verificar se a câmera está funcionando

```bash
ls /dev/video*
```
```bash
gst-launch-1.0 v4l2src device=/dev/video0 ! videoconvert ! xvimagesink
```

## Verificar se a câmera funciona no TX2

```bash
 ls /dev/video*
```

## teste o vídeo
```bash
 gst-launch-1.0 v4l2src device=/dev/video0 ! videoconvert ! xvimagesink
```

## Rodar inferência do Edge Impulse (com câmera) no Docker

```bash
 sudo docker run --rm -it \
--runtime nvidia --gpus all \
-p 1337:1337 \
--device /dev/video0:/dev/video0 \
public.ecr.aws/g7a8t7v6/inference-container:c94e7ccaca5d3e76e7ed6b046d7a5108b8762707 \
--api-key EI_SUA_API_KEY_AQUI \
--run-camera
```



