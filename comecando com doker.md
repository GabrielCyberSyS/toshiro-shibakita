🐳 Passo a passo para instalar o Docker no Linux (ou WSL)

1️⃣ Atualize os pacotes do sistema

sudo apt update && sudo apt upgrade -y

2️⃣ Instale dependências necessárias
sudo apt install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release -y
    
3️⃣ Adicione a chave GPG oficial do Docker

sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
    sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    
4️⃣ Adicione o repositório Docker à lista de fontes APT
echo \
  "deb [arch=$(dpkg --print-architecture) \
  signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null



5️⃣ Atualize o APT novamente e instale o Docker Engine
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y


6️⃣ Verifique se o Docker está funcionando
sudo docker --version
sudo docker run hello-world

7️⃣ (Opcional) Permitir rodar Docker sem sudo
sudo usermod -aG docker $USER
newgrp docker
