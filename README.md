# Example
```yaml
- hosts: <hosts>
  vars:
    postfix:
      psql:
        auth_type: dovecot
        mailbox_transport: dovecot
        certname: example.com
        hostname: mail.example.com
        destinations:
          - example.com
        psql:
          user: mail
          db: mail
          hosts:
            - unix:/var/run/postgresql/
          aliases_query: "SELECT mail FROM aliases WHERE alias = '%s'"
          boxes_query: "SELECT mail FROM users WHERE mail = '%s'" 


  roles:
    - postfix
```
