Role Name
=========

This is yet another certbot role for Ansible. I created it since the other
existing options didn't quite do what I wanted.

Like the other roles out there, this is useful for allowing you to install
certbot through your distribution's package manager or with pip. You can also
specify a list of domains for installation of multiple certificates.

THe main way that this role differs from the others is that a change in the
domain list for a certificate should result in a renewal with an updated list of
domains. This should make it easy to expand the list of domains handled by a
single certificate request.

Requirements
------------

This role makes use of openssl functionality, meaning it's going to want
to install the PyOpenSSL and Cryptography pip modules.

Role Variables
--------------

Please see the variable documentation in
[defaults/main.yml](https://github.com/dudefellah/ansible-role-certbot/blob/master/defaults/main.yml).

Dependencies
------------

No role dependencies exist.

Example Playbook
----------------

Installing a certificate using a pip installed certbot:

    - hosts: mygroup
      roles:
         - role: dudefellah.certbot
           certbot_pip_install: true
           certbot_certificates:
             - email: letsencrypt@myhost.com
               domains:
                 - me.myhost.com
                 - myother.myhost.com
             - email: otherme@myotherhost.com
               domains:
                 - myotherhost.com
                 - myother.myotherhost.com

License
-------

GPLv3

Author Information
------------------

Dan: https://github.com/dudefellah
