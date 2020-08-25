Dynatrace-ActiveGate-Ansible
================

### Note: Documentation in Progress

Ansible role to install/update/rollback/uninstall ActiveGate on Linux

Use this role to install default & Custom AGs that focus on specific functions
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

You will need to supply the role with following parameters.

Dynatrace Environment Url: **Managed** `https://{your-domain}/e/{your-environment-id}` |  **SaaS** `https://{your-environment-id}.live.dynatrace.com`

Paas Token: Required for downloading ActiveGate. See documentation on creating [PaaS token](https://www.dynatrace.com/support/help/shortlink/kubernetes-applications)

ActiveGate function: Available options - default/synthetic/synthetic_http_only/zremote/oneagent_routing/integrations/custom

Role Variables
--------------

 TO BE ADDED SOON..

Dependencies
------------

 TO BE ADDED SOON..

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
      dynatrace_activegate_function: "default"
```

License
-------

Licensed under the MIT License. See the LICENSE file for details.
