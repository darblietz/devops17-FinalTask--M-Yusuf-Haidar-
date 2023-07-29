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























