# Ansible role: Platform.sh local setup

[![Build Status](https://travis-ci.org/danbohea/ansible-role-platformsh.svg?branch=master)](https://travis-ci.org/danbohea/ansible-role-platformsh)

Helps automate the setup of your Platform.sh project in local development when using the Platform.sh CLI.

- Configures passwordless authentication via your Platform.sh user API token.
- Enables autocompletion and shell aliases.
- Sets your project remote.
- Builds your project (`platfrom build`).

Optional Drupal-specific features:

- Generates drush aliases.
- Renames drush alias group name to something sensible (i.e. not the Platform.sh app ID).


## Requirements

- [Platform.sh CLI](https://github.com/platformsh/platformsh-cli)
- [Drush](https://github.com/drush-ops/drush) (optional)


## Role Variables

All role default variables are listed below along with their respective default values.

```yaml
# Platform.sh user
# ------------------------------------------------------------------------------

# Platform.sh user API token.
# Required for passwordless authentication.

platformsh_token: null

# Platform.sh app
# ------------------------------------------------------------------------------

# The Platform.sh app ID as set when you create your Platform.sh project.

platformsh_app_id: xxxxxxxxxxxxx

# A succinct string to identify your project.
# Will be used to as the drush alias group name.

platformsh_app_name: myapp

# Indicate whether your project is a Drupal site or not.
# Determines whether to setup drush aliases.

platformsh_app_drupal: false

# Local environment
# ------------------------------------------------------------------------------

# The user that will be accessing the Platform.sh CLI

platformsh_user: vagrant

# The install location of the Platform.sh CLI binary (parent directory).

platformsh_install_dir: "/home/{{ platformsh_user }}/.composer/vendor/bin"

# The configuration directory for the Platform.sh CLI.

platformsh_config_dir: "/home/{{ platformsh_user }}/.platformsh"

# The root directory of your application.

platformsh_app_root: /var/www/drupalvm
```


## Dependencies

None.


## Example Playbook

```
- hosts: localhost
  connection: local

  roles:
    - pixelart.platformsh-cli
    - geerlingguy.drush
    - ansible-role-platformsh
```


## License

MIT


## Author Information

This role was created by [Dan Bohea](http://bohea.co.uk).
