Ansible Role:Red Hat Process Automation Manager on OpenShift
=========

This role Red Hat Process Automation Manager on OpenShift.

Role Variables
------------

| Variable                    | Default Value      | Required |  Description   |
|-----------------------------|--------------------|----------|----------------|
|`OCP_PROJECT`                | `rhpam`            | Required | OpenShift project name in which to provision this role |
|`DOCKER_IMAGES_TAG`          | `7.3.0.GA`      | Optional | RHPAM container image tag in registry.redhat.io |

OpenShift Version Compatibility
------------

When listing this role in `requirements.yml`, make sure to pin the version of the role via one of the tags:

```
- src: duncandoyle.ansible_openshift_rhpam
  version: 0.0.1
```  

The following tables shows the version combinations that are tested and verified:

| Role Version      | OpenShift Version |
|-------------------|-------------------|
| 0.0.1   | 3.11.x  |

Note that if a version combination is not listed above, it does **NOT** mean that it won't work on that
version. The above table is merely the combinations that we have verified and tested.


Example Playbook
------------

```
name: Example Playbook
hosts: localhost
tasks:
- import_role:
    name: duncandoyle.ansible_openshift_rhpam
  vars:
    OCP_PROJECT: "rhpam"
```

Test locally
------------
If you want to test this role locally:

```
ansible-playbook -i tests/inventory tests/role_provision.yml \
        -e OCP_PROJECT=rhamt
```

__NOTE:__ Add as many parameter variations from the defaults as you want.
