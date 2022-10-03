Ansible role: Apache
====================

Install apache2 and configure both HTTP and HTTPS virtual hosts.

Role Variables
--------------

```
ENTRY POINT: main - Install and configure apache2

        Install apache2 and configure both HTTP and HTTPS virtual
        hosts.

OPTIONS (= is mandatory):

- apache_allow_override
        Default allow_override settings for all vhosts
        [Default: All]
        type: str

- apache_conf_templates
        Template files for additional configuration under conf-enabled
        Builtin templates available:
          * conf/ldap.conf
          * conf/letsencrypt.conf
        [Default: (null)]
        elements: str
        type: list

- apache_default_http_listenon
        Default HTTP listen addresses and ports
        [Default: ['*:80']]
        elements: str
        type: list

- apache_default_https_listenon
        Default HTTPS listen addresses and ports
        [Default: ['*:443']]
        elements: str
        type: list

- apache_default_loglevel
        Default log level for all vhosts
        [Default: warn]
        type: str

- apache_default_mods_disabled
        Default apache2 mods to disable
        [Default: (null)]
        elements: str
        type: list

- apache_default_mods_enabled
        Default apache2 mods to enable
        [Default: ['ssl']]
        elements: str
        type: list

- apache_default_vhost_options
        Default vhost options set across all vhosts
        [Default: (null)]
        type: str

- apache_extra_pkgs
        Extra apache2 packages
        [Default: (null)]
        elements: str
        type: list

- apache_honor_cipher_order
        If true, prefer the server's cipher preference order
        [Default: False]
        type: bool

- apache_ignore_missing_ssl_certificate
        Create HTTPS vhosts even when SSL certificates are missing
        [Default: True]
        type: bool

- apache_log_dirs
        Log directories created under /var/log/apache2/
        [Default: (null)]
        elements: dict
        type: list

        OPTIONS:

        = dir
            Name of the directory

            type: str

        - group
            Group assigned to the directory
            [Default: adm]
            type: str

        - mode
            Mode of the directory
            [Default: u=rwx,g=rx,o=]
            type: str

        - owner
            Owner of the directory
            [Default: root]
            type: str

- apache_logrotate_config
        Logrotate configuration for apache
        [Default: (null)]
        elements: dict
        type: list

        OPTIONS:

        = logs
            Fileglob for files under /var/log/apache2/

            type: str

        - options
            Logrotate options (overrides options in
            apache_logrotate_default_options)
            [Default: (null)]
            type: dict

        - scripts
            Logrotate scripts (overrides scripts in
            apache_logrotate_default_scripts)
            [Default: (null)]
            type: dict

- apache_logrotate_default_options
        Default options for logrotate configuration
        [Default: (null)]
        type: dict

- apache_logrotate_default_scripts
        Default scripts for logrotate configuration
        [Default: (null)]
        type: dict

- apache_mods_disabled
        Extra apache2 mods to disable
        [Default: (null)]
        elements: str
        type: list

- apache_mods_enabled
        Extra apache2 mods to enable
        [Default: (null)]
        elements: str
        type: list

- apache_mods_templates
        Template files for modifying mod configuration under mods-
        available
        Builtin templates available:
          * mods/ssl.conf
        [Default: ['mods/ssl.conf']]
        elements: str
        type: list

- apache_options
        Default options settings for all vhosts
        [Default: -Indexes +FollowSymLinks]
        type: str

- apache_sites_disabled
        Files to be removed from sites-enabled (files in
        apache_sites_templates or apache_vhosts_filename are not
        removed)
        [Default: (null)]
        elements: str
        type: list

- apache_sites_templates
        Template files for additional vhosts
        [Default: (null)]
        elements: str
        type: list

- apache_ssl_ciphers
        List of ciphers available for negotiation in SSL handshake
        [Default: ['HIGH', '!aNULL']]
        elements: str
        type: list

- apache_ssl_extra
        Extra SSL mod configuration
        [Default: (null)]
        type: str

- apache_ssl_options
        SSL options for all HTTPS vhosts
        [Default: (null)]
        type: str

- apache_ssl_protocols
        List of SSL/TLS protocols to enable
        [Default: ['all', '-SSLv3']]
        elements: str
        type: list

- apache_vhosts
        Configuration for HTTP vhosts
        [Default: (null)]
        elements: dict
        type: list

        OPTIONS:

        - allow_override
            Types of directives that are allowed in .htaccess files
            under documentroot
            [Default: (null)]
            type: str

        - customlog
            Filename for access log stored under /var/log/apache2/
            [Default: (null)]
            type: str

        - documentroot
            Directory that forms the main document tree visible from
            the web
            [Default: (null)]
            type: str

        - errorlog
            Filename for error log stored under /var/log/apache2/
            [Default: (null)]
            type: str

        - extra_parameters
            Extra configuration
            [Default: (null)]
            type: str

        - https_redirect
            Configuration for redirecting HTTP requests to HTTPS
            [Default: (null)]
            type: str

        - listenon
            Listen addresses and ports
            [Default: (null)]
            elements: str
            type: list

        - loglevel
            Controls the verbosity of the error log
            [Default: (null)]
            type: str

        - options
            Configures what features are available under documentroot
            [Default: (null)]
            type: str

        - serveradmin
            Email address that the server includes in error messages
            sent to the client
            [Default: (null)]
            type: str

        - serveralias
            Alternate names for a host used when matching requests to
            name-virtual hosts
            [Default: (null)]
            type: str

        = servername
            Hostname and port that the server uses to identify itself

            type: str

- apache_vhosts_filename
        Destination filename for vhosts configuration file
        [Default: (null)]
        type: str

- apache_vhosts_ssl
        Configuration for HTTPS vhosts
        [Default: (null)]
        elements: dict
        type: list

        OPTIONS:

        - allow_override
            Types of directives that are allowed in .htaccess files
            under documentroot
            [Default: (null)]
            type: str

        - certificate_chain_file
            File path to SSL certificate chain
            [Default: (null)]
            type: str

        = certificate_file
            File path to SSL certificate

            type: str

        = certificate_key_file
            File path to SSL key

            type: str

        - customlog
            Filename for access log stored under /var/log/apache2/
            [Default: (null)]
            type: str

        - documentroot
            Directory that forms the main document tree visible from
            the web
            [Default: (null)]
            type: str

        - errorlog
            Filename for error log stored under /var/log/apache2/
            [Default: (null)]
            type: str

        - extra_parameters
            Extra configuration
            [Default: (null)]
            type: str

        - listenon
            Listen addresses and ports
            [Default: (null)]
            elements: str
            type: list

        - loglevel
            Controls the verbosity of the error log
            [Default: (null)]
            type: str

        - options
            Configures what features are available under documentroot
            [Default: (null)]
            type: str

        - serveradmin
            Email address that the server includes in error messages
            sent to the client
            [Default: (null)]
            type: str

        - serveralias
            Alternate names for a host used when matching requests to
            name-virtual hosts
            [Default: (null)]
            type: str

        = servername
            Hostname and port that the server uses to identify itself

            type: str

- apache_vhosts_template
        Source template file on host running ansible for vhosts
        configuration
        [Default: (null)]
        type: str
```

Installation
------------

This role can either be installed manually with the ansible-galaxy CLI tool:

    ansible-galaxy install git+https://github.com/wandansible/apache,main,wandansible.apache
     
Or, by adding the following to `requirements.yml`:

    - name: wandansible.apache
      src: https://github.com/wandansible/apache

Roles listed in `requirements.yml` can be installed with the following ansible-galaxy command:

    ansible-galaxy install -r requirements.yml

Example Playbook
----------------

    - hosts: web_servers
      roles:
         - role: wandansible.apache
           become: true
           vars:
             apache_vhosts:
               - servername: "example.org"
                 serveradmin: "sysadmin@example.org"
                 errorlog: error.log
                 customlog: access.log
                 https_redirect: |
                   Redirect permanent / https://example.org/

             apache_vhosts_ssl:
               - servername: "example.org"
                 serveradmin: "sysadmin@example.org"
                 documentroot: /var/www/html/
                 errorlog: ssl_error.log
                 customlog: ssl_access.log
                 certificate_file: /etc/letsencrypt/live/example.org/fullchain.pem
                 certificate_key_file: /etc/letsencrypt/live/example.org/privkey.pem
                 extra_parameters: |
                   Protocols h2 http/1.1

             apache_conf_templates:
               - conf/letsencrypt.conf
             
             apache_ssl_protocols:
               - "all"
               - "-SSLv3"
               - "-TLSv1"
               - "-TLSv1.1"
               - "-TLSv1.2"
             
             apache_ssl_extra: |
               SSLHonorCipherOrder     off
               SSLSessionTickets       off
               
               SSLUseStapling On
               SSLStaplingCache "shmcb:logs/ssl_stapling(32768)"
             
             apache_default_mods_enabled:
               - ssl
               - headers
             
             apache_ssl_options: Header always set Strict-Transport-Security "max-age=15768000"
