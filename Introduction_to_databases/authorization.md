## Authorization

### Users
```sql
CREATE USER
GRANT ... ON ... TO ...

GRANT SELECT, INSERT, UPDATE ON *.* TO u1
```

- `*.*`  is `db_name.tbl_name`

### Roles

```sql
CREATE ROLE someRole
GRANT someRole TO someOne
GRANT somePrivilege to someRole
```

