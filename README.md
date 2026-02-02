# Ansible playbook to configure VPN

## Purpose 
WireGuard-Ansible installs and configures WireGuard server. Tested on Ubuntu with Mac as a client

## Steps
- install wirequard
- create configuration file for VPN server (eg wg0.conf)
- create configuration file for client
- configure private and public keys for client und server
- start WireGuard server

## How to use it
1. On some management server clone vpn-wireguard-ansible repository
2. Update the public IP of the server in inventory.ini
3. Update network interface name and DNS in vars.yml
4. Run ansible playbook: `ansible-playbook -i inventory.ini site.yml` (with option --connection=local if you run ansible playbook on VPN server)
5. Install WireGuard on your client. Eg for Mac run: `$ brew install wireguard-tools`
6. On server find the file `/root/wg-clients/my-client.conf` and copy its content to `/etc/wireguard/wg0.conf` on your client (eg Mac)
7. Start Wiregiard on your clien `sudo wg-quick up wg0`
8. Check that your connection goes throught VPN Server (eg Mac) `traceroute -n -I 1.1.1.1` 

