# ansible-cvmfs-client
Install and configure cvmfs on client node

Requirements
------------

Tested on an SL 6 and 7 nodes.


Role Variables
------------

All variables are prefixed with role name, ansible_cvmfs_client. Variables, the config file they affect and are and their defaults are listed below:


File: default.local

`ansible_cvmfs_client_CVMFS_REPOSITORIES: atlas,atlas-condb,lhcb`

`ansible_cvmfs_client_CVMFS_CACHE_BASE: /scratch/var/cache/cvmfs2`

`ansible_cvmfs_client_CVMFS_QUOTA_LIMIT: 2000`

`ansible_cvmfs_client_CVMFS_HTTP_PROXY: http://squid.site:3128`


File: lhcb.cern.ch.local

`ansible_cvmfs_client_lhcb_CVMFS_QUOTA_LIMIT: 10000`

File: atlas.cern.ch.local

`ansible_cvmfs_client_atlas_CVMFS_QUOTA_LIMIT: 5000`


File: domain.d/cern.ch.local

`ansible_cvmfs_client_CVMFS_SERVER_URL: "http://cernvmfs.gridpp.rl.ac.uk/opt/@org@;http://cvmfs-stratum-one.cern.ch/opt/@org@;http://cvmfs.racf.bnl.gov/opt/@org@"`

`ansible_cvmfs_client_CVMFS_PUBLIC_KEY: /etc/cvmfs/keys/cern.ch/cern.ch.pub`


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