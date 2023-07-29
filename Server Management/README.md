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


