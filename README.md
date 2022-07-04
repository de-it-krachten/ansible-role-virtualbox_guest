[![CI](https://github.com/de-it-krachten/ansible-role-virtualbox_guest/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-virtualbox_guest/actions?query=workflow%3ACI)


# ansible-role-virtualbox_guest

Compiles Virtualbox guest additions from source

## Platforms

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- CentOS 7
- RockyLinux 8
- OracleLinux 8
- AlmaLinux 8
- AlmaLinux 9
- Debian 10 (Buster)
- Debian 11 (Bullseye)
- Ubuntu 18.04 LTS
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Fedora 35
- Fedora 36

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
virtualbox_guest_obsolete_packages:
    - virtualbox-guest-x11
    - virtualbox-guest-additions
    - virtualbox-guest-dkms

force_virtbox_guest: False
skip_reboot: False

virtbox_iso: /usr/share/virtualbox/VBoxGuestAdditions.iso
virtbox_method: iso
</pre></code>

### vars/Fedora.yml
<pre><code>
# List of packages needed for compilation
virtualbox_guest_packages:
  - gcc
  - kernel-devel
  - kernel-headers
  - dkms
  - make
  - bzip2
  - perl
  - libxcrypt-compat
  - p7zip
  - p7zip-plugins
</pre></code>

### vars/family-RedHat.yml
<pre><code>
# List of packages needed for compilation
virtualbox_guest_packages:
  - gcc
  - kernel-devel
  - kernel-headers
  - dkms
  - make
  - bzip2
  - perl
  - p7zip
  - p7zip-plugins
</pre></code>

### vars/Ubuntu.yml
<pre><code>
# List of packages needed for compilation
virtualbox_guest_packages:
  - build-essential
  - dkms
  # - linux-headers-{{ ansible_kernel }}
  - linux-headers-generic
  - p7zip-full
</pre></code>

### vars/family-Debian.yml
<pre><code>
# List of packages needed for compilation
virtualbox_guest_packages:
  - build-essential
  - dkms
  # - linux-headers-{{ ansible_kernel }}
  - linux-headers-amd64
  - p7zip-full
</pre></code>



## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'virtualbox_guest'
  hosts: all
  vars:
  tasks:
    - name: Include role 'virtualbox_guest'
      include_role:
        name: virtualbox_guest
</pre></code>
