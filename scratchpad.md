```
---
- pause:
      prompt: "Sudo password for localhost "
  when: ( env == 'local' ) and
      ( inventory_hostname == "localhost" ) and
      ( hostvars["localhost"]["ansible_become_password"] is not defined )
  register: sudo_password
  no_log: true
  tags:
       - always

```