# chromeos-dev-bootstrap
goal: document how to roll a dev / dev-ops-y machine on something like a pixelbook

## update debian
```bash
sudo apt-get -y update && sudo apt-get -y upgrade
```

## docker
```sh
sudo apt-get install -y  \
     apt-transport-https \
     ca-certificates     \
     curl                \
     gnupg2              \
     software-properties-common && \
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add - && \
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"
sudo apt-get -y update && \
sudo apt-get install -y docker-ce
```

## docker compose
```sh
sudo apt-get install -y docker-compose && \
sudo usermod -a -G docker $USER
```

## kubectl 
```sh
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl && \
chmod +x ./kubectl && \
sudo mv ./kubectl /usr/local/bin/kubectl && \
kubectl version
```

## helm 
```sh 
curl -LO https://get.helm.sh/helm-v2.14.3-linux-amd64.tar.gz && \
tar -zxvf helm-v2.14.3-linux-amd64.tar.gz && \
chmod +x linux-amd64/helm && \
sudo mv ./linux-amd64/helm /usr/local/bin/helm && \ 
rm -rf helm-*.tar.gz linux-amd64
```

## tf
```sh
export TER_VER="0.12.9" && \
wget https://releases.hashicorp.com/terraform/${TER_VER}/terraform_${TER_VER}_linux_amd64.zip && \
unzip terraform_${TER_VER}_linux_amd64.zip && \
chmod +x terraform && \
sudo mv terraform /usr/local/bin/ && \
which terraform && \
terraform -v
```

## git
```sh
git config --global user.email <Email ID>
git config --global user.name "<Full Name>"
```

## py3
```sh
sudo apt install -y python3-pip
```

## awscli
```sh
pip3 install awscli --upgrade --user
```

##  node
```sh
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash - && \
sudo apt-get install -y nodejs
```

## go
```sh
sudo add-apt-repository ppa:longsleep/golang-backports && \
sudo apt-get update -y && \
sudo apt-get install -y golang-go
```

## jq / build essential
```sh
sudo apt-get -y install build-essential jq
```

## gcloud
```sh
echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] http://packages.cloud.google.com/apt cloud-sdk main" | sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list && \ 
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key --keyring /usr/share/keyrings/cloud.google.gpg add - && \
sudo apt-get update && sudo apt-get install -y google-cloud-sdk
```
