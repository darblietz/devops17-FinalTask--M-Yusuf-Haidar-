# Deployment
### Staging
- frontend dumbmerch staging<br><br>
  Setelah diclone dari git repository personal, lalu pindah ke branch staging <br><br>
```
git checkout staging
```
![1](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/0f1c877c-5355-4fa2-a664-2592b0b1e963)<br><br>
  disini saya membuat docker images seminimal mungking ukurannya dengan membuat file .dockerignore <br><br>
```
nano .dockerignore
```
![5  cat dockerignore fe](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/162634a6-1a19-40e7-b147-836707f14ab1)
<br><br>
  lalu membuat file config Dockerfile untuk kebutuhan membuat docker darblietz/fe-dumbmerch-staging<br><br>
```
FROM node:16-slim
WORKDIR /app
COPY . .
RUN npm install
EXPOSE 3000
CMD [ "npm", "start" ]
```
  kemudian membuat docker image dengan perintah berikut :
```
docker build -t darblietz/fe-dumbmerch-staging:latest .
```
![2](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/d805ab2c-dae6-4e64-95e0-bb830c27b8a0)<br><br>

- backend dumbmerch staging<br><br>
   Setelah diclone dari git repository personal, lalu pindah ke branch staging <br><br>
![3](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/510551fe-246c-434d-a4f2-e02bd70e1ad3)<br><br>
  Lalu membuat docker images seminimal mungking ukurannya dengan membuat file .dockerignore <br><br>
```
.git
**/*.tar.gz
**/*.tgz
**/*.iso
**/*.raw
**/*.work-*
```
![4  cat dockerignore be](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/fbe822f7-b50f-47f5-b6c6-6ff36d87d5ce)<br><br>
  kemudian membuat docker image dengan perintah berikut :
```
docker build -t darblietz/fe-dumbmerch-staging:latest .
```
![6](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/b25af5c4-b6fe-429f-874b-3ce651abe95c)<br><br>

### Docker compose
  file config docker-compose.yml untuk kebutuhan docker compose :
```
version: "3.8"
services:
   db:
    container_name: db-dumbmerch
    image: postgres:latest
    ports:
      - 5432:5432
    volumes:
      - ~/postgresql:/var/lib/postgresql/data
    environment:
      - POSTGRES_USER=haidar
      - POSTGRES_PASSWORD=password
      - POSTGRES_DB=dumbmerch

   backend:
    depends_on:
      - db
    image: darblietz/be-dumbmerch-staging:latest
    container_name: be-dumbmerch
    stdin_open: true
    restart: unless-stopped
    ports:
      - 5000:5000
   frontend:
    image: darblietz/fe-dumbmerch-staging:latest
    container_name: fe-dumbmerch
    stdin_open: true
    restart: unless-stopped
    ports:
      - 3000:3000
```
  Lalu jalankan docker compose dengan perintah berikut :
```
docker compose up -d
```
![7](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/9a10db9b-3823-4b10-886c-e5efea61fe73)<br><br>
![8](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/027739ac-3332-4c0f-b1bb-b09230d5877d)<br><br>







