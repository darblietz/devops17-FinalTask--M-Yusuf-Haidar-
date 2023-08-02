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



