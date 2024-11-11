---
title: Roles Overview
---
# Roles Overview

Roles are a fundamental component used to encapsulate a set of tasks and configurations that can be reused across different playbooks. Each role is designed to perform a specific function, such as configuring the AIX environment, installing Oracle software, or creating a database.

Roles help in organizing the automation workflow by breaking down complex processes into smaller, manageable units. They include various elements like tasks, variables, handlers, and templates, which are defined in their respective directories within the role.

Dependencies between roles can be defined to ensure that certain roles are executed before others, maintaining the correct order of operations. Roles are invoked in playbooks using the `include_role` directive, specifying the name of the role to be executed.

## Example Playbook

This example demonstrates how to use a role in a playbook, specifying the role name and passing variables as parameters.

## Role Variables

This section describes the settable variables for the role, including those in <SwmPath>[roles/powervc_create_aixvm/defaults/main.yml](roles/powervc_create_aixvm/defaults/main.yml)</SwmPath>, <SwmPath>[roles/powervc_create_aixvm/vars/main.yml](roles/powervc_create_aixvm/vars/main.yml)</SwmPath>, and any variables that can be set via parameters.

## Role Endpoints

Role endpoints are specific tasks or actions that can be executed within a role. Below are some examples of role endpoints.

<SwmSnippet path="/roles/preconfig/.travis.yml" line="15">

---

### Install Ansible

The <SwmToken path="roles/preconfig/.travis.yml" pos="16:5:7" line-data="  - pip install ansible">`install ansible`</SwmToken> endpoint installs Ansible using pip. This is crucial for running Ansible playbooks and roles.

```yaml
  # Install ansible
  - pip install ansible
```

---

</SwmSnippet>

<SwmSnippet path="/roles/preconfig/.travis.yml" line="24">

---

### Syntax Check

The <SwmToken path="roles/preconfig/.travis.yml" pos="25:7:9" line-data="  # Basic role syntax check">`syntax check`</SwmToken> endpoint runs a basic syntax check on the Ansible playbook to ensure there are no syntax errors before execution.

```yaml
script:
  # Basic role syntax check
  - ansible-playbook tests/test.yml -i tests/inventory --syntax-check
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBYW5zaWJsZS1wb3dlci1haXgtb3JhY2xlJTNBJTNBU3dpbW0tRGVtbw==" repo-name="ansible-power-aix-oracle"><sup>Powered by [Swimm](/)</sup></SwmMeta>
