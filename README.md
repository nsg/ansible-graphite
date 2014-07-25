nsg.graphite
========

This role installs graphite, I choose to install graphite from pip because the packages in the distributions repositories are old and features are missing. I’m using apt/yum when possible.

Requirements
------------

As usual, read the tasks and make sure this role will not breaks your installation, I will for example mess with django, twisted and uwsgi.

This role exposes the graphite web interface with uwsgi at `localhost:3031`, you need to configure a web server your self to talk to that. For example, do this with nginx:

```
server {
  listen 8080;
  charset utf-8;
  access_log /var/log/nginx/graphite.access.log;
  error_log /var/log/nginx/graphite.error.log;

  location / {
  include uwsgi_params;
  uwsgi_pass 127.0.0.1:3031;
  }
}
```

Role Variables
--------------


Example Playbook
-------------------------

```
    - hosts: servers
      roles:
         - { role: nsg.graphite, graphite_secret_key: 'dgdgdfgasg' }
```

... or place graphite_secret_key in group_vars, host_vars, inventory...

License
-------

MIT

Author Information
------------------

Stefan Berggren, nsg@nsg.cc
