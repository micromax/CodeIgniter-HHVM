# CodeIgniter

This is my personal modified version of CodeIgniter for use with HipHop VM (HHVM) and removal of unecessary code to support earlier versions of PHP

## Requirements
- PHP 5.4+ or HHVM 2.0+
- Nginx (recommended) or other HTTP server

## Sample Nginx Config
```
    location / {
        try_files $uri $uri/ /index.php;
    }

    proxy_redirect off;
    location ~ /index.php$ {
        proxy_set_header REQUEST_URI $request_uri;
        proxy_set_header X_FORWARDED_FOR $remote_addr;
        proxy_set_header Host my.domain.com;
        proxy_pass http://localhost:8000;
    }
```

## Sample HHVM Config
```
Server {
    Port = 8000
    IP = 127.0.0.1
 
    DefaultDocument = index.php
    ErrorDocument404 = index.php
 
    [...]
 
}
```
