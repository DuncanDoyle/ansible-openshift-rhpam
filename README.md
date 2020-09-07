Ansible Role:Red Hat Process Automation Manager on OpenShift
=========

This role deploys Red Hat Process Automation Manager (the RHPAM-Authoring environment) on OpenShift.

Note that this role expects both the RHPAM ImageStreams and RHPAM Authoring template to be available in the `openshift` namespace.

Role Variables
------------

| Variable                    | Default Value      | Required |  Description   |
|-----------------------------|--------------------|----------|----------------|
|`OCP_PROJECT`                | `rhpam`            | Required | OpenShift project name in which to provision this role |
|`IMAGE_STREAM_NAMESPACE`     | `openshift`        | Optional | Namespaces in which the RHPAM ImageStreams have been installed. |
|`RHPAM_VERSION_TAG`          | `7.8.0.GA`         | Optional | RHPAM container image tag in registry.redhat.io. I.e. the RHPAM version to deploy. |
|`RHPAM_ENVIRONMENT`          | `trial-ephemeral`            | Optional | RHPAM Environment type. Currently "trial-ephemeral" (default) and "authoring" have been tested. |
|`RHPAM_VERSION_ID`           | `78`      | Optional | The version id used when selecting the RHPAM-Authoring template to test. E.g. `78` for templates of version `7.3.x`, `74` for templates of version `7.4.x`, etc. |

OpenShift Version Compatibility
------------

When listing this role in `requirements.yml`, make sure to pin the version of the role via one of the tags:

```
- src: duncandoyle.ansible_openshift_rhpam
  version: 0.0.6
```  

The following tables shows the version combinations that are tested and verified:

| Role Version      | OpenShift Version |
|-------------------|-------------------|
| 0.0.1   | 3.11.x  |
| 0.0.2   | 3.11.x  |
| 0.0.3   | 3.11.x  |
| 0.0.4   | 3.11.x  |
| 0.0.5   | 3.11.x, 4.x |
| 0.0.6   | 4.5 |


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
