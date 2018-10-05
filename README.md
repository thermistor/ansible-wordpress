# WordPress ansible role

## Usage

    - role: wordpress
      wordpress_production_site: example.com
      wordpress_shortname: example
      wordpress_git_repo: ssh://git@github.com/username/example
      wordpress_base_dir: /home/example/example.com
      wordpress_symlink_deploy: no
      wordpress_deployer_keys:
        - "{{ lookup('file', 'files/ssh_keys/jane_deployer.pub') }}"
      wordpress_db_password: d34db33f
      wordpress_auth_key: d34db33f
      wordpress_secure_auth_key: d34db33f
      wordpress_logged_in_key: d34db33f
      wordpress_nonce_key: d34db33f
      wordpress_auth_salt: d34db33f
      wordpress_secure_auth_salt: d34db33f
      wordpress_logged_in_salt: d34db33f
      wordpress_nonce_salt: d34db33f
      wordpress_themes:
        - como
      wordpress_plugins:
        - {name: google-sitemap-generator, version: tags/4.0.9}
        - {name: login-logo, version: tags/0.9.0}
        - {name: w3-total-cache, version: tags/0.9.7}


## To update wordpress to a new version

Change the `wordpress_version` in this role's `defaults/main.yml` then do:

    ansible-playbook -K -i staging blog.yml --tags wordpress_update


## To update plugins

Change the plugin's version in playbook (really it's a path, can be in form `tags/0.9.0` or `trunk`).
Also to change akismet's version, change `wordpress_akismet_version` in this role's `defaults/main.yml`.
Then do:

    ansible-playboo0k -K -i staging blog.yml --tags wordpress_plugins
