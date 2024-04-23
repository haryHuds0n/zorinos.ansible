
# Setup Software in Zorin OS with Ansbile

Playbook that setup minimum software and tools required for an developer to work with.

The following software will be setup

- Vscode
- Google Chrome
- Postman
- Zulip
- Telegram

![Image](https://i.imgur.com/Aa4E14u.png)


## Reference

 - [Vscode Installation](https://code.visualstudio.com/docs/setup/linux)
 - [Google Chrome](https://support.google.com/chrome/a/answer/9025903?hl=en)
 - [Postman](https://www.postman.com/downloads/)
 - [Zulip Linux Installation](https://zulip.com/help/desktop-app-install-guide)
 - [Telegram](https://desktop.telegram.org/)


## How it run

- Playbook will loop through each workstation define in inventory file by ip address and execute task on that remote system.
- `user` in inventory file is the user developer have on remote system, e.g. `developer1`.
- `ansible_user` and `ansible_ssh_pass` is the admin user and password on that remote system, e.g. .
- For task that download and install package on system it will ask for become password to allow it, you can set in `ansible.cfg` file.
- ( Optional) If you don't want to create `ansible.cfg` file, you can save sudo token before execute playbook, this will allow ansible to run task with sudo without issue.

## How to run

**Note**

- In order to run this playbook, system must have ansible and python
- [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- [Install python](https://www.python.org/downloads/)

1. Clone the repo

    ```bash
    git clone https://github.com/haryHuds0n/zorinos.ansible.git
    ```

2. Checkout to `dynamic` branch

    ```bash
    cd zorinos.ansible
    git checkout dynamic
    ```

3. Edit `inventory` file

    Replace `ansible_user`, `ansible_ssh_pass` and `user` with your correct user and password.

    If you are using ssh key you can replace `private_key_file` and `remote_user` in `ansible.cfg` with correct user and path to private key.

    Example inventory file:
    ```powershell
    [workstation]
    192.168.3.50 ansible_user=sysadmin ansible_ssh_pass=password user=dev1
    192.168.3.51 ansible_user=sysadmin ansible_ssh_pass=password user=dev2
    ```

4.  ( Optional ). If you prefer using config file, then run this command to generate ansible config file.

    ```bash
    mkdir /etc/ansible
    ansible-config init --disabled > /etc/ansible/ansible.cfg
    ```

5. Run playbook

    ```bash
    ansible-playbook playbook.yml -i inventory -K
    ```