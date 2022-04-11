### Now we get install nginx
## 3 Ways

- By repo
- By yum
- By build source


Trang chủ : https://nginx.org

Phiên bản ổn định mới nhất : 1.18.0

### now we install by repo, because it's easy!


#### B1: Update các package có sẵn:

```

yum update -y

yum upgrade -y

```
##### B2: Khởi tạo repo NGINX:

```

vi /etc/yum.repos.d/nginx.repo

```

Thêm vào nội dung sau:

```

[nginx]

name=nginx repo

baseurl=http://nginx.org/packages/centos/7/$basearch/

gpgcheck=1

```

#### B3: Import chữ ký xác thực:

```

wget --no-check-certificate -O nginx_signing.key https://nginx.org/keys/nginx_signing.key

rpm --import nginx_signing.key

```

#### B4: Cập nhật thông tin repo:

```

yum repolist

```

#### B5: Cài đặt NGINX thông qua repo trước đó:

```

yum --disablerepo=* --enablerepo=nginx install nginx -y

```

#### B6: Cấu hình firewalld cho phép port 80:

```

firewall-cmd --zone=public --permanent --add-port=80/tcp

firewall-cmd --reload

```

B7: Khởi động và cấu hình startup cho dịch vụ:

```

systemctl start nginx.service

systemctl enable nginx.service

```

#### B8: Mở trình duyệt nhập IP của server để kiểm tra:

```

http://192.168.5.10

```

### Cài đặt trên Ubuntu 18.04
#### B1: Update các package sẵn có:

```

sudo apt-get update -y

sudo apt-get upgrade -y

```

#### B2: Khởi tạo repo NGINX trong file sources.list :

```

sudo vi /etc/apt/sources.list

```

Thêm vào nội dung sau :

```

deb http://nginx.org/packages/ubuntu/ bionic nginx

deb-src http://nginx.org/packages/ubuntu/ bionic nginx

```

#### B3: Import chữ ký xác thực:

```

wget --no-check-certificate -O nginx_signing.key https://nginx.org/keys/nginx_signing.key

sudo apt-key add nginx_signing.key

```

#### B4: Cập nhật thông tin repo :

```

sudo apt-get update

```

#### B5: Cài đặt NGINX :

```

sudo apt-get install -y nginx

```

#### B6: Cấu hình firewall cho phép port 80 :

```

sudo ufw allow 80/tcp

```

#### B7: Khởi động và cấu hình startup cho dịch vụ :

```

service nginx start

sudo update-rc.d nginx defaults

sudo update-rc.d nginx enable

```

#### B8: Mở trình duyệt nhập IP của server để kiểm tra

Các file cấu hình cơ bản của NGINX

banner test
Cloud Server - Giải pháp đám mây giúp vận hành website ổn định, nhanh chóng
/etc/nginx/nginx.conf : file cấu hình chính

/usr/local/nginx/conf.d/ : thư mục chứa các file cấu hình riêng (như virtual host,...)

/usr/share/nginx/html : thư mục chứa source code web

Một số lệnh cơ bản với NGINX

Khởi động NGINX :

```

nginx

```

Dừng dịch vụ NGINX

```

nginx -s quit

```

Kiểm tra cú pháp cấu hình NGINX :

```

nginx -t

```

Load lại cấu hình NGINX mà không cần khởi động lại dịch vụ :

```

nginx -s reload

```

Mở trực tiếp file log của NGINX :

```

nginx -s reopen

```



