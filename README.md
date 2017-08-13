# ansible-role-passwordless-user

Configures user with passwordless login:
- Creates a user.
- Allows given RSA pub keys to login passwordlessly with the user.
- Configures the user to have passwordless sudo to root.

## Requirements

No specific requirements

## Role Variables

Variable                  | Default             | Comments
---                       | ---                 | ---
passwordless_user         | example_user        | Automation user to be configured for ansible usage.
passwordless_user_sshkeys | `~/.ssh/id_rsa.pub` | RSA pub keys added to auth keys on the automation user

## Dependencies

No dependencies.

## Usage

Example playbook:
```yaml
---
- hosts: hosts
  become: true
  user: root

  vars:
    passwordless_user: admin
    passwordless_user_sshkeys:
      - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDPHzsPpUwr6C0yW5JLAxF0lnNfvA8qO4BVfavzZURid5ARiiOO0mrnerQoe1nlDM63HNISwmciPGPrkpDOSqJGtobU63xJPJ/vnZJ2WkIKOIB0+gzPRzAx9UCM16kD2TFQf/fAN+3dC4gsFQ5SbSYTQ4sR5K7/+cw6X4KZIqQclx+yoEBB1ERT1wnRyzz/yYrYi9ITr0CTk9cEMJCdeqHHXUy1k60MTyjKGA5YOhcd2idnrh7xAu9n3dvo2XywBRxsycRjNExI3GxjfKR0xl1HZeTlCCLd1Flsx71KmGymgutMDWBMeQILtVWGKiW1uuHCfdANRwrn07 example@example.com
  roles:
    - ansible-role-passwordless-user
```

Execution example:
```sh
ansible-playbook passwordless_user.yml  -k
```
