# deplpoy-to-docker Ansible role

Simple role for deploy app to docker by docker-compose template

### Example

playbook:

```yaml
---
- hosts: nginx
  become: yes

  roles:
    - role: deploy_to_docker
      vars:
        - dtd_project_name: "nginx_app"
        - dtd_app_root: "/var/data/nginx" # required
        - dtd_app_version: "0.0.1" # required
        - dtd_templates_folder: "template/nginx/docker-compose.yml.j2" # required
        - dtd_state: "{{ nginx_state }}"
...

```

template/nginx/docker-compose.yml.j2:

```yaml
version: "3.9"
services:
  web:
    image: nginx:stable-alpine
    ports:
      - "80:80"
```
