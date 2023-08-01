# Monitoring
### Node Exporter
- Ada 3 node-exporter masing-masing terinstall diservernya :<br><br>![1](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/1759240e-7d62-419f-a926-3980ecfaac07)<br><br>
![2](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/ce9c5fc7-3958-43de-9505-02acfb37a8dd)<br><br>![3](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/34114e0e-40e9-4112-965e-1e763ce9c5d7)
<br><br>
### Prometheus
- prometheus sudah terinstall pada server monitoring berikut sudah disematkan file config prometheus.yml untuk penambahan target node-exporter <br><br>
![4](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/542ff046-783c-4f91-8067-ed71454ded41)<br><br>

### Setup Grafana
- menambahkan data source prometheus terlebih dahulu di Grafana <br><br>![5](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/ab635b4c-9918-4ce2-adb9-a7474458c181)
<br><br>![6](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/0586ed7b-2b72-45d3-8d58-11ad97d5be64)<br><br>![7](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/47eab3da-dd73-44d7-ac41-960a1f7dcd25)<br><br>
- Disini saya menggunakan import dashbord "node exporter full" digrafana labs dengan Copy ID atau donwload json-nya :<br><br>
![1](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/badbd503-64aa-4e3c-a2b5-d491ac6caef0)<br><br>
![2](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/c876ca12-50f7-4d94-9a66-2b0cb1dc0f79)<br><br>
![3](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/be6b74ce-e919-476b-8d13-e0e535b5d4be)<br><br>
![4](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/c8d61707-26bc-4ec0-9280-9f3bbb76fd5a)<br><br>
![5](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/e22b35a8-f86b-43e2-a86a-cda3db34a0be)<br><br>

### Alert Grafana
- disini saya menggunakan telegram untuk alert grafana <br><br>
  ![1](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/37e0209c-f6a9-494d-a508-d2887ad44e23)<br><br>
  ![2](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/e3155cc5-a16a-4f28-97cb-c8d0c5ef7b98)<br><br>
  ![3](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/96fa9987-c4d5-4637-a6f9-2517ce8a75e8)<br><br>
  
### Alert Rules
- alert rules ada 3 parameter yaitu :
  - CPU  Usage Over 80%<br><br>![1](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/b6a460a7-b9fe-4b5d-8304-6a50fb05def5)<br><br>
  - RAM Usage Over 10%<br><br>![2](https://github.com/darblietz/devops17-FinalTask--M-Yusuf-Haidar-/assets/98991080/095b5e86-5805-4503-aa87-34da72bbc9f5)<br><br>
  - Low Storage Warning









