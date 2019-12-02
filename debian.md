# Debian administration

## Setting up MOTD

You can edit MOTD with `nano /etc/motd`.
[ASCII ART generator](http://patorjk.com/software/taag/#p=display&f=Big%20Money-ne&t=XD)

## Changing SSH ports
You can change ssh port and other settings in `/etc/ssh/sshd_config` file

## Adding SSH Keys

### With putty
- Generate ssh-key with putty-gen.
- Modify `~/.ssh/authorized_keys`. Copy from putty gen.
- Save private key to some location.
- In putty Connection->SSH->Auth select private key file for authentication.
- Save session. Connect. Done.

### Without putty
- ssh-keygen: `ssh-keygen -t rsa -b 4096 -f keyname -C key_comment`
- Modify `~/.ssh/authorized_keys`. Copy from `keyname.pub` (or ssh-copy-id)
- Connect to ssh `ssh -i ~/.ssh/custom_key_name SYSUSER@x.x.x.x`

## No password login for root user
In `/etc/ssh/sshd_config` file: `PermitRootLogin prohibit-password`

## SSH banner
In `/etc/ssh/sshd_config` file: `Banner /etc/ssh/banner` and paste banner content to this file

## Install some software
- [htop](https://linux.die.net/man/1/htop) `apt-get install htop`
- [docker](https://www.docker.com) `apt-get install docker`
- [curl](https://curl.haxx.se/) `apt-get install curl`

## UFW Firewall
I'm too stupid/lazy for pure iptables, so I'm using UFW.
- Installation:
`apt install ufw`
- Basic configuration:
  - `ufw default deny incoming`
  - `ufw default allow outgoing`
  - `ufw allow ssh_port comment ssh`
- List rules
`ufw status verbose`
