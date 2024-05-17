# Installation guide

URL:
https://hub.docker.com/r/ollama/ollama

### Install Nvidia GPU (si aplica)

**Install Nvidia driver**

```bash
curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg

curl -s -L https://nvidia.github.io/libnvidia-container/stable/deb/nvidia-container-toolkit.list | sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' | sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list

sudo apt-get update

sudo apt-get install -y nvidia-container-toolkit
```

**Configure Docker to use Nvidia driver**

```bash
sudo nvidia-ctk runtime configure --runtime=docker
sudo systemctl restart docker
```

## Run the project container

This project install ollama and flowiser in the same container

1. `docker-compose up -d`
2. Open [http://localhost:3000](http://localhost:3000) to access **flowise**
3. Open [http://localhost:11434](http://localhost:11434) to access **ollama**
4. You can bring the containers down by `docker-compose stop`

When you run the docker-compose, the following containers are started:

-   agents
    -   ollama
    -   flowise

## Install the llama3 model

From the ollama API documentation:
https://github.com/ollama/ollama/blob/main/docs/api.md

You need to install the `llama3` model in ollama:

```bash
curl  -X POST 'http://localhost:11434/api/pull' -d '{"name": "llama3"}'
```

To verify that the model is installed, open [http://localhost:11434/api/tags](http://localhost:11434/api/tags)

# Guide to use the project

To start the project, run the following command:

```bash
docker-compose up -d
```

To stop the project, run the following command:

```bash
docker-compose stop
```
