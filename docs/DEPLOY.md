# HyperDrop reverse proxy (example with nginx on api.hyperdrop.com)
# Assumes Dart presence server runs at 127.0.0.1:8787

server {
    listen 80;
    server_name api.hyperdrop.com;

    location /api/ {
        proxy_pass http://127.0.0.1:8787;
        proxy_set_header Host System.Management.Automation.Internal.Host.InternalHost;
        proxy_set_header X-Real-IP ;
        proxy_set_header X-Forwarded-For ;
        proxy_set_header X-Forwarded-Proto ;
    }

    location /downloads/ {
        root /var/www/hyperdrop; # place android.apk, windows.zip, hyperdrop-web-public.zip here
    }
}
