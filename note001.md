# 自行建立Docker映像檔儲存庫

## 需求

當使用K8S時，往往會需要一個可以裝容器的Docker映像檔儲存庫。

當

## docker-compose.yaml

```yaml
version: '2'
services:
  registry-web:
    image: hyper/docker-registry-web:latest
    ports:
      - 8080:8080
    environment:
      REGISTRY_URL: http://registry:5000/v2
      REGISTRY_NAME: 127.0.0.1:5000
    networks:
      - registry-net
    depends_on:
       - registry
  registry:
    image: registry:2
    ports:
      - 5000:5000
    networks:
      - registry-net

networks:
  registry-net:
```