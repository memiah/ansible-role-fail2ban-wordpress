Fail2ban WordPress
==================

An Ansible Role that installs the fail2ban service and [WordPress 
fail2ban plugin](https://wordpress.org/plugins/wp-fail2ban/) on RedHat systems.

Requirements
------------

A WordPress installation must exist on the target system.

Role Variables
--------------

Available variables are listed below, along with default values (see 
`defaults/main.yml`):

    fail2ban_wordress_plugin_name: wp-fail2ban

Name of the WordPress fail2ban plugin.

    fail2ban_wordress_plugin_version: ""
    
Version of the plugin to install, if empty the development version is installed.

    fail2ban_wordress_plugins_dir: /tmp

Path to the WordPress plugins directory, or temporary directory if using as must use plugin.

    fail2ban_wordress_mu_plugins_dir: false
    
Path to the mu-plugins directory if installing as a must use plugin.

    fail2ban_wordress_log_path: /var/log/messages

Log file to use.

    fail2ban_wordress_bantime: 3600

Time (in seconds) to ban IPs for.

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: webservers
      become: yes
      vars_files:
        - vars/main.yml
      roles:
         - memiah.fail2ban-wordpress

*Inside `vars/main.yml`*:

    fail2ban_wordress_plugin_version: ""
    fail2ban_wordress_plugin_dir: /path/to/wp-plugins/

View the status of the wordpress filter:

    fail2ban-client status wordpress

License
-------

MIT / BSD

Author Information
------------------

This role was created in 2016 by [Memiah Limited](https://github.com/memiah).
