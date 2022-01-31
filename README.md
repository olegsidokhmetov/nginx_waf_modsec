Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

Run file main.yml in folder `/task`

```
---
- hosts: nginx
  become: true
  vars_files:
  - /etc/ansible/roles/NextCloud/vars/main.yml
  - /etc/ansible/roles/NextCloud/defaults/main.yml
  tasks:

    - name: 1-Update and upgrade apt packages
      include: 1-Update_and_upgrade_apt_packages.yaml

    - name: 2-Install Nginx and update apt cache
      include: 2-Install_Nginx.yaml

    - name: 3-Install dependencies
      include: 3-Install_dependencies.yaml

    - name: 4-Create directory
      include: 4-Create_directory.yaml

    - name: 5-Download ssdeep using git
      include: 5-Download_ssdeep_using_git.yaml

    - name: 6-Install ssdeep
      include: 6-Install_ssdeep.yaml

    - name: 7-Download ModSecurity using git branch {{ git_app_branch_ver_ModSecurity }}
      include: 7-Download_ModSecurity_using_git_branch_v3_master.yaml

    - name:  8-Install ModSecurity from directory {{ git_dest_folder_ModSecurity }}
      include: 8-Install_ModSecurity.yaml

    - name:  9-Download ModSecurity-nginx using git{{ git_dest_folder_ModSecurity-nginx }}
      include: 9-Download_ModSecurity-nginx_using_git.yaml

    - name:  10-Check nginx version
      include: 10-Check_nginx_version.yaml

    - name:  11-Download nginx with version 1.18.0 in "{{ download_dir }}"
      include: 11-Download_nginx_needed_version.yaml

    - name: 12-Add new line "load_module modules/ngx_http_modsecurity_module.so;" in file {{ nginx_conf_file }}
      include: 12-Editing_nginx_conf_file.yaml

    - name: 13-Create directory /etc/nginx/modsec/ for store ModSecurity configuration
      include: 13-Create_directory_modsec.yaml

    - name: 14-Copy the ModSecurity configuration to folder {{ ModSecurity_nginx_dir_config }}
      include: 14-Copy_modSecurity_configuration.yaml

    - name: 15-Editing modsecurity.conf file in folder {{ ModSecurity_nginx_dir_config }}
      include: 15-Editing_modsecurity.conf_file.yaml

    - name: 16-Create file modsec-config.conf with new line "Include /etc/nginx/modsec/modsecurity.conf"
      include: 16-Create_modsec-config.conf_with_config.yaml

    - name: 17-Copy file unicode.mapping from folder {{ git_dest_folder_ModSecurity }} to folder {{ ModSecurity_nginx_dir_config }}
      include: 17-Copy_unicode.mapping.yaml

    - name: 18-Restart nginx
      include: 18-Restart_Nginx.yaml

    - name: 19-Download OWASP version v3.3.2 in "{{ download_dir }}"
      include: 19-Download_owasp.yaml

    - name: 20-Copy the "crs-setup.conf.example" configuration file to folder {{ owasp_conf_nginx_dir }}
      include: 20-Create_dir_coreruleset-3.3.2.yaml

    - name: 21-Add new configuration line in file modsec-config.conf
      include: 21-Add_new_conf_line_in_modsec-config.conf.yaml

    - name: 22-Final restart Nginx
      include: 22-Final_restart_Nginx.yaml
```

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
