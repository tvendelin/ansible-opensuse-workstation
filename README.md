# OpenSUSE Leap 15 Workstation Setup with Ansible

An Ansible playbook for configuring a multimedia workstation to my preferences. This is merely an
'umbrella' for several Ansible roles which are developed separately and are included as Git
submodules.

## Hardware

The NVIDIA GeForce 20-series GPU is assumed. For anything different, disable `nvidia` role and,
optionally, add something else.

## Usage

Install OpenSUSE with Gnome and Multimedia enabled.

```
# become root
su -

# Install git
zypper in --no-recommends -y git

# Upgrade pip
pip install -U pip

# Install Ansible with pip
pip install ansible
```

Close and re-open terminal so that `bash` picks the `git` completions. 

If you want to install Davinci Resolve to edit your videos, go to their site, download the
installer, make it executable, and run it as a regular user. Don't launch it, as it won't
work - yet.

Clone this repository with submodules, and run Ansible.

```
git clone --recurse-submodules https://github.com/tvendelin/ansible-opensuse-workstation.git
workstation

cd workstation/

ansible-playbook workstation.yml -K
```

Reboot.

If you prefer to run Ansible remotely, on the target machine:
- open SSH port
- enable and start `sshd`

