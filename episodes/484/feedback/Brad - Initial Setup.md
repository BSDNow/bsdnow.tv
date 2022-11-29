Hey JT and Benedict and Allan and Tom (and any et. al I may have missed),

Tom and Benedict were asking for initial steps we take when setting up a new machine, so I thought I would include mine. Please consider this a work in progress... I have been mostly setting up jails recently, and with Benedict's help, I have put a lot of it into Ansible playbooks. So part 1 if my steps are to spin up the jail (which can be ignored if it is a hardware host).

Part I: On the host machine's console
Create the jail and log in to the console.
        host# IOCHOST=test1 ; iocage create -r 13.1-RELEASE set ip4_addr="192.168.1.125/24" -p /usr/iocage/pkgs.json -n $IOCHOST boot=on

-p points to a file with packages to install during creation of the jail. The file looks like:
      {
           "pkgs": [
           "python39",
           "sudo",
           "rsync",
           "vim",
           "bash",
           "tmux",
           "node-exporter"
           ]
       }

log into the iocage console on the jail host.
     host# iocage console

Part II: Configuration from the console
In the console, we have to set up the groundwork for ansible.
Install a few necessary packages:
python39
sudo
rsync
vim
bash
tmux
node-exporter (I will probably be setting up prometheus or grafana later.
This list is the same as the one in section 1, in case the host being provisioned is not an iocage jail (e.g. a hardware node). In addition to the packages above, on a hardware node, I also install smartmontools, zfstools, ntp.
Create the ansible user and set it up in sudoers.
Enable sshd on the host
First, get rid of weaker (< 3071 bits) prime numbers in /etc/sshd/moduli:
  IOCAGE_CONSOLE# awk '$5 >= 3071' /etc/ssh/moduli > /etc/ssh/moduli.safe 
  IOCAGE_CONSOLE# mv /etc/ssh/moduli.safe /etc/ssh/moduli

Delete any existing keys, and then set up only good keys, generate keys, and start ssh.
  IOCAGE_CONSOLE# rm /etc/ssh/ssh_host_*
  IOCAGE_CONSOLE# sysrc sshd_dsa_enable=NO
  sshd_dsa_enable: -> NO
  IOCAGE_CONSOLE# sysrc sshd_ecdsa_enable=NO
  sshd_ecdsa_enable: -> NO
  IOCAGE_CONSOLE# sysrc sshd_ed25519_enable=YES
  sshd_ed25519_enable: -> YES
  IOCAGE_CONSOLE# sysrc sshd_rsa_enable=YES
  sshd_rsa_enable: -> YES
  IOCAGE_CONSOLE# sysrc sshd_enable=YES
  sshd_enable: NO -> YES
  IOCAGE_CONSOLE# service sshd start
  Generating RSA host key.
  3072 SHA256:GXW965WdFk4cIX3PlM52DREMzMz4SBBGB0Lqm0zmh+8 root@test1 (RSA)
  Generating ECDSA host key.
  256 SHA256:44H7iV/8pn69jlJK2QjqJGhpWcTnNohjfKkKB4USDAk root@test1 (ECDSA)
  Generating ED25519 host key.
  256 SHA256:xczxmBcDBI7ikvCHUax/CumuaqvjA5mxJXHfhlZai5w root@test1 (ED25519)
  Performing sanity check on sshd configuration.
  Starting sshd.

Part III: From the ansible host (worf)
This is where we finally get to run the playbooks.
push the ansible ssh key to the new server
 [ansible@worf ~]$ ssh-copy-id -i .ssh/ansible.pub test1
 [ansible@worf ~]$ ansible-playbook playbooks/provision.yaml -e "host=test1"
 [ansible@worf ~]$ ansible-playbook playbooks/usersetup.yaml -e "host=test1"
 [ansible@worf ~]$ ansible-playbook playbooks/sshsetup.yaml -e "host=test1"
 [ansible@worf ~]$ ansible-playbook playbooks/periodic.yaml -e "host=test1"

provision.yaml
Installs remaining core packages (vim, rsync, tmux) and sets up backuppc service account and user account for storm.
usersetup.yaml
installs /usr/local/etc/bashprompt, which sets prompt colors for bash prompts)
configure root's .login to launch bash on login (without changing root's shell to bash)
adds the following lines to /root/.bashrc, and .profiles for ansible, backuppc and storm users.
sshsetup.yaml
Set up ssh_config to allow key-based root login
Set up authorized_keys for root, storm, and backuppc
periodic.yaml
sets up /etc/peroidic.conf

Let me know what you think...I'll send updates as they occur to me...
--b
