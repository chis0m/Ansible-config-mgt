## Ansible-config-mgt
Project 12

#### static import
Roles directory                 - abstract out the tasks
static assignments dir          - Roles are referenced here
sites.yml                       - entry point to our ansible configuration

`Roles(tasks) --> static playbooks  --> sites.yml`

#### dynamic import
Roles directory                    - abstract out the tasks
env-vars dir                       - abstract out environment variables with values unique to an environment
dynamic-assignment/env-vars.yml    - programmatically load variables from `env-vars` dir
sites.yml                          - entry point to our playbook

- In `Roles` directory e.g `Roles/chisom.nginx.lb/default/main.yml` and `Roles/chisom.apache.lb/default/main.yml`, we turn off the load balancers by default.
- In `env-vars` based on environment we specify which loadbalancers to use
- Dynamic import 
  - In `dynamic-assignements/env-vars.yml` playbook we dynamically load environment settings from `env-vars/*` to determine what lb to use for each environment
  - In `static-assignments/loadbalancers.yml` we import lbs roles based on their default config
- In `playbook/sites.yml` we import the different playbooks from static/dynamic-assignments