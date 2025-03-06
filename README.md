# test-final

= Cmd for docker install
  - curl -fsSL https://get.docker.com/ -o get-docker.sh
  - sudo sh get-docker.sh

- 2:
  - sudo apt update && sudo apt install -y nginx
  - sudo systemctl start nginx
  - sudo systemctl enable nginx

- 3:
  - cd /var/www/html
  - sudo nano index.html (Ctril+O to save , Press Enter , Ctrl+x to exit)

- 4:
  - sudo apt update
  - sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
  - curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
  - echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  - sudo apt update
  - sudo apt install -y docker-ce docker-ce-cli containerd.io
  - sudo docker run hello-world

- 5:
  - sudo docker pull nginx
  - sudo docker run --name mynginx -d -p 8080:80 nginx

- 6:
  - mkdir mynginx && cd mynginx   
  - docker pull timetitipon/mynginx-custom
  - sudo docker run --name custom-nginx -d -p 8081:80 mynginx-custom (On VM)

- 7:
  - docker build -t mynginx-custom .
  - docker tag mynginx-custom timetitipon/mynginx-custom
  - docker push timetitipon/mynginx-custom (on powershell vs code) 

- 8:
  - mkdir ~/mywebsite
  - touch index.html
  - vi index.html (and copy content from question 3)
  - sudo docker run --name mapped-nginx -d -p 8082:80 -v ~/mywebsite:/usr/share/nginx/html nginx

- 9:
  - mkdir ~/dockercompose && cd ~/dockercompose
  - docker-compose up -d

- 10:
  - mkdir ~/mydocker && cd ~/mydocker
  - touch index.html
  - vi index.html (and add this content)
  - <html>
    <body><h1>Docker Compose Custom Page</h1></body>
    </html>

  - touch docker-compose.yml
  - vi docker-compose.yml (and add this content)
  - version: '3'
    services:
      web:
      image: nginx
      ports:
        - "8083:80"
      volumes:
        - ./index.html:/usr/share/nginx/html/index.html
    
    - sudo docker compose up -d

   


    
