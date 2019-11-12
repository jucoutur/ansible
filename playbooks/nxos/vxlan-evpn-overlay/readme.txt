##############################################
# VXLAN EVPN L2VNI/L3VNI provisioning
# tested against: Ansible 2.7.4 / NX-OS 9.2(2)
# contact: jucoutur@cisco.com
# issued on: 2019-02-04
##############################################

1/ Update the 'hosts.yaml' file with the right IPs or hostnames (in case you use hostnames, make sure they are resolved either by having DNS entries or putting them in your /etc/hosts file)

2/ create one file per host in './host_vars/<host>.yaml'. Here you will store vars that are unique for this host (interfaces to associate to the L2VNI, BGP ASN)

3/ Make sure you put your credentials in './group_vars/nxos_vteps_cli.yaml'. Here you will store vars that are shared within the vxlan_vteps_cli group.

4/ run the playbook to create/delete L2VNIs or create/delete L3VNIs (don't forget to specify the local 'hosts.yaml' inventory file):
root@5f0d00e4ae49:~/playbooks/nxos/vxlan-evpn/provisioning# ansible-playbook -i hosts.yaml 1-create_l2vni.yaml

NB: remember you need to create a valid L3VNI/VRF before creating a L2VNI with L3 config (attached to this L3VNI/VRF)