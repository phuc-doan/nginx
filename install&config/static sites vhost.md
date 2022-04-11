# Now we get config vhost for nginx

### vhost web tĩnh

- Ở đây tôi sử dụng thư mục sẵn có của nginx là /usr/share/nginx... để lưu lại source code 

#### B1: Sau các bước cài đặt thành công, chúng ta tiến hành vào `/usr/share/nginx` để tạo thu muc

```
mkdir /usr/share/nginx/web1/html
mkdir /usr/share/nginx/web2/html
```

![image](https://user-images.githubusercontent.com/83824403/162659876-2ba78be8-4b8b-4163-9ec6-20ee964761ec.png)


#### B2: Them file code

```
vi /usr/share/nginx/web1/html/index.html
```

`day la web1`

![image](https://user-images.githubusercontent.com/83824403/162660051-602ecb63-3a82-41c4-bea6-d39325a551f1.png)


#### B3: Tuong tu B2, chung ta tao cho web 2

```
vi /usr/share/nginx/web2/html/index.html
```

`day la web2`

**co mot so luu y tren mang la tao `site-enable` & `sites-available` nhung tuy nhien viec phan quyen vat va hon nhieu so voi viec su dung luon thu muc san co cua `nginx`**

#### B4: Tien hanh copy file default nginx

```
cp /etc/nginx/conf.d/default /etc/nginx/conf.d/web1.conf
cp /etc/nginx/conf.d/default /etc/nginx/conf.d/web2.conf

```
#### B5: Vao thu muc web1.conf de sua duong dan tro source code

thay the duong dan 
``location {\
root /usr/share/nginx/html/
``
thanh duong dan chua source code cua ban

`
root /usr/share/nginx/web2/html/
`

lam tuong tu voi web 1 nua
 - duong dan sau khi thay doi la

 `- root /usr/share/nginx/web1/html/`

![image](https://user-images.githubusercontent.com/83824403/162659835-4d74ff41-84da-477a-961d-3ee8789f1278.png)



 #### B6: them duong dan access log va error log

 #### B7: Run command 

 ``` systemctl reload nginx```
 ```nginx -t```
 
 **lưu ý:
 
 **dùng *`tail -5  /var/log/nginx/error.log`* để check log xem nếu có lỗi**
 
 **Câu lệnh *`ps x | grep nginx`* để có thể tìm pid nginx đang chạy**
 
 **ngoài ra *`lsof -p pid`* để xem user chủ quản**
 
 - Tuy nhiên SD này cho những trường hợp tạo nginx vhost bằng thư mục khác ví dụ như `/var/www/html/...`, sau đó phân quyền cho thư mục path code mode `755` Và change own cho path là user của nginx

**- Nhưng trường hợp này tôi làm là tạo ngay trên thư mục có sẵn của nginx là `/usr/share/...`**

##### Như này là thành công
![image](https://user-images.githubusercontent.com/83824403/162660551-80d76934-6764-4de1-9efa-535780c797b5.png)
 
 
 
 Author: Doan Van Phuc
