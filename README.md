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
        - project_name: "nginx_app"
        - app_root: "/var/data/nginx" # required
        - app_version: "0.0.1" # required
        - templates_folder: "template/nginx/docker-compose.yml.j2" # required
        - state: "{{ nginx_state }}"
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
