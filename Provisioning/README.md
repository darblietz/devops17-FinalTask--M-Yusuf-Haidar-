# Provision Servers using Terraform
- Pertama-tama membuat file berupa main.tf membuat server diprovider idcloudhost melalui terraform menggunakan registry bapung:<br><br>![1  idch](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/cce8bccc-c0a0-43eb-b504-4bac7d827f8f)<br><br>

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
  auth_token = "mTWvAHka6YmhUncBxKZyCpeL40C7Kyc0"
}

resource "idcloudhost_vm" "appserver" {
  name = "haidar-appserver"
  os_name = "ubuntu"
  os_version = "20.04"
  vcpu = "2"
  memory = "2048"
  disks = "20"
  username = "haidar"
  initial_password = "Haidar97"
  public_key = "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDzUJ3O14LdOhsRa6H0QAGfoPLC/ybczUdi04liDzoxRnuk12lgoSQGvyzJDUxJHBa33/q3wQgBCjl+B/R2N64BjBEbYfU>  billing_account_id = "1200157626"
}

resource "idcloudhost_floating_ip" "firstIP" {
  name = "appserverIP"
  billing_account_id = "1200157626"
  assigned_to = idcloudhost_vm.appserver.id
}
```
<br><br>
- selanjutnya melakukan inisiasi, validasi, plan, dan apply pada folder terraform :<br><br>
  ```
  terraform init |
  terraform validate |
  terraform plan |
  terraform apply
  ```
<br><br>
![5  init](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/9a2ac288-314b-4d27-a939-9eae483c887d)<br><br>![6  validate](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/274b2c27-8fe5-4857-958e-a2f4ca974221)<br><br>![7  plan](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/6bdf35e1-8f54-4915-b7c5-dcd422f55ba3)<br><br>![8  apply](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/d9cfcfe8-0f72-4094-a6cd-2ee54ca30768)<br><br>
- Result<br><br>![2  result haidar-appserver](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/a5cc09cf-23a0-44e8-9785-343d51580b4c)<br><br>![3  result haidar-gateway](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/f71579b2-a243-4dcf-a490-2c08a5e3ab08)<br><br>![4  result haidar-monitoring](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/447ee0ff-84ea-4b4b-8990-d463b9f06314)<br><br>

# Server configuration using Ansible

- Pertama membuat file configurasi ansible.cfg :<br><br>
```
[defaults]
inventory = Inventory
private_key_file = /home/rommel/.ssh/id_rsa
host_key_checking = False
interpreter_python = auto_silent
```
- Berikuntya membuat file Inventory untuk library dari server yang akan dikonfigurasi dengan ansible :<br><br>
```
[appserver]
103.179.56.88

[gateway]
103.179.56.156

[monitoring]
103.179.56.174

[appserver:vars]
ansible_user="haidar"
ansible_pythone_interpreter=/usr/bin/python3

[gateway:vars]
ansible_user="haidar"

[monitoring:vars]
ansible_user="haidar"
```
<br><br>


  
  























