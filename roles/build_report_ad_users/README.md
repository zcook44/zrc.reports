build_report_ad_users
========

Gathers users from an Active Directory Domain Controller and then on a Linux host installs Apache and creates a report based on current Active Directory Users


Requirements
------------

Must run on an Active Directory Domain Controller and then the report must be deployed onto an Apache server

Role Variables / Configuration
--------------

N/A

Dependencies
------------

N/A

Example Playbook
----------------

The role can be used to create an html report on a Linux host by getting users from an Active Directory Domain Controller.


```
---
- name: Build AD User Info Report
  hosts: all

  tasks:

    - name: Get AD user accounts with groups and lock status
      ansible.windows.win_shell: |
        Import-Module ActiveDirectory
        Get-ADUser -Filter * -Property GivenName, Surname, SamAccountName, MemberOf, LockedOut |
        Select-Object GivenName, Surname, SamAccountName, @{Name="Groups";Expression={(Get-ADUser -Identity $_.SamAccountName -Property MemberOf |
        Select-Object -ExpandProperty MemberOf | Get-ADGroup | Select-Object -ExpandProperty Name) -join ", "}}, LockedOut |
        ConvertTo-Json
      register: ad_users

    - name: Build the report
      ansible.builtin.include_role:
        name: shadowman.reports.build_report_ad_users
        apply:
          delegate_to: report.zrc.dev
          run_once: true
```
