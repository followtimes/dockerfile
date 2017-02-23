#build a image for nginx

#base image is nginx:latest(1.11.9)
FROM nginx
MAINTAINER followtimes <zhuhenghui@xiaomi.com>

WORKDIR /home/work/nginx

ENTRYPOINT ["nginx", "-g", "daemon off;"]
#/home/work/nginx use the host
CMD ["-c", "/home/work/nginx/conf/nginx.conf"]
