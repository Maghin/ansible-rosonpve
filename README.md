rosonpve
========

Manages RancherOS virtual machine on Proxmox (pve).

Requirements
------------

This role is to be run directly on the RancherOS host as all virtual machine tasks are delegated to localhost or to the proxmox node you specify.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

RancherOS parameters
--------------------

================================  ======================================================================================================
Variable                          Description
================================  ======================================================================================================
rosonpve_ssh_authorized_keys      A list of all allowed key on host
rosonpve_hostname                 Specify hostname. Default: ``ansible_hostname``
rosonpve_docker_version           Default: ``docker-1.10.3``
rosonpve_docker_storage_engine    Default: ``overlay2``
================================  ======================================================================================================

Virtual Machine parameters
--------------------------

The virtual machine is create with one network, you can specify the pve bridge to connect it to. It has only one disk as it's assumed that volumes will be external (via NFS or other) and most of containers and images data will often be cleaned up.

========================  ==============================================================================================================
Variable                  Description
========================  ==============================================================================================================
rosonpve_vm_name          Default: ``{{ inventory_hostname }}``
rosonpve_vm_cores         Default: ``1``
rosonpve_vm_memory        Default: ``2048``
rosonpve_vm_disksize      Default: ``16``
rosonpve_vm_vga           Default: ``qxl`` (ok for spice)
rosonpve_vm_bridge        Default: ``vmbr0``
rosonpve_vm_pve_node      Specify pve node. **Mandatory**
rosonpve_vm_storage       Default: ``local-lvm``
========================  ==============================================================================================================

Network parameters
------------------

========================  ==============================================================================================================
Variable                  Description
========================  ==============================================================================================================
rosonpve_net_dhcp         Specify if dchp is enabled or not. Default: ``true``
rosonpve_net_ipv4         Specify network ipv4 adress with CIDR range. Example: ``10.0.0.11/24``
rosonpve_net_gateway      Specify network ipv4 default gateway. Example: ``10.0.0.1``
rosonpve_net_dns          Specify network ipv4 default gateway. Default: ``8.8.8.8``
========================  ==============================================================================================================

Proxmox SHK environment
-----------------------

========================  ==============================================================================================================
Variable                  Description
========================  ==============================================================================================================
pve_api_host              Default: ``localhost``
pve_api_user              Default: ``root@pam``
pve_api_pass              Specify the API password.
pve_iso_path              Default: ``/var/lib/vz/template/iso``
pve_userdata_dir          Default: ``/data``
========================  ==============================================================================================================


Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

MIT

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
