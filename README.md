## Set up an Open Liberty on OpenShift workshop

### Prereqs
1. Deploy a suitably sized "OpenShift 4.7 Workshop" cluster in RHPDS (others will likely work too)
1. Create file `ansible_deploy/inventory` with the following format:
    ```
    localhost

    [bastion]
    bastion.GUID.sandboxNNN.opentlc.com

    [bastion:vars]
    ansible_user=myuser
    ansible_ssh_pass=mypassword

    [all:vars]
    cluster_base_url=cluster-GUID.GUID.sandboxNNN.opentlc.com
    ansible_ssh_common_args='-o StrictHostKeyChecking=no'
    ```
1. Install Ansible dependencies on control node
   - Ansible 2.9
   - python3-openshift
   - python3-pyyaml

### Install
1. Execute:
    ```bash
    pushd ansible_deploy
    ansible-playbook site.yml
    popd
    ```
1. Password for all users (`user1` through `userNN`) for all tools should be `openshift`
1. Fill out https://etherpad-etherpad.apps.cluster-GUID.GUID.sandboxNNN.opentlc.com/p/main (not yet automated)
1. See [Workshop Guided Exercises](https://github.com/mattparko/liberty-workshop)
