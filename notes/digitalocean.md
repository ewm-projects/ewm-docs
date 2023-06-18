# General notes for using DigitalOcean Droplets

## Setup
_todo_

## Github Action Deploy

_source: [danieltorscho gist](https://gist.github.com/danieltorscho/c104c23e97c840f09fd9a186ec092b28)_

**Setup user in droplet**
- `adduser deployer`
- `usermod -aG sudo deployer`
- `exit`

**Setup SSH for droplet & github**
- `ssh deployer@DROPLET_IP`
  - Obtain droplet ip address from your digital ocean droplet dashboard
- `ssh-keygen`
- `ssh-keyscan -t rsa github.com >> ~/.ssh/known_hosts`
- `cat ~/.ssh/id_rsa.pub`
  - Copy the output starting from `ssh-rsa`
  - Go to [Github SSH settings](https://github.com/settings/ssh/new)
  - Paste the id_rsa contents
- `cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys`
- `cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys2`
- `chmod 700 ~/.ssh/authorized_keys && chmod 640 ~/.ssh/authorized_keys2`
- Go to your repository > settings > security > secrets and variables > actions
  - In Secrets tab, add secrets:
    - name: `HOST`, value: `YOUR_DROPLET_IP_ADDRESS`
    - name: `USERNAME`, value: `deployer`
    - name: `KEY`, value: `DEPLOYER_SSH_PRIVATE_KEY`
      - copy from `cat ~/.ssh/id_rsa`
      - Include the "BEGIN OPENSSH" and "END OPENSSH" comments as well



## Misc

**Update server**
- `sudo apt update`
- `sudo apt upgrade`
- `sudo reboot`

## Resources
- [Initial server setup](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-20-04)
- [Step by step guide for digital ocean deployment](https://gist.github.com/danieltorscho/c104c23e97c840f09fd9a186ec092b28)
