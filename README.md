# Assigning static IP
An Ansible playbook to assign static IP address for Ubuntu server 18.04 VM.

## Requirements
* SSH Keys on the client machine.
* A machine with the [Ubuntu server](http://cdimage.ubuntu.com/releases/18.04.2/release/) installed.
* SSH Key-Based Authentication your server.
* Ansible 2.7+

## Usage
1. Clone this repository.
    ```
    git clone https://github.com/rastoelias/ansible-static-ip.git ubuntu-static-ip
    ```
2. Copy the `hosts.example` file to the `hosts` file.
    ```
    cp hosts.example hosts
    ```
3. Open the `hosts` file and replace `SERVER-IP-ADDRESS` with the public IP address of your server.
    ```
    [server]
    111.111.111.111
    ```
4. Copy the `config.example.yml` to the `config.yml` file.
    ```
    cp config.example.yml config.yml
    ```
5. Open the `config.yml` file, make desired changes and save changes.
6. Run playbook
    ```
    ansible-playbook provision.yml -u USER --become -K -e ansible_port=PORT
    ```

> NOTE: Playbook will fail because after the `sudo netplan apply` command your SSH connection will drop
