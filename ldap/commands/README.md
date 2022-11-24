## LDAPSearch

### TLS with port 389

```bash
ldapsearch -H ldap://ldap.jumpcloud.com:389 -ZZ -x -b "ou=Users,o=YOUR_ORG_ID,dc=jumpcloud,dc=com" -D "uid=LDAP_BINDING_USER,ou=Users,o=YOUR_ORG_ID,dc=jumpcloud,dc=com" -W "(objectClass=inetOrgPerson)"
```

### LDAPS with port 636

```bash
ldapsearch -H ldaps://ldap.jumpcloud.com:636 -x -b "ou=Users,o=YOUR_ORG_ID,dc=jumpcloud,dc=com" -D "uid=LDAP_BINDING_USER,ou=Users,o=YOUR_ORG_ID,dc=jumpcloud,dc=com" -W "(objectClass=inetOrgPerson)"
```
