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
- `minio_buckets`: A list of buckets that should be created
- `minio_policies`: A list of policies that grants users access to buckets

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
          - username: app
            password: xxx
        minio_buckets:
          - name: app
        minio_policies:
          - username: app
            bucket: app
            type: readwrite
```

## Versioning

In order to have a verioning in place and working, create leightweight tags that point to the appropriate minor release versions.

Creating a new minor release:

```bash
git tag v1
git push --tags
```

Replacing an already existing minor release:

```bash
git tag -d v1
git push origin :refs/tags/v1
git tag v1
git push --tags
```
