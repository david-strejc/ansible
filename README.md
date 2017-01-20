Tips and tricks for Ansible
===========================

* changed_when

```
- name: ensure postgresql hstore extension is created
  sudo: yes
  sudo_user: postgres
  shell: "psql my_database -c 'CREATE EXTENSION hstore;'"
  register: psql_result
  failed_when: >
    psql_result.rc != 0 and ("already exists" not in psql_result.stderr)
  changed_when: "psql_result.rc == 0"
```
