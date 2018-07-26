This is an Ansible playbook for deploying DC/OS, iRODS, PerfSONAR and
PIVOT side-by-side across regions on Amazon Web Service (AWS) and
Google Cloud Platform (GCP).

In order to run the playbook, credentials need to be set as environment
variables on your local machine as below:

```shell
# AWS credentials
export AWS_SECRET_ACCESS_KEY=*****
export AWS_ACCESS_KEY_ID=******

# GCP credentials
export GCE_CREDENTIALS_FILE_PATH=/path/to/your/gcp-cred.json

# Turn off SSH host key checking for the Ansible playbook
export ANSIBLE_HOST_KEY_CHECKING=False
```

Playbook configurations are specified in `group_vars/all`.

The components can be optionally installed by toggling the values of the
`install` entries in the configuration file. For instance, to install
DC/OS only, the configuration looks as below:

```yaml
...
install:
    dcos: true
    irods: false
    perfsonar: false
...
```

To set up a cluster, run the `main.yml` playbook in the root directory as
below:
```shell
ansible-playbook main.yml
```

To tear down the cluster, run the `teardown.yml` playbook as below:
```shell
ansible-playbook teardown.yml
```
