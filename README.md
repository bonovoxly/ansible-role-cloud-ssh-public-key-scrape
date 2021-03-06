cloud-ssh-public-key-scrape
=========

When managing cloud instances or VMs, verifying and tusting the public SSH fingerprint of the instance/VM has always been difficult to automate. This coupled with `service.ssh-print-host-keys` allows for any user/process to gather any SSH public host key at any time.

Requirements
------------

The cloud CLI tool and a properly authenticated user for that particular service. For instance:

- Google Cloud SDK for Google Cloud
- the AWS CLI for Amazon Web Services
- Azure support coming soon...

## GCP

To use GCP, configure the local Google Cloud SDK. It will need permissions to the project and VMs.

Role Variables
--------------

```
# The cloud provider to use. Supported versions include gcp, aws, and azure. Required
cloud_provider: gcp

# The path to use for the known_hosts file. Defaults to {{ ansible_env.HOME }}/.ssh/known_hosts.
known_hosts: ./known_hosts

## GCE Options
# The GCE project. Only required for Google Cloud.
project: operation-phoenix
```

Dependencies
------------

- The Google Cloud SDK
- The AWS SDK
- The Azure SDK

Example Playbook
----------------

An example playbook that imports the SSH keys to the current user.

```
- hosts: localhost
  connection: local
  gather_facts: yes
- roles:
    - role: cloud-ssh-public-key-scrape
      cloud: gcp
      project: my-google-project
```

License
-------

BSD

Author Information
------------------

Bill Cawthra - https://blog.billyc.io
