### B1: file cấu hình của nginx sẽ gồm 

### B2: Them config 

- Vao /etc/nginx/conf.d
- Copy file defaut.conf sang thu muc moi. O day thu muc cua minh la `doanvanphuc.conf`

```
cd /etc/nginx/conf.d
cp default.conf doanvanphuc.conf
```

### B3: vao thu muc phucdv.conf sua 1 vai thong so

- server name: doanvanphuc.com /theo hosts cua ban
-  access_log  /var/log/nginx/doanvanphuc.access.log  main;
-  error_log  /var/log/nginx/doanvanphuc.error.log;
- Phan location trong http, phan root se tro vao duong dan chua path code tao o **Buoc 5** nhu ben duoi

**co the them 1 vai thong so try_files $uri $usri/ =404; tuy nhien minh ko them**

#### B4: Vao thu muc chua path code

```
cd /usr/share/nginx
```

#### B5: Tao path moi

```
mkdir webtest
```

*noi chung phan tao pathcode la gi ko quan trong, ti nua chung ta se chown cho user nginx va dung tu file conf trong `/etc/nginx/conf.d/....` tro vao path vua tao*

##### Sau do change owner cho pathcode, de user co quyen choc vao va doc du lieu

```
chown -R nginx. webtest
```

#### B6: tao file html

```
vi index.html

day la web doanvanphuc.com

```

#### B7: Reload and test

``` 
systemctl reload nginx
nginx -t
```


##### moi thu ok la xong roi