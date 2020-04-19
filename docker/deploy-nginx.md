 the "ssl" directive is deprecated, use the "listen ... ssl" directive instead in /etc/nginx/conf.d/default.conf:6

Listen 443 ssl





docker run  --name mini-nginx -d -p 80:80 -v/usr/local/etc/nginx/html:/usr/share/nginx/html -v /usr/local/etc/nginx/conf/nginx.conf:/etc/nginx/nginx.conf -v /usr/local/etc/nginx/conf.d:/etc/nginx/conf.d  -v /usr/local/etc/nginx/logs:/var/log/nginx  -v /usr/local/etc/nginx/conf/mini.antbeat.com:/usr/local/nginx/conf nginx

-v /etc/letsencrypt:/etc/letsencrypt



监听80 443

 docker run  --name mini-nginx -d -p 80:80 -p 443:443 -v/usr/local/etc/nginx/html:/usr/share/nginx/html -v /usr/local/etc/nginx/conf/nginx.conf:/etc/nginx/nginx.conf -v /usr/local/etc/nginx/conf.d:/etc/nginx/conf.d  -v /usr/local/etc/nginx/logs:/var/log/nginx  -v /usr/local/etc/nginx/conf/mini.antbeat.com:/usr/local/etc/nginx/conf/mini.antbeat.com nginx



K Apr 19 16:25 servert.crt
-rw-rw-r-- 1 antbeat antbeat 1.7K Apr 19 16:25 servert.key

/usr/local/etc/nginx/conf/mini.antbeat.com/servert.key

/usr/local/etc/nginx/conf/mini.antbeat.com/servert.crt