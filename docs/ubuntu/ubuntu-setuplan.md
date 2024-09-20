# Bước 1: Xác định tên của giao diện mạng
```cmd
ip addr
```

# Bước 2: Chỉnh sửa cấu hình mạng với netplan
```
ls /etc/netplan/
```

# Bước 3: Sử dụng vim và chỉnh sửa file trong thư mục netplan
```cmd
sudo apt install vim
```

```cmd
vim /etc/netplan/50-cloud-init.yaml
```

```yaml
network:
    version: 2
    ethernets:
        enp2s0:
            dhcp4: no
            addresses:
            - 192.168.0.110/24
            gateway4: 192.168.0.1
            nameservers:
              addresses:
                - 8.8.8.8
                - 8.8.4.4
```

`ESC` và `:wq`

# Bước 4: Áp dụng cấu hình
```cmd
sudo netplan apply
```


# Bước 5: Kiểm tra lại cấu hình
```
ip addr
```