---
title: Using Ansible in the ansible-power-aix-oracle Repository
---
# Intro

This document explains how Ansible is used in the context of the ansible-power-aix-oracle repository. It will cover the configuration and usage of Ansible for automating the installation of Oracle Single Instance database <SwmToken path="vars/oracle_params.yml" pos="24:10:10" line-data="           - /binora/images/oracle/19c/V982583-01_193000_db.zip">`19c`</SwmToken> on a new AIX operating system.

<SwmSnippet path="/ansible.cfg" line="1">

---

# Ansible Configuration

The <SwmPath>[ansible.cfg](ansible.cfg)</SwmPath> file contains the configuration settings for Ansible. It specifies the default behavior and connection settings for Ansible.

```ini
[defaults]
inventory = ./inventory
interpreter_python = /usr/bin/python
#interpreter_python = /usr/opt/freeware/bin/python3
remote_user = root
host_key_checking = False
remote_tmp = /tmp/.ansible
[ssh_connection]
ssh_args = -o ForwardAgent=yes -o ControlPersist=30m -o ServerAliveInterval=45 -o ServerAliveCountMax=10

```

---

</SwmSnippet>

<SwmSnippet path="/ansible.cfg" line="1">

---

# Default Settings

The <SwmToken path="ansible.cfg" pos="1:0:2" line-data="[defaults]">`[defaults]`</SwmToken> section sets the default <SwmPath>[inventory](inventory)</SwmPath> file location, Python interpreter, remote user, and other settings.

- **Inventory File**: Specifies the <SwmPath>[inventory](inventory)</SwmPath> file location (<SwmToken path="ansible.cfg" pos="2:0:5" line-data="inventory = ./inventory">`inventory = ./inventory`</SwmToken>).
- **Python Interpreter**: Specifies the Python interpreter to use (<SwmToken path="ansible.cfg" pos="3:0:9" line-data="interpreter_python = /usr/bin/python">`interpreter_python = /usr/bin/python`</SwmToken>).
- **Remote User**: Specifies the remote user for SSH connections (<SwmToken path="ansible.cfg" pos="5:0:4" line-data="remote_user = root">`remote_user = root`</SwmToken>).
- **Host Key Checking**: Disables host key checking (<SwmToken path="ansible.cfg" pos="6:0:4" line-data="host_key_checking = False">`host_key_checking = False`</SwmToken>).
- **Remote Temporary Directory**: Specifies the remote temporary directory (<SwmToken path="ansible.cfg" pos="7:0:7" line-data="remote_tmp = /tmp/.ansible">`remote_tmp = /tmp/.ansible`</SwmToken>).

```ini
[defaults]
inventory = ./inventory
interpreter_python = /usr/bin/python
#interpreter_python = /usr/opt/freeware/bin/python3
remote_user = root
host_key_checking = False
remote_tmp = /tmp/.ansible
```

---

</SwmSnippet>

<SwmSnippet path="/ansible.cfg" line="8">

---

# SSH Connection Settings

The <SwmToken path="ansible.cfg" pos="8:0:2" line-data="[ssh_connection]">`[ssh_connection]`</SwmToken> section sets the SSH connection options.

- **SSH Arguments**: Specifies the SSH arguments to use (<SwmToken path="ansible.cfg" pos="9:0:30" line-data="ssh_args = -o ForwardAgent=yes -o ControlPersist=30m -o ServerAliveInterval=45 -o ServerAliveCountMax=10">`ssh_args = -o ForwardAgent=yes -o ControlPersist=30m -o ServerAliveInterval=45 -o ServerAliveCountMax=10`</SwmToken>).

```ini
[ssh_connection]
ssh_args = -o ForwardAgent=yes -o ControlPersist=30m -o ServerAliveInterval=45 -o ServerAliveCountMax=10

```

---

</SwmSnippet>

# Ansible Role: oracle_createdb

This role creates a test database using the DBCA utility from Oracle Home. It is included in the playbook to automate the database creation process.

# Example Playbook for oracle_createdb

The example playbook demonstrates how to include the `oracle_createdb` role in a playbook.

```yaml
- hosts: aix
  include_role:
    name: oracle_createdb
```

# Ansible Role: preconfig

This role performs AIX configuration tasks needed for Oracle installation. It is included in the playbook to prepare the AIX environment for Oracle installation.

# Example Playbook for preconfig

The example playbook demonstrates how to include the <SwmToken path="vars/oracle_params.yml" pos="32:0:0" line-data="preconfig:">`preconfig`</SwmToken> role in a playbook.

```yaml
- hosts: aix
  include_role:
    name: preconfig
```

<SwmSnippet path="/vars/oracle_params.yml" line="4">

---

# Ansible Variables

The <SwmPath>[vars/oracle_params.yml](vars/oracle_params.yml)</SwmPath> file defines variables used in the playbooks. The <SwmToken path="vars/oracle_params.yml" pos="5:0:0" line-data="work_dir:   &amp;work_dir &quot;/tmp/ansible&quot;">`work_dir`</SwmToken> variable specifies the Ansible work directory on the target system (<SwmToken path="vars/oracle_params.yml" pos="5:0:0" line-data="work_dir:   &amp;work_dir &quot;/tmp/ansible&quot;">`work_dir`</SwmToken>`: `<SwmToken path="vars/oracle_params.yml" pos="5:7:10" line-data="work_dir:   &amp;work_dir &quot;/tmp/ansible&quot;">`/tmp/ansible`</SwmToken>).

```yaml
# Provide the ansible work directory on target system
work_dir:   &work_dir "/tmp/ansible"

# binary location can be remote|local|nfs
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBYW5zaWJsZS1wb3dlci1haXgtb3JhY2xlJTNBJTNBU3dpbW0tRGVtbw==" repo-name="ansible-power-aix-oracle"><sup>Powered by [Swimm](/)</sup></SwmMeta>
