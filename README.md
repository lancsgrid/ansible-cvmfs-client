# ansible-cvmfs-client
Install and configure cvmfs on client node

Requirements
------------

Only tested on an SL 7 node.


Role Variables
------------

Currently implements variables for "/etc/cvmfs/default.local". All variables are prefixed with role name, ansible_cvmfs_client. Variables are and their defaults are:

`ansible_cvmfs_client_CVMFS_REPOSITORIES: atlas,atlas-condb,lhcb`

`ansible_cvmfs_client_CVMFS_CACHE_BASE: /scratch/var/cache/cvmfs2`

`ansible_cvmfs_client_CVMFS_QUOTA_LIMIT: 2000`

`ansible_cvmfs_client_CVMFS_HTTP_PROXY: http://squid.site:3128`

The default for `ansible_cvmfs_client_CVMFS_HTTP_PROXY` will cause and error, or the server will fail over to cern.  Please change this one.

Dependencies
------------

None.


Example Playbook
----------------
---
- hosts: cvmfs-client
  remote_user: root

  roles:
    - ansible-cvmfs-client
  vars:
    ansible_cvmfs_client_CVMFS_HTTP_PROXY: http://squid.localsite.ac.uk:3128


License
-------

GPL v3

Author Information
------------------

Created by Robin Long (GridPP)