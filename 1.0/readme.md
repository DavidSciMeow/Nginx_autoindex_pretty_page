```
server {
....//其他配置

    location /autoindex.html {
        root 这个文件的存放位置(绝对路径)
    }

    location / {
        root 你的要做网盘的根目录(绝对路径)

        autoindex on;
        autoindex_format html; 
        autoindex_exact_size on; 
        autoindex_localtime on; 

        charset utf-8,gbk;

        add_after_body /autoindex.html;
    }

....//其他配置
}
```
