# cisco.ucs Collection Development Notes

### Current Development Status

| Configuration Category | Configuration Task | Module Name |
| ---------------------- | ------------------ | ----------- |
| LAN                    | IP Addresses for KVM Access | ucs_ip_pool |
|                        | MAC Address Pools  | ucs_mac_pool |
|                        | VLANs              | ucs_vlans   | in 2.5 |
| Server                 | UUID Suffix Pool   | ucs_uuid_pool |
|                        | Server Pool        | use ucs_managed_objects, see server_deploy.yml
|                        | Server BIOS Policy | use ucs_managed_objects
|                        | FW/Power/Maintenance Polices | use ucs_managed_objects
|                        | Boot Policy        | use ucs_managed_objects, see server_deploy.yml
|                        | Service Profile Template | ucs_service_profile_template |
|                        | Service Profile from Template | ucs_service_profile_from_template |

### Ansible Development Notes

Modules in development follow processes documented at http://docs.ansible.com/ansible/latest/dev_guide/developing_modules_general.html.  The modules support ansible-doc and should eventually have integration tests.

When developing modules in this repository, here are a few helpful commands to sanity check the code and documentation (replace module_name with your module (e.g., intersight_objects)).  Ansible modules won't generally be pylint or pycodestyle (PEP8) clean without disabling several of the checks:
  ```
  pylint --disable=invalid-name,no-member,too-many-nested-blocks,redefined-variable-type,too-many-statements,too-many-branches,broad-except,line-too-long,missing-docstring,wrong-import-position,too-many-locals,import-error <module_name>.py
  
  pycodestyle --max-line-length 160 --config /dev/null --ignore E402 <module_name>.py
  
  ansible-doc <module_name>
  ```

# Community:

* We are on Slack (https://ciscoucs.slack.com/) - Slack requires registration, but the ucspython team is open invitation to
  anyone.  Click [here](https://ucspython.herokuapp.com) to register 
