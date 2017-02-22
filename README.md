# hello-vagrant-and-ansible_local
Vagrant x ansible_local Example

# About
vagrantとansible_localを利用して、環境のプロビジョニングを行うサンプルです。  
Windows環境ではansibleが利用できない問題がありましたが、  
ansible_localによって、プロビジョニングする環境上にansibleをインストールして利用できるようになりました。  
  
このサンプルでは、ansibleの利用例としてgitとvimをインストールしています。

# Usage

```bash
$ git clone https://github.com/DaisukeOtaka/hello-vagrant-and-ansible_local.git
$ cd hello-vagrant-and-ansible_local
$ vagrant up
$ vagrant ssh
```

```bash
$ which git
$ which vim
```

# Example

```
$ vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Importing base box 'centos/7'...
==> default: Matching MAC address for NAT networking...
==> default: Checking if box 'centos/7' is up to date...
==> default: Setting the name of the VM: hello-vagrant-and-ansible_local_default_1487753899743_88257
==> default: Fixed port collision for 22 => 2222. Now on port 2202.
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 22 (guest) => 2202 (host) (adapter 1)
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2202
    default: SSH username: vagrant
    default: SSH auth method: private key
    default:
    default: Vagrant insecure key detected. Vagrant will automatically replace
    default: this with a newly generated keypair for better security.
    default:
    default: Inserting generated public key within guest...
    default: Removing insecure key from the guest if it's present...
    default: Key inserted! Disconnecting and reconnecting using new SSH key...
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
    default: No guest additions were detected on the base box for this VM! Guest
    default: additions are required for forwarded ports, shared folders, host only
    default: networking, and more. If SSH fails on this machine, please install
    default: the guest additions and repackage the box to continue.
    default:
    default: This is not an error message; everything may continue to work properly,
    default: in which case you may ignore this message.
==> default: Rsyncing folder: /c/opt/vagrant/machines/hello-vagrant-and-ansible_local/ => /vagrant
==> default: Running provisioner: ansible_local...
    default: Installing Ansible...
    default: Running ansible-playbook...
cd /vagrant && PYTHONUNBUFFERED=1 ANSIBLE_NOCOLOR=true ansible-playbook --limit="all" --inventory-file=hosts -v provision_vagrant.yml
Using /etc/ansible/ansible.cfg as config file

PLAY [vagrant] *****************************************************************

TASK [setup] *******************************************************************
ok: [127.0.0.1]

TASK [install git] *************************************************************
...
TASK [install vim] *************************************************************
...
PLAY RECAP *********************************************************************
127.0.0.1                  : ok=3    changed=2    unreachable=0    failed=0


$ vagrant ssh
[vagrant@localhost ~]$ which git
/usr/bin/git
[vagrant@localhost ~]$ which vim
/usr/bin/vim
```
