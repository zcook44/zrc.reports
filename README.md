# ZRC Reports Collection

The Ansible ZRC Reports collection includes a variety of Ansible content to help automate the creation of Linux, Windows, Cloud, Active Directory, and Networking reports.

<!--start requires_ansible-->
## Ansible version compatibility

This collection has been tested against following Ansible versions: **>=2.9.10**.

Plugins and modules within a collection may be tested with only specific Ansible versions.
A collection may contain metadata that identifies these versions.
PEP440 is the schema used to describe the versions of Ansible.
<!--end requires_ansible-->

## Tested with Ansible

This collection has been tested against RHEL 7, 8, 9, Windows Server 2016, IOS, EOS, VyOS
<!-- List the versions of Ansible the collection has been tested with. Must match what is in galaxy.yml. -->

## External requirements
<!-- List any external resources the collection depends on, for example minimum versions of an OS, libraries, or utilities. Do not list other Ansible collections here. -->

## Included content
<!--start collection content-->


### Modules
Name | Description
--- | ---
[zrc.reports.win_scan_packages](https://github.com/zcook44/zrc.reports/blob/main/docs/zrc.reports.win_scan_packages_module.rst)|Scans for all packages on a Windows server
[zrc.reports.win_scan_services](https://github.com/zcook44/zrc.reports/blob/main/docs/zrc.reports.win_scan_services_module.rst)|Scans for all services on a Windows server

<!--end collection content-->

## Installing this collection

You can install the ZRC Reports collection with the Ansible Galaxy CLI:

    ansible-galaxy collection install zrc.reports

You can also include it in a `requirements.yml` file and install it with `ansible-galaxy collection install -r requirements.yml`, using the format:

```yaml
---
collections:
  - name: zrc.reports
```
## Using this collection

### Using ZRC Reports Ansible Collection

An example for using this collection to scan a Windows host for packages:


```yaml
---
- name: Scan packages of all Windows hosts
  hosts: windows

  tasks:

    - name: "Scan packages (Windows)"
      zrc.reports.win_scan_packages:

```


### Code of Conduct
This collection follows the Ansible project's
[Code of Conduct](https://docs.ansible.com/ansible/devel/community/code_of_conduct.html).
Please read and familiarize yourself with this document.

## Roadmap

<!-- Optional. Include the roadmap for this collection, and the proposed release/versioning strategy so users can anticipate the upgrade/update cycle. -->

## More information

- [Ansible Collection overview](https://github.com/ansible-collections/overview)
- [Ansible User guide](https://docs.ansible.com/ansible/latest/user_guide/index.html)
- [Ansible Developer guide](https://docs.ansible.com/ansible/latest/dev_guide/index.html)
- [Ansible Community code of conduct](https://docs.ansible.com/ansible/latest/community/code_of_conduct.html)

## Licensing

GNU General Public License v3.0 or later.

See [LICENSE](https://www.gnu.org/licenses/gpl-3.0.txt) to see the full text.
