Just forward DNS requests to the stack, as I don't think there is much point having a VPN for https based requests. Unless I am protecting a private server.

# pi-hole
Pi Hole repository


Use docker composer file from here:
https://github.com/pi-hole/docker-pi-hole/#running-pi-hole-docker


Cloudflare DNS over TLS server repo:
https://github.com/qdm12/cloudflare-dns-server
https://hub.docker.com/r/qmcgaw/cloudflare-dns-server

### openvpn
https://github.com/kylemanna/docker-openvpn/blob/master/docs/docker-compose.md


https://www.reddit.com/r/pihole/comments/5z0slc/is_it_possible_to_setup_a_vpn_that_only_tunnels/

Trying not to send all traffic through the VPN
https://forum.netgate.com/topic/133346/force-redirection-of-dns-for-openvpn-traffic
https://forums.openvpn.net/viewtopic.php?f=6&t=27618


Setup
```bash
PI_HOLE_IP=0.0.0.0
# VPN.SERVERNAME.COM can just be an ip address
docker-compose run --rm openvpn ovpn_genconfig -n $PI_HOLE_IP -u udp://VPN.SERVERNAME.COM
docker-compose run --rm openvpn ovpn_initpki
sudo chown -R $(whoami): ./openvpn-data
```
Setup Client
```bash
export CLIENTNAME="jordan_laptop"
# with a passphrase (recommended)
docker-compose run --rm openvpn easyrsa build-client-full $CLIENTNAME
```

https://www.digitalocean.com/community/tutorials/how-to-run-openvpn-in-a-docker-container-on-ubuntu-14-04?utm_source=githubreadme

To be the ip of the pi-hole. Just use the pi-hole server.
https://docs.pi-hole.net/guides/vpn/setup-openvpn-server/

Only route DNS traffic over vpn
https://docs.pi-hole.net/guides/vpn/only-dns-via-vpn/

docker run --name cloudflared --rm --net host \
 -e DNS1=#.#.#.# -e DNS2=#.#.#.# visibilityspots/cloudflared

### dns-over-https


