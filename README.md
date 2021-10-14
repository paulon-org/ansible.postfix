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
        ldap:
          host: "ldapi:///"
          base: "ou=passwd,dc=example,dc=com"
          boxes_query: mail=%s
          boxes_result: mail
          aliases_query: otherMailbox=%s
          aliases_result: mail
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
