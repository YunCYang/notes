# Server

## EC2

IPv4 Public IP: 18.144.81.193

Download and keep the security key-pair document safe.

### Use Git Bash

For Linux or macOS, do `chmod 600 ~/[key-pair file location]` to change the safety mode.

run `ssh -i ~/Desktop/ec2-ssh.pem ubuntu@18.144.81.193`
`~/...` is the file location of the key-pair file
`ubuntu@18.144.81.193` ubuntu is the user name, or the type of service you launched.
18.144.81.193 is the IPv4 Public IP.

```
The authenticity of host '18.144.81.193 (18.144.81.193)' can't be established.
```

Run `yes` if this is the first time running the machine.

`sudo apt update` raise user to root in order to install tools. Update lists of available packages on the virtual machine. `apt` is a package manager.

`sudo apt upgrade` upgrade the available packages.
`[Y/n]` capitalized Y means default, can just press enter in order to select it.

On the colorful package configuration screen, select
`install the package maintainer's version`. Only for the first time.

`sudo reboot` to reboot and make sure all the packages are installed. The connection will be closed.

connect using the same command.

Install using `sudo apt -y install <name>` -y is optional
nodejs, npm, httpie, postgresql, nginx (a proxy)

proxy - prebuilt webserver for public, so public doesn't have to connect to node, which is inefficient.

use `top` to check which service is running. `q` to exit.

### Elastic IP

Get a stable public IP address for the public. One free for all.
Elastic IP address: `184.169.194.166`
Associate the address with the instance.

### Log

Clone the git repo for portfolio example to yuncyang.com
`git clone <git repo address> yuncyang.com`

Copy the nginx config file
`sudo cp /etc/nginx/sites-available/default /etc/nginx/sites-available/yuncyang.com`
cp stands for copy

Use nano to edit the file
`sudo nano /etc/nginx/sites-available/yuncyang.com`

Inside nano:

- Change root: `root /home/ubuntu/yuncyang.com;`
- Change server name to domain name `server_name yuncyang.com;`
- ctrl O, enter to save, ctrl X to exit nano

Remove the default config file in sites-enabled (not sites-available!)
`sudo rm /etc/nginx/sites-enabled/default`

Enable the customed configuration file.
`sudo ln -s /etc/nginx/sites-available/yuncyang.com /etc/nginx/sites-enabled/yuncyang.com`

Reboot nginx
`sudo service nginx restart`

Install certbot for https
Go to certbot website for detail example
`sudo add-apt-repository ppa:certbot/certbot`
`sudo apt-get install certbot python-certbot-nginx`

[Back](../../README.md)

--
note:
Old config that wasn't working:

located at ` /etc/nginx/sites-available/yuncyang.com`

```
server {
    if ($host = yuncyang.com) {
        return 301 https://$host$request_uri;
    } # managed by Certbot


        listen 80;
        listen [::]:80;

        server_name yuncyang.com;
        return 404; # managed by Certbot


}
```

Above config always return 404 when visits http://yuncyang.com , instead of redirecting to https version.
