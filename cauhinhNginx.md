# Virtual Host 1: Beta App (Port 8080)
server {
    listen 8080;
    listen [::]:8080;

    server_name _;

    root /var/www/beta-app/html;
    index index.html;

    access_log /var/log/nginx/beta-app.access.log;
    error_log /var/log/nginx/beta-app.error.log;

    location / {
        try_files $uri $uri/ =404;
    }
}

# Virtual Host 2: Internal App (Port 8090)
server {
    listen 8090;
    listen [::]:8090;

    server_name _;

    root /var/www/internal-app/html;
    index index.html;

    access_log /var/log/nginx/internal-app.access.log;
    error_log /var/log/nginx/internal-app.error.log;

    location / {
        try_files $uri $uri/ =404;
    }
}