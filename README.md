This ansible playbook is created to spin up FreeIPA and Keycloak Servers on CentOS 8. 

Note: this installation is just a basic installation designed to get familar with FreeIPA. Security hardening of the base CentOS server is left for your organization, as organizations' security requirements differ. However, feel free to message me and I will try to guide you through.

The following requirements are needed to run this playbook:

* 2 CentOS 8 Server (2 cores, 4 GB RAM is the extreme minimum)
* Set the IP address to 192.168.50.50 for FreeIPA and 192.168.50.51 for keycloak. You can change the IP address and the login user in the hosts file.
* Python3

Instructions:
Once you have configured your CentOS server you can run the following commands to install a base installation of FreeIPA. 

```sh
$ git clone https://github.com/salimwp/freeipa-ansible
$ cd freeipa-ansible
$ python3 -m venv .
$ source bin/activate
$ pip3 install -r requirements.txt
$ ansible-playbook -i hosts -k -K ipa.yaml
```

You should set your DNS of the computer you are using to the matching IP address of FreeIPA since it is running a DNS server. Go to https://ipa01.dc1.example.org. You can change this name in the freeipa tasks. We will be using Ansible vars in the next version to fix this. We also have the FreeIPA packages installing via command line rather than DNF ansible module as at the time it wasn't working correctly.