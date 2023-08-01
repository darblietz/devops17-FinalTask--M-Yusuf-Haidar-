# Web Server
### Cloudflare<br><br>
![1](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/d9bef008-efd5-4bb4-90a6-4ae5b373ed21)<br><br>
### NGINX<br><br>
- file config install-nginx.yml untuk isntalasi nginx pada server gateway :<br><br>
```
---
- become: true
  gather_facts: false
  hosts: gateway
  tasks:
    - name: Installing nginx
      apt:
        name: nginx
        state: latest
        update_cache: yes

    - name: delete default nginx site
      file:
        path: /etc/nginx/sites-enabled/default
        state: absent

    - name: Copy rproxy.conf
      copy:
        src: /home/rommel/ansible/config/reverse-proxy/  # Add the file name to the source path
        dest: /etc/nginx/sites-enabled

    - name: Check nginx
      command: nginx -t

    - name: Reload nginx
      service:
        name: nginx
        state: reloaded
```
### SSL Certbot<br><br>
![2](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/29d79cc2-5280-4a27-899d-adfae092d5f8)<br><br>
![3](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/c16d2e25-307e-413d-8ab1-edfb9dcfb3b5)<br><br>
![4](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/63e5f593-3c96-4023-8570-e7606efbf879)<br><br>
![5](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/c07fd24e-6814-434d-8472-c6edb6761496)<br><br>
![6](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/581a2b1c-47d7-4baa-a171-2ac45a1d0d53)
<br><br>![7](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/fd3dd87c-ac85-49db-a03f-58cdcfccd221)
<br><br>![8](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/e10b0f45-0cda-4396-be6c-faf3ca01fb44)
<br><br>![9](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/75507db3-1698-4e00-9f63-8ffb0d05749b)
<br><br>![10](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/9279ec4a-119d-4142-b32a-113d2a4bf9f4)
<br><br>






