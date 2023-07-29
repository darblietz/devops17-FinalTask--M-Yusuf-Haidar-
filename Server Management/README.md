# Server Management
### SSH
- ssh public key sudah diterapkan dalam terraform setiap server :<br><br>
```

terraform {
  required_providers {
    idcloudhost = {
      source = "bapung/idcloudhost"
      version = "0.1.3"
    }
  }
}

provider "idcloudhost" {
  auth_token = ""
}

resource "idcloudhost_vm" "appserver" {
  name = "haidar-appserver"
  os_name = "ubuntu"
  os_version = "20.04"
  vcpu = "2"
  memory = "2048"
  disks = "20"
  username = "haidar"
  initial_password = ""
  public_key = ""
  billing_account_id = ""
}

resource "idcloudhost_floating_ip" "firstIP" {
  name = "appserverIP"
  billing_account_id = "1200157626"
  assigned_to = idcloudhost_vm.appserver.id
}
```
![1  id_rsa pub](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/06e2aca5-8c1c-4b49-aa07-843aa2c3fb9f)<br><br>![2  authorized_keys appserver](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/e8236476-49af-4efa-b4ca-3dbcbd9ef40d)![3  authorized_keys gateway](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/b4ea3dc9-3557-4e13-86d4-f569c016d348)![4  authorized_keys monitoring](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/060ce6a7-9ad5-4763-8269-02beb051edef)![5  ssh](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/a44d137a-0692-49c9-b061-38316f9a8b4f)
<br><br>

- Untuk disable password login kita access ke directory /etc/ssh/sshd_config :<br><br>
  "PasswordAuthentication no"<br>![6  sshd_config](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/2f372ddf-6261-48fa-b785-4341f2490c3c)<br><br>

### Firewall
- Buat file config firewall.yml untuk instalasi ufw pada server gateway :
```
---
- become: true
  gather_facts: false
  hosts: gateway
  tasks:
    - name: install firewall
      apt:
        name: ufw
        update_cache: yes
        state: latest
    - name: enable ufw
      community.general.ufw:
        state: enabled
        policy: allow
    - name: rules
      community.general.ufw:
        rule: allow
        proto: tcp
        port: "{{ item }}"
      with_items:
      - 22
      - 80
      - 443
      - 3000
      - 5000
      - 3306
      - 9090
      - 9100
      - 8080
    - name: enable ufw
      community.general.ufw:
        state: reloaded
        policy: allow
```
![7  ansible-playbook firewall yml](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/26e9c296-004d-4883-9905-da2ccb96b312)<br><br>![8  sudo ufw verbose](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/b071e0e8-312a-4ee0-b249-d808ce4c887c)







