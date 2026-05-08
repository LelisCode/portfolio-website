
# Project my web site

sudo apt update

sudo apt install docker.io -y

sudo systemctl start docker

sudo systectl enable docker 

docker --version

sudo usermod -aG docker ubuntu

#  APÓS CRIAR ARQUIVO CI

docker pull username/portfolioweb-site:latest

docker run -d -p 8080:8080 --name portfolioweb username/portfolioweb-site:latest

# APÓS CRIAR ARQUIVO CD
sudo apt install nginx -y

sudo systectl start nginx

sudo systemctl enable nginx

sudo nano /etc/nginx/sites-available/docker-app


      serve {
                listen 80;

                location / {
                    proxy_pass: http//localhost:8080;
                    proxy_set_header: host $host;
                    proxy_set_header: X-Real-IP $remote_addr;

                }
            }
