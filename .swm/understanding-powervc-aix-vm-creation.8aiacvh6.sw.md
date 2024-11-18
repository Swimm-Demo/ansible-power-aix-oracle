---
title: Understanding PowerVC AIX VM Creation
---
# Overview

<SwmToken path="powervc_oracle_play.yml" pos="2:11:11" line-data="- name: &quot;Play1: Creating PowerVC VM&quot; ">`PowerVC`</SwmToken> AIX VM Creation involves creating a new AIX virtual machine using IBM's <SwmToken path="powervc_oracle_play.yml" pos="2:11:11" line-data="- name: &quot;Play1: Creating PowerVC VM&quot; ">`PowerVC`</SwmToken>, which is a virtualization and cloud management solution. This process is automated using Ansible playbooks and roles.

# Role: <SwmToken path="powervc_oracle_play.yml" pos="9:6:6" line-data="    - role: powervc_create_aixvm ">`powervc_create_aixvm`</SwmToken>

The role <SwmToken path="powervc_oracle_play.yml" pos="9:6:6" line-data="    - role: powervc_create_aixvm ">`powervc_create_aixvm`</SwmToken> is responsible for the creation of the AIX VM. It includes various tasks, handlers, and variables that define the configuration and steps required to create the VM.

<SwmSnippet path="/powervc_oracle_play.yml" line="1">

---

This snippet from <SwmPath>[powervc_oracle_play.yml](powervc_oracle_play.yml)</SwmPath> shows how the playbook is structured to create a <SwmToken path="powervc_oracle_play.yml" pos="2:11:11" line-data="- name: &quot;Play1: Creating PowerVC VM&quot; ">`PowerVC`</SwmToken> VM using the <SwmToken path="powervc_oracle_play.yml" pos="9:6:6" line-data="    - role: powervc_create_aixvm ">`powervc_create_aixvm`</SwmToken> role.

```yaml
---
- name: "Play1: Creating PowerVC VM" 
  hosts: localhost 
  gather_facts: yes
  vars_files: vars/powervc_oracle_params.yml
  vars:
    ansible_python_interpreter: /usr/bin/python 
  roles:
    - role: powervc_create_aixvm 
      tags: powervc_create_aixvm
```

---

</SwmSnippet>

# Variables: <SwmPath>[vars/powervc_oracle_params.yml](vars/powervc_oracle_params.yml)</SwmPath>

The variables required for the VM creation, such as the work directory, are defined in the <SwmPath>[vars/powervc_oracle_params.yml](vars/powervc_oracle_params.yml)</SwmPath> file. These variables are used by the tasks within the <SwmToken path="powervc_oracle_play.yml" pos="9:6:6" line-data="    - role: powervc_create_aixvm ">`powervc_create_aixvm`</SwmToken> role to configure the VM creation process.

<SwmSnippet path="/vars/powervc_oracle_params.yml" line="1">

---

This snippet from <SwmPath>[vars/powervc_oracle_params.yml](vars/powervc_oracle_params.yml)</SwmPath> shows the variables specific to <SwmToken path="vars/powervc_oracle_params.yml" pos="2:28:28" line-data="# This file is defining Oracle Variables needed for oracle single instance installation on PowerVC AIX VM">`PowerVC`</SwmToken> that are needed for the Oracle Single Instance installation on <SwmToken path="vars/powervc_oracle_params.yml" pos="2:28:28" line-data="# This file is defining Oracle Variables needed for oracle single instance installation on PowerVC AIX VM">`PowerVC`</SwmToken> AIX VM.

```yaml
# Copyright (c) IBM Corporation 2021
# This file is defining Oracle Variables needed for oracle single instance installation on PowerVC AIX VM

# Below are the variables that are specific to PowerVC
vm_name: "oravm"
cimage_id: "9437d7e3-14de-4865-a13b-12479fa05909"
vm_profile: "medium"
vm_network: "Network129"
orasw_vg_disk_size: 100
data_disk_count: 3 
```

---

</SwmSnippet>

# Tasks: <SwmPath>[roles/powervc_create_aixvm/tasks/](roles/powervc_create_aixvm/tasks/)</SwmPath>

The tasks within the <SwmToken path="powervc_oracle_play.yml" pos="9:6:6" line-data="    - role: powervc_create_aixvm ">`powervc_create_aixvm`</SwmToken> role are organized in the <SwmPath>[roles/powervc_create_aixvm/tasks/](roles/powervc_create_aixvm/tasks/)</SwmPath> directory. These tasks include the specific steps needed to create and configure the AIX VM on <SwmToken path="powervc_oracle_play.yml" pos="2:11:11" line-data="- name: &quot;Play1: Creating PowerVC VM&quot; ">`PowerVC`</SwmToken>.

```mermaid
graph TD;
    A[PowerVC AIX VM Creation] --> B[powervc_create_aixvm Role];
    B --> C[Tasks];
    B --> D[Handlers];
    B --> E[Variables];
    A --> F[powervc_oracle_play.yml Playbook];
    F --> G[Creating PowerVC VM];
    F --> vars/powervc_oracle_params.yml Variables];

%% Swimm:
%% graph TD;
%%     A[PowerVC AIX VM Creation] --> B[powervc_create_aixvm Role];
%%     B --> C[Tasks];
%%     B --> D[Handlers];
%%     B --> E[Variables];
%%     A --> F[powervc_oracle_play.yml Playbook];
%%     F --> G[Creating <SwmToken path="powervc_oracle_play.yml" pos="2:11:11" line-data="- name: &quot;Play1: Creating PowerVC VM&quot; ">`PowerVC`</SwmToken> VM];
%%     F --> H[<SwmPath>[vars/powervc_oracle_params.yml](vars/powervc_oracle_params.yml)</SwmPath> Variables];
```

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBYW5zaWJsZS1wb3dlci1haXgtb3JhY2xlJTNBJTNBU3dpbW0tRGVtbw==" repo-name="ansible-power-aix-oracle"><sup>Powered by [Swimm](/)</sup></SwmMeta>
