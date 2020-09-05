Dynatrace-ActiveGate-Ansible
================

Ansible role to install/update/rollback/uninstall ActiveGate on Linux

Use this role to install following ActiveGate types:
1. Default AG
2. OneAgent Routing AG - OneAgent traffic routing & DB plugins only
3. Integrations AG - AWS, Azure, Cloud Foundry, Kubernetes, VMWare integrations
4. Synthetic AG - Synthetic Monitoring - Browser & HTTP Monitoring
5. Synthetic HTTP Only - Synthetic Monitoring - HTTP Monitoring Only
6. Custom AG - Specify custom functions eg: Plugin Module

Note: This role is based on Dynatrace [Dynatrace-OneAgent-Ansible](https://github.com/Dynatrace/Dynatrace-OneAgent-Ansible) role

Requirements
------------

Requires ansible >= 2.9.0


Role Variables
--------------

`*`Mandatory

| Parameter                           |  Variable                          | Variable Values                                              |
| :-----------------------------------|:-----------------------------------| :----------------------------------------------------------  |
| Dynatrace Environment Url`*`        | `dynatrace_environment_url:`       | **Managed** `https://{your-domain}/e/{your-environment-id}`  |
|                                     |                                    | **SaaS** `https://{your-environment-id}.live.dynatrace.com`  |
| PaaS Token`*` (for downloading AG)  | `dynatrace_paas_token:`            | See documentation on creating [PaaS token](https://www.dynatrace.com/support/help/shortlink/kubernetes-applications) |
| Role Task`*`                        | `dynatrace_activegate_role_task:`  | `install`, `update`, `rollback`, `uninstall` |
| ActiveGate Version                  | `dynatrace_activegate_version:`    | default: `latest`. List all available versions of the ActiveGate installer using [API](https://www.dynatrace.com/support/help/dynatrace-api/environment-api/deployment/activegate/get-activegate-versions/) |
| ActiveGate Function                 | `dynatrace_activegate_function:`   | default: `default`. Options: `default`, `synthetic`, `synthetic_http_only`, `zremote`,`oneagent_routing`,`integrations`,`custom` |

`
`
### See Role `defaults/main.yml` for full list of variables


Dependencies
------------

 None

Example Playbook
----------------
```
  ---
  - name: Install ActiveGate
    hosts: testag
    become: true
    serial: 2
    roles:
      - role: Dynatrace-ActiveGate-Ansible
    vars:
      dynatrace_environment_url: tenantid.live.dynatrace.com
      dynatrace_paas_token: <your paas token>
      dynatrace_activegate_role_task: install      
      dynatrace_activegate_version: latest
      dynatrace_activegate_function: default
```

License
-------

Licensed under the MIT License. See the LICENSE file for details.
