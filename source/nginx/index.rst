======
Todo
======

.. contents:: :local:

Config
------

vhost::

        server {

        listen 80;
        access_log /var/log/nginx/plonegov.local.access.log;
        error_log /var/log/nginx/plonegov.local.error.log;

        # Note that domain name spelling in VirtualHostBase URL matters
        # -> this is what Plone sees as the "real" HTTP request URL.
        # "Plone" in the URL is your site id (case sensitive)
        location / {
            rewrite ^(.*)$ /VirtualHostBase/http/$http_host:80/Plone/VirtualHostRoot$1 break;
            proxy_pass   http://127.0.0.1:8080;
            proxy_set_header  X-Real-IP  $remote_addr;
}
}

more soon ...

