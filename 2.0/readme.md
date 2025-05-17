nginx需要安装 nginx-extras
```
sudo apt install nginx-extras
```
nginx主要配置需要添加
```
load_module modules/ngx_stream_module.so;
load_module modules/ngx_http_dav_ext_module.so;
```
服务器server块
```
server
{
    server_name nasadmin.electronicute.cn;
    listen 80;
    gzip on;

    #auth_basic "Restricted";
    #auth_basic_user_file ....某个pwd

    location / {
        root /....某个路径
        index index.html;
        autoindex on;
        charset utf-8,gbk;
        dav_methods     PUT DELETE MKCOL COPY MOVE;
        dav_ext_methods PROPFIND OPTIONS;
        create_full_put_path on;
        dav_access user:rw group:rw all:r;
        limit_except GET HEAD OPTIONS PROPFIND {
            allow all;
        }
    }
}
```
