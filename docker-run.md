# docker run commands for launching apps

## attu
```docker run -d -p 8800:3000 -e MILVUS_URL=http://host.docker.internal:19530 zilliz/attu:v2.4.0```


```docker run -d -p 3000:8080 --gpus all --add-host=host.docker.internal:host-gateway OLLAMA_BASE_URL=http://127.0.0.1:11434 -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:cuda```

