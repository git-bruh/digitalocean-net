# digitalocean-net

Sets up the static network configuration based on the [DigitalOcean metadata file](https://docs.digitalocean.com/reference/api/metadata-api/#operation/getMetadata) without a `/etc/network/interfaces` file and `ifup`

# Usage

```sh
# /dev/vdb is mounted at /mnt
./donet /mnt/digitalocean_meta_data.json
```

```sh
# Just print out the operations that would be performed
# Redirect stderr to hide debug logs
$ ./donet -d /mnt/digitalocean_meta_data.json 2>/dev/null
ip link set eth0 up
ip address add 139.59.2.174/20 broadcast + dev eth0
ip route add default via 139.59.0.1 dev eth0
ip link set eth1 up
ip address add 10.122.0.2/20 broadcast + dev eth1
ip route add default via 10.122.0.1 dev eth1
nameserver 67.207.67.2
nameserver 67.207.67.3
```
