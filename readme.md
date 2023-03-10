# Ansible MinIO Role

MinIO installation role.

## Role Variables

- `minio_api_scheme`: The scheme that should be used to access the API with the client after setup
- `minio_api_address`: The IP address that the server should bind for the API
- `minio_api_port`: The port that the server should bind for the API
- `minio_console_address`: The IP address that the server should bind for the console
- `minio_console_port`: The port that the server should bind for the console
- `minio_root_user`: The username of the root user
- `minio_root_password`: The password of the root user
- `minio_users`: A list of users that should get access to the server

## Example Playbook

```yaml
- hosts: all
  tasks:
    - ansible.builtin.include_role:
        name: ansible-minio
      vars:
        minio_api_scheme: http
        minio_api_address: 127.0.0.1
        minio_api_port: 9000
        minio_console_address: 127.0.0.1
        minio_console_port: 9001
        minio_root_user: minio
        minio_root_password: xxx
        minio_users:
          - access_key: app
            secret_key: xxx
```

## Versioning

In order to have a verioning in place and working, create leightweight tags that point to the appropriate minor release versions.

Creating a new minor release:

```bash
git tag 1.0
git push --tags
```

Replacing an already existing minor release:

```bash
git tag -d 1.0
git push origin :refs/tags/1.0
git tag 1.0
git push --tags
```
