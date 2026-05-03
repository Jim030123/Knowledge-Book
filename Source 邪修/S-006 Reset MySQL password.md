- Need PowerShell administrator.

```bash
net stop mysql80
```


```bash
cd "C:\Program Files\MySQL\MySQL Server 8.0\bin"
```

- Initialize the file
```bash
cd "C:\Program Files\MySQL\MySQL Server 8.0\bin"
.\mysqld --initialize --datadir="C:\ProgramData\MySQL\MySQL Server 8.0\Data4408"

```

- The ***.err*** file contains the new password. 
- Connection
```bash
.\mysqld --datadir="C:\ProgramData\MySQL\MySQL Server 8.0\Data4406" --port=4408

```

- 