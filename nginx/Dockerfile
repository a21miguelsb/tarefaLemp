FROM debian:latest

RUN apt update && apt install -y curl gnupg2 ca-certificates lsb-release debian-archive-keyring

RUN curl https://nginx.org/keys/nginx_signing.key | gpg --dearmor   \
    | sudo tee /usr/share/keyrings/nginx-archive-keyring.gpg >/dev/null

RUN echo "deb [signed-by=/usr/share/keyrings/nginx-archive-keyring.gpg] \
    http://nginx.org/packages/ubuntu `lsb_release -cs` nginx" \
    | sudo tee /etc/apt/sources.list.d/nginx.list

RUN apt update && apt install nginx

RUN apt instll -y php fpm

EXPOSE 80

CMD ["/usr/sbin/nginx","-g","daemon off;"]