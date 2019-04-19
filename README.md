Role Name
=========

This role is designed to do a baseline configuration and prep for a new docker registry server for use with an openshift install. 

Install this directory in your `roles` path under the name `disconnected-registry`

```
git clone this-git-repo roles/disconnected-registry
```

Requirements
------------

Requires a RHEL server with a valid subscription to use yum updates.
The registry server needs an internet connection to sync all the packages from the internet for use later. 
Ansible Hosts file
```
[registry]
<server>.<domain>
```

Role Variables
--------------

#### baseline_packages:
A listing of all packages to be installed via yum.

#### registryFQDN:
This is the target FQDN of the server that you wish to make a docker registry server, this should be the same as your hosts file entry can also be overridden if you don't want to modify the variables file with 
```
-e "registryFQDN=<server>.domain"
```

#### ocpVersion:
The version of OpenShift which will be installed using the newly created registry server, defaults to 3.10

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Usage
------------

This role is designed to be run against the intended target for becoming a registry server and makes use of the Red Hat Communities of Practice - OpenShift Toolkit registry, specifically the disconnected registry portion (https://github.com/redhat-cop/openshift-toolkit). The structure and layout was based upon Chris Grimm's project https://github.com/cgrimm-redhat/rhfedora


### Install both profiles
```
$ ansible-playbook disconnected-registry.yml -K
```


## Example Playbook
```
---
- hosts: registry
  become: true
  roles:
    - disconnected-registry
```

License
-------

BSD

Author Information
------------------
Phillip Kramp - pkramp@redhat.com - github.com/pekramp

