
---
## Usage
Usage is very simple.  There are a few required variables that must be defined on the Ansible CLI when executing:
+ dp_cluster - the cluster name of the SVM DR snapmirror destination cluster
+ dp_vserver - the destination vserver on the 'dp_cluster'
+ src_cluster - the cluster name of the SVM DR source snapmirror cluster
+ src_vserver - the matching source vserver name
+ op - one of 'break|resync'
+ ansible-playbook -i playbooks/inventory/group_vars/all/hosts -l na -e dp_cluster=<DP_CLUSTER_NAME> -e dp_vserver=<DP_VSERVER_NAME> -e src_cluster=<SRC_CLUSTER_NAME> -e src_vserver=<SRC_VSERVER_NAME> -e op=<break|resync> playbooks/site.yml


## Restrictions
+ This set of playbooks does NOT reverse replication.  It will only break and later resync from the original source to the original destination
+ These playbooks work only for SVM DR setup
+ If the destination vserver is not in the proper state for the requested operation, the playbook will fail:
  + For a break operation the dp_verser must be stopped
  + For a resync operation the dp_vserver must be started

