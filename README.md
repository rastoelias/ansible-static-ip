# Assigning static IP
An Ansible playbook to assign static IP address for Ubuntu server 18.04 VM.

## Requirements
* SSH Keys on the client machine.
* Ansible 2.7+ on your local machine.
* Remote machine. Tested on:
    * Ubuntu server 18.04
    * Debian stretch 9.4
* Non-root sudo user with SSH Key-Based Authentication on your remote machine.

## Usage
1. Clone this repository.
    ```
    git clone https://github.com/rastoelias/ansible-static-ip.git ansible-static-ip
    ```
2. Copy the `hosts.example` file to the `hosts` file.
    ```
    cp hosts.example hosts
    ```
3. Open the `hosts` file and replace `SERVER-IP-ADDRESS` with the public IP address of your server.
    ```
    [server]
    111.111.111.111 ansible_user=USER ansible_port=PORT
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
    or
    ```
    ansible-playbook provision.yml -b
    ```
> NOTE (Ubuntu 18.04): Playbook will fail because after the `sudo netplan apply` command your SSH connection will drop
