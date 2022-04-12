## `Cấu hình nginx với php-fpm` ⚙⚙

![image](https://user-images.githubusercontent.com/83824403/162784870-3361b1c3-109e-4568-99ab-562849f54037.png)


**Mình đã cài php5.4 nhưng sau đó phải đẩy lên ver 7.4 cho ổn đinh nên docs có phần HD `upgrde php version luôn`**

### Bước 1: Cài cắm php/ Update lên bản 7.4

✔ *PHP 7 ra đời khá lâu và cộng đồng đủ thời gian để trải nghiệm các cách tổ chức code mới mẻ

✔ *khả năng chịu tải tốt hơn,✔  thời gian load trang cũng cải thiện đáng kể.*

✔ *Đặc biệt nếu bạn nâng cấp PHP 5.x sang PHP 7.x, tốc độ load của WordPress được cải thiện đáng kể. ✔ *

✔ *Nói chung phiên bản PHP 7 trở về sau tốt hơn rất nhiều so với phiên bản PHP 5.6 ✔✔✔ *

### `Ưu điểm khi nâng cấp PHP 7`

- **So với PHP 5 thì khi nâng cấp PHP 7 với nhiều ưu điểm nổi trội ở phiên bản này như là:**

- Giới hạn xử lý requests của PHP 7 là gấp đôi PHP 5.6,🚗 🚗 và nó đáp ứng từng request nhanh hơn.

- Trong xử lý dữ liệu, PHP 7 là hơn 3,5  lần bộ nhớ 🎞🎞 hiệu quả hơn so với PHP 5.6.

- Nhiều cộng đồng được thành lập, có thể giúp các nhà phát triển, xử lý sự cố PHP và hỗ trợ một số kỹ thuật khác 😎😎.


## Làm việc với 1 số file sau đây 🛴🛴 

### `php-fpm.con` :💥 Cấu hình extensiton php-fpm cho webserver

### `/etc/php/7.2/fpm/pool.d/*.conf`: 💥 thì pool.d chứa conf site mặc định là `www.conf`


- *Kiểu giống Vhost nginx*

### 💥 phpscrips và webserver nginx sẽ giao tiếp với nhau qua: - TCP socket & File socket 

-  *tiến trình php-fpm và process nginx độc lập và ko giao tiếp đc nên cần có 1 thằng ở giữa là tcp socket hoặc file socket**
  
              
              
              
              

## 😎😎 Ok Vào việc ✈✈❤

- Cài đặt và nâng cấp PHP 7 trên CentOS

- Đầu tiên, trước khi nâng cấp PHP 7 bạn cần gỡ cài đặt các phiên bản cũ của PHP. Tiếp theo, bạn kiểm tra phiên bản PHP của mình với `php-v`

![image](https://user-images.githubusercontent.com/83824403/162785730-4e97bda4-3c9e-41ab-8c6b-c3c6fc692579.png)


#### Để cài đặt và nâng cấp PHP 7, bạn cần kích hoạt EPEL và Remi repository trên CentOS 7 với câu lệnh sau:

- Cài đặt EPEL

```
yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
```

- Cài đặt phiên bản mới nhất của remi repository
```
# CentOS 6 
rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-6.rpm

# CentOS 7 
rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
```

- Đăng nhập máy chủ của bạn để cài đặt yum-utils & bật kho lưu trữ EPEL. 💻 Nó cần thiết cho việc upgrade hay cài đặt của các bước sau.

```
yum install epel-release yum-utils -y
```

- Server của bạn đã được thiết lập để cài đặt PHP 7.0, PHP 7.1, PHP 7.2 hoặc PHP 7.3 theo dưới đây:

```
For PHP 7.3
yum --enablerepo=remi-php73 install php-xml php-soap php-xmlrpc php-mbstring php-json php-gd php-mcrypt
### For PHP 7.2
yum --enablerepo=remi-php72 install php-xml php-soap php-xmlrpc php-mbstring php-json php-gd php-mcrypt
### For PHP 7.1
yum --enablerepo=remi-php71 install php-xml php-soap php-xmlrpc php-mbstring php-json php-gd php-mcrypt 
### For PHP 7.0
yum --enablerepo=remi-php70 install php-xml php-soap php-xmlrpc php-mbstring php-json php-gd php-mcrypt

```

- Để định cấu hình kho lưu trữ PHP 7.x bạn sử dụng các câu lệnh dưới đây 🐟🐟🐟  

```
# PHP 7.0 
yum-config-manager --enable remi-php70  🐬
# PHP 7.1  
yum-config-manager --enable remi-php71  🐬

# PHP 7.2 
yum-config-manager --enable remi-php72  🐬

# PHP 7.3 
yum-config-manager --enable remi-php73   🐬
```


- Cài đặt các gói cơ bản cho VPS/Server

```
yum install php php-mcrypt php-cli php-gd php-curl php-mysql php-ldap php-zip php-fileinfo
```

- Tắt php repository tương ứng này đi vì bạn cần sử dụng PHP 7.x

```
# PHP 5.5 
yum-config-manager --disable remi-php55

# PHP 5.6 
yum-config-manager --disable remi-php56
```

- Cài đặt PHP Modules 🏃‍♂️
🏃‍♂️
- Sau khi đã cài đặt PHP 7x trên server. Bạn có thể cài đặt thêm một số PHP Modules cần thiết cho các ứng dụng:

```
### For PHP 7.3
yum --enablerepo=remi-php73 install php-xml php-soap php-xmlrpc php-mbstring php-json php-gd php-mcrypt

### For PHP 7.2
yum --enablerepo=remi-php72 install php-xml php-soap php-xmlrpc php-mbstring php-json php-gd php-mcrypt

### For PHP 7.1
yum --enablerepo=remi-php71 install php-xml php-soap php-xmlrpc php-mbstring php-json php-gd php-mcrypt 

### For PHP 7.0
yum --enablerepo=remi-php70 install php-xml php-soap php-xmlrpc php-mbstring php-json php-gd php-mcrypt
```

- Ngoài ra, bạn có thể tìm Modules có sẵn trong yum repository 🖥🖥   với lệnh như sau:

```
# yum --enablerepo=remi-php73 search php | grep php73 [For PHP 7.3]
```
#### Kiểm tra lại danh sách repository một lần nữa, đảm bảo phần remi tương tự như sau là được: `yum repolist all`


### Nếu mọi người cài ver 7x ngay từ đầu thì bỏ qua bước 1 và chuyển đến bước 2

### B2: Vào sửa thư mục `www-conf` có sẵn trong php-fpm

![image](https://user-images.githubusercontent.com/83824403/162787676-26652dc1-6c57-451b-98ba-46918820d95a.png)

- Một vài thông số chúng ta cần chỉnh


 ![image](https://user-images.githubusercontent.com/83824403/162787899-ec98e85a-0135-47d0-a9ec-0254cbde755d.png)
 
 ![image](https://user-images.githubusercontent.com/83824403/162787961-35cd4679-a3b2-42fd-add6-56eb893e221a.png)
 
 **Chỉnh file về `user, group` nginx và phần location như kia là được**
 
 ### B3: Vào file config của website Nginx `thêm 1 vài thông số để web enable tính năng PHP-FPM` 🛠🛠
 
 ```
 vi /etc/nginx/conf.d/web2.conf
 ```
 
 
 
 ![image](https://user-images.githubusercontent.com/83824403/162788785-7a8b5e08-26b4-483d-907d-2a708b3b9ce1.png)

**Chỉnh như file là được**

### B4: Tạo `index.php` để trình PHP scripts đọc file 

```
vi /usr/share/nginx/web2/index.php
```

```
<?php
echo <h1> hello php </h1>
?>
```
![image](https://user-images.githubusercontent.com/83824403/162789183-70fc652e-23d3-4e80-b0b9-6bb658c567b8.png)


### B5: Test với địa chỉ `web2.com/index.php`

**Nếu ra được text như trên là đã làm chính xác
 
 

 
 
 #### ĐƯờng dẫn log cần quan tâm nếu có sự cố khi test web
 ![image](https://user-images.githubusercontent.com/83824403/162788340-f2479029-68c0-4402-b09f-4fb939f55451.png)
 
 
 
 ### ❗ `*Lưu ý:*`
 
 - Lỗi xảy ra trong bài

1) Không để ý ver Php phải cài lại ( Upgrade lại )
2) Bug `Existing lock /var/run/yum.pid: another copy is running as pid 10432.`
 
 **Cách xử lý TH này là chạy command `kill_process`**
 - Như hình bên dưới 

![image](https://user-images.githubusercontent.com/83824403/162789745-139ae164-0537-4562-bd65-a1156d15322a.png)

### `Referrence: https://blog.cloud365.vn/linux/huong-dan-tao-virtualhost-trong-nginx/` 🔑🔑
