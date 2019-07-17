FROM ubuntu:latest

WORKDIR /tmp
RUN apt-get update && \
    apt-get install curl -y
RUN curl https://bin.equinox.io/c/VdrWdbjqyF/cloudflared-stable-linux-amd64.deb -o cloudflared-stable-linux-amd64.deb
RUN dpkg -i cloudflared-stable-linux-amd64.deb
#sudo apt-get install -f
## instructions here
# just use the default options
CMD cloudflared proxy-dns
#RUN mkdir -p /usr/local/etc/cloudflared
#RUN cat << EOF > /usr/local/etc/cloudflared/config.yml
#proxy-dns: true
#proxy-dns-upstream:
# - https://1.1.1.1/dns-query
# - https://1.0.0.1/dns-query
#EOF
#
#RUN sudo cloudflared service install

# would like to use standalone binary... https://bin.equinox.io/c/VdrWdbjqyF/cloudflared-stable-linux-amd64.tgz
