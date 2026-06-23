# cic-ansible
Ansible playbooks for RWU's Cybersecurity and Intel Club.

# Variables
All custom variables are registered through the template local_`(file #, e.g. [001]-bootstrap.yaml)`_`(command name/context)`
For example, in [002-updates.yaml](roles/common/002-updates.yaml):
```diff
\- name: Enable unattended upgrades and periodic cache updates
    ansible.builtin.copy:
    dest: /etc/apt/apt.conf.d/20auto-upgrades
    content: |
        APT::Periodic::Update-Package-Lists "1";
        APT::Periodic::Unattended-Upgrade "1";
    owner: root
    group: root
    mode: "0644"
+   register: common_002_update20autoupgrades
```
At the very least, registered variables should track the file number they came from, to make debugging easier.