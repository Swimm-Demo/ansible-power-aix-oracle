---
title: Configuration Overview
---
# Configuration Overview

Configuration refers to the setup and customization of variables and parameters necessary for the installation and deployment of Oracle Single Instance database <SwmToken path="vars/powervc_oracle_params.yml" pos="26:7:7" line-data="ora_parent_dir: &quot;/orabin/19c&quot;">`19c`</SwmToken> on AIX systems. It involves defining various settings such as virtual machine details, storage templates, network configurations, and disk sizes specific to the <SwmToken path="vars/powervc_oracle_params.yml" pos="4:18:18" line-data="# Below are the variables that are specific to PowerVC">`PowerVC`</SwmToken> environment.

Additionally, configuration includes specifying the locations and types of Oracle binaries, user and group details, and filesystem parameters required for the Oracle deployment. The configuration also covers optional settings like NFS details for fileset installation and parameters for using standard NIM filesystems.

Furthermore, it involves setting up Oracle-specific parameters such as SID, passwords, character sets, and ASM disk group configurations.

<SwmSnippet path="/vars/powervc_oracle_params.yml" line="4">

---

The file <SwmPath>[vars/powervc_oracle_params.yml](vars/powervc_oracle_params.yml)</SwmPath> contains variables specific to <SwmToken path="vars/powervc_oracle_params.yml" pos="4:18:18" line-data="# Below are the variables that are specific to PowerVC">`PowerVC`</SwmToken>, including virtual machine name, image ID, profile, network, and disk sizes.

```yaml
# Below are the variables that are specific to PowerVC
vm_name: "oravm"
cimage_id: "9437d7e3-14de-4865-a13b-12479fa05909"
vm_profile: "medium"
vm_network: "Network129"
orasw_vg_disk_size: 100
data_disk_count: 3 
data_disk_size: 20
data_disk_prefix: "{{ vm_name }}_data"
data_disks: "{%- for n in range(2, data_disk_count + 2, 1 ) -%} {%- if n == data_disk_count+1 -%} hdisk{{ n }} {%- else -%} hdisk{{ n }}, {%- endif -%} {%- endfor -%}"
```

---

</SwmSnippet>

# Configuration in <SwmPath>[vars/oracle_params.yml](vars/oracle_params.yml)</SwmPath>

This section specifies the Ansible work directory and the location type of Oracle binaries, which can be remote, local, or NFS.

<SwmSnippet path="/vars/oracle_params.yml" line="4">

---

The file <SwmPath>[vars/oracle_params.yml](vars/oracle_params.yml)</SwmPath> specifies the Ansible work directory on the target system and the location type of Oracle binaries, which can be remote, local, or NFS.

```yaml
# Provide the ansible work directory on target system
work_dir:   &work_dir "/tmp/ansible"

# binary location can be remote|local|nfs
# remote : Ansible Controller location defined in oracledbaix19c & oraclegridaix19c
# local: Local location of Target Hosts
# nfs: Network File system location
ora_binary_location: nfs
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBYW5zaWJsZS1wb3dlci1haXgtb3JhY2xlJTNBJTNBU3dpbW0tRGVtbw==" repo-name="ansible-power-aix-oracle"><sup>Powered by [Swimm](/)</sup></SwmMeta>
