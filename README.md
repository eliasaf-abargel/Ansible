# Ansible

install Ansible on a CentOS 9 

1 - sudo dnf update

```bash
sudo dnf update
```

2 - Enable the EPEL Repository

```bash
sudo dnf install epel-release
```

3 - Install Ansible


```bash
sudo dnf install ansible
```

4 - Verify the Installation

```bash
ansible --version
```


5 - Basic Configuration (Optional)

  ```bash
  ssh-keygen
  ```

- Copy the public key to the managed nodes:

  ```bash
  ssh-copy-id user@remote_host
  ```

  Replace `user` with the remote username and `remote_host` with the remote server's IP address or hostname.

- Test Ansible's ability to connect to the managed nodes:

  ```bash
  ansible all -m ping -u user -i /path/to/inventory
  ```

  Replace `/path/to/inventory` with the path to your Ansible inventory file.

6 - Configure Ansible (Optional)
- You may want to configure Ansible according to your needs. Ansible's configuration can be done in the `/etc/ansible/ansible.cfg` file, and you can define your hosts in the `/etc/ansible/hosts` file.

### For server win you have open service Windows Remote Management

Setting up Windows nodes for Ansible is a bit more involved since Ansible uses WinRM (Windows Remote Management) instead of SSH for Windows.

Run this script on your Windows nodes as an administrator. It will configure WinRM with sensible defaults that work well with Ansible.

PowerShell script provided by Ansibl 

$url = "https://raw.githubusercontent.com/ansible/ansible/devel/examples/scripts/ConfigureRemotingForAnsible.ps1"
$file = "$env:temp\ConfigureRemotingForAnsible.ps1"
(New-Object -TypeName System.Net.WebClient).DownloadFile($url, $file)
powershell.exe -ExecutionPolicy ByPass -File $file



