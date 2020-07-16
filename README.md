# MediaServer Playbook
> An ansible playbook to install a media streaming server on a Raspberry Pi.

## Getting Started

1. Install [ansible](https://www.ansible.com/) on your local machine.
2. Make sure your Raspberry Pi is reachable via SSH.
3. Run the playbook with the hosts and tags your want. (Details Below).
    ```
    ansible-playbook -i hosts  mediaserver.yml
    ```

## Configuration

### Hosts

I tend to use a simple `hosts` file with the format below

```
[rpi]
192.168.1.42 ansible_user=pi ansible_become=true
```

More details can be found in the [ansible documentation](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html)

### Tags
There are three tags you can filter in or out [details here](https://docs.ansible.com/ansible/latest/user_guide/playbooks_tags.html)

- `network`: For NAS and redundancy roles and tasks.
- `backup`: For redundancy roles and tasks.
- `media`: For media server roles and tasks.

## Components

### NAS Server
A NAS server will be installed to be able to share data over the network.

#### Redundancy
As a backup mecanimism, the data of the NAS server can be synced to another hard drive.

### Media Server
In order to use the data of the NAS server, a Plex server was installed. Once installed, you can configure it at `http://<your-ip>:32400/web/`

## eBooks Server
Since I have a great deal of ebooks, the playbook installs nginx and add a PHP application to display a Calibre library.
