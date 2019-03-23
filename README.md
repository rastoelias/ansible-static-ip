# Assigning static IP
An Ansible playbook to assign static IP address on remote server.
> Tested on: Ubuntu server 18.04, Debian stretch 9.4

## Local machine requirements
* SSH Keys
* Ansible 2.7+

## Remote server requirements
* IP address of the remote server
* sudo user with SSH Key-based and passwordless authentication.
    > see: https://github.com/rastoelias/create-ansible-user

## Usage
1. Clone this repository.
    ```
    git clone https://github.com/rastoelias/ansible-static-ip.git ansible-static-ip
    ```
2. Copy the `hosts.example` file to the `hosts` file.
    ```
    cp hosts.example hosts
    ```
3. Open the `hosts` file, make desired changes and save changes.
    ```
    [server]
    111.111.111.111

    [server:vars]
    ansible_user=ansible
    ansible_port=22
    ansible_python_interpreter=/usr/bin/python3
    ```
4. Copy the `config.example.yml` to the `config.yml` file.
    ```
    cp config.example.yml config.yml
    ```
5. Open the `config.yml` file, make desired changes and save changes.
6. Test the connection.
    ```
    ansible all -m ping
    ```
6. Run playbook
    ```
    ansible-playbook provision.yml
    ```
> NOTE (Ubuntu 18.04): Playbook will fail because after the `sudo netplan apply` command your SSH connection will drop
