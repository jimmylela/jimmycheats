

#os version #distro #distribution
    cat /etc/*release

#SSH #SSH server

Xubuntu 20.04 fresh install 

## Install SSH server
$ sudo apt update
$ sudo apt install openssh-server

## Back up original config file and write protect it
$ sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak.orig.YYYYMMDD
$ sudo chmod a-w /etc/ssh/sshd_config.bak.orig.

## Modify config file as desired
$ vi /etc/ssh/sshd_config

#Port <<desired_port_number>>


## Check config file for errors before restarting service (especially if SSH is the only method of remote management!)
$ sudo sshd -t -f /etc/ssh/sshd_config
