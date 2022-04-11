# now we get config vhost for nginx

### vhost web tĩnh

Ở đây tôi sử dụng thư mục sẵn có của nginx là /usr/share/nginx... để lưu lại source code 

B1: Sau các bước cài đặt thành công, chúng ta tiến hành vào /usr/share/nginx để tạo thu muc

```
mkdir /usr/share/nginx/web1/html
mkdir /usr/share/nginx/web2/html
```



B2: Them file code

```
vi /usr/share/nginx/web1/html/index.html
```

`day la web1`

B3: Tuong tu B2, chung ta tao cho web 2

```
vi /usr/share/nginx/web2/html/index.html
```

`day la web2`

**co mot so luu y tren mang la tao `site-enable` & `sites-available` nhung tuy nhien viec phan quyen vat va hon nhieu so voi viec su dung luon thu muc san co cua `nginx`**

B4: Tien hanh copy file default nginx

```
cp /etc/nginx/conf.d/default /etc/nginx/conf.d/web1.conf
cp /etc/nginx/conf.d/default /etc/nginx/conf.d/web2.conf

```
B5: Vao thu muc web1.conf de sua duong dan tro source code

thay the duong dan 
`location {\
root /usr/share/nginx/html/
`
thanh duong dan chua source code cua ban

`
root /usr/share/nginx/web2/html/
`

lam tuong tu voi web 1 nua
 - duong dan sau khi thay doi la

 `- root /usr/share/nginx/web1/html/`

 B6: them duong dan access log va error log

 B7: Run command 

 ``` systemctl reload nginx```
 ```nginx -t```
 
