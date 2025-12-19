```conf
server {
    listen 80; 
    server_name localhost;
    root /var/www/app/public;

    index index.php index.html index.htm;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location ~ /\.(env|git|htaccess) {
        deny all;
    }

    location ~ ^/(storage|vendor) {
        deny all;
    }


    location ~ \.php$ {
        include fastcgi_params;
        fastcgi_pass php-fpm:9000;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    }

    error_log  /var/log/nginx/error.log;
    access_log /var/log/nginx/access.log;
}
```

- **listen: 80** -> port
- **server_name:** -> szervernév
- **root:** -> gyökérkönyvtár
- **index:** -> index fájlok
- **location /:** -> hely
- **try_files** -> fájl keresés:
    - ez úgy müködik, hogy megnézzük elsőnek hogy van e ilyen fájl, után hogy mappa és végül ha nincs semmi akkor átirányít az index.php-ra
        - Azt olvastam, hogy ez a beállítás Larvel-hez kell, és ez a: front controller pattern
- **fastcgi:**
        -> Alap FastCGI környezeti változók, utána pedig a php-fpm szükséges változók
        -> PHP-FPM szerver címe és portja (default: 9000 PORT),
        -> megmondjuk például melyik fájlt futtassa a PHP-FPM

- **Logolások:**
    - error_log: -> hiba napló helye
    - access_log: -> hozzáférési napló helye

```
    location ~ /\.(env|git|htaccess) {
        deny all;
    }

    location ~ ^/(storage|vendor) {
        deny all;
    }
```

> Tiltja a hozzáférést az env, git, htaccess, storage és vendor fileokhoz, tulajdoképpen egy .gitignore szerűség (?!)

Forrás:
- *Medium*
- *Serverion nginx config generátor:* https://www.serverion.com/nginx-config/#?0.domain=localhost&0.index=index.html&0.fallback_html