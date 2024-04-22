
# Automation Setup Software in Zorin OS with Ansbile

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

- Playbook execute all task on local machine on where it run.

## How to run

**Note**

- In order to run this playbook, your system must have ansible and python.
- Playbook will install software for all user but only create desktop shorcut for current user only.
- Playbook use some apt command so you need to have sudo password to perform installation.
- [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- [Install python](https://www.python.org/downloads/)

1. Clone the repo

    ```bash
    git clone https://github.com/haryHuds0n/zorinos.ansible.git
    ```

2. Go to the repo directory

    ```bash
    cd zorinos.ansible
    ```

3. Run playbook

    ```bash
    ansible-playbook playbook.yml
    ```