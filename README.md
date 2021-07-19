## Server Setup

1. [Initial Server Setup with Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-18-04)
2. [How To Set Up a Firewall with UFW on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-18-04)
3. [How To Harden OpenSSH on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-harden-openssh-on-ubuntu-18-04)
4. [How To Install Node.js on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-18-04)
5. [How To Set Up a Node.js Application for Production on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-ubuntu-18-04)

### Server Additional Reading

- [How to Set Up SSH Keys on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-1804)
- [Systemd Essentials: Working with Services, Units, and the Journal](https://www.digitalocean.com/community/tutorials/systemd-essentials-working-with-services-units-and-the-journal)

## Server Maintenance

- [How To View and Configure Linux Logs on Ubuntu and Centos](https://www.digitalocean.com/community/tutorials/how-to-view-and-configure-linux-logs-on-ubuntu-and-centos)

## Caddy

### Setup

1. [How To Install Go and Set Up a Local Programming Environment on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-install-go-and-set-up-a-local-programming-environment-on-ubuntu-18-04)
2. [How To Host a Website with Caddy on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-host-a-website-with-caddy-on-ubuntu-18-04)
3. [Cloudflare module for Caddy](https://github.com/caddy-dns/cloudflare)

### Caddyfile

```
example.com, www.example.com {
    reverse_proxy 127.0.0.1:3000
    encode gzip

    log {
        output stderr
        format console
        level PANIC
    }

    tls {
        dns cloudflare {env.CF_API_TOKEN}
    }
}
```

The CF_API_TOKEN is located in the /etc/systemd/system/caddy.service

```
...
[Service]
User=caddy
Group=caddy
Environment=CF_API_TOKEN=your_token_here
ExecStart=/usr/bin/caddy run --environ --config /etc/caddy/Caddyfile
ExecReload=/usr/bin/caddy reload --config /etc/caddy/Caddyfile
TimeoutStopSec=5s
LimitNOFILE=1048576
LimitNPROC=512
PrivateTmp=true
ProtectSystem=full
AmbientCapabilities=CAP_NET_BIND_SERVICE
...
```

## VSCode Remote

- [sucode](https://github.com/microsoft/vscode/issues/48659#issuecomment-825328802)
- [copy](https://github.com/microsoft/vscode/issues/48659#issuecomment-871085291)
