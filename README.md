# Ansible Role: Creates Cloudfront Buckets

Creates one or more Cloudfront distributions and configures them using a default json template.

## Installation

``` bash
$ ansible-galaxy install https://github.com/crushlovely/ansible-s3.git
```
## Variables

You will want to fill all these in before running the role.

``` yaml
app_name: test
server_env: qa
access_key: ""
secret_key: ""
asset_vars:
  - bucket_name: "{{ app_name }}-{{ server_env }}"
    caller_reference: 1
  - bucket_name: "{{ app_name }}-assets-{{ server_env }}"
    caller_reference: 2
```
You can also add a vars folder to your project folder and have your variables served by adding them to a file and calling it in your playbook.

```yaml
- hosts: localhost
...
  vars_files:
    - vars/default_vars.yml
...
```
## Usage

Once this role is installed on your system, include it in the roles list of your playbook.

``` yaml
- hosts: localhost
  connection: local
  gather_facts: True
  roles:
    - ansible-cloudfront
```

## Dependencies

None

## License

MIT