This is a description of the files in this folder:

- .inventory.txt: local inventory file for jenkins-related hosts

- ansible.cfg: local ansible configuration file, to override some of the
               default configurations.

- files: repository of files that need to be copied to jenkins hosts [NOT COMM]
  - jdk-8u144-linux-x64.rpm: JDK 8 installer for RedHat-like hosts
  - jdk-8u144-linux-x64.tar.gz: JDK 8 installer for non-RedHat hosts

- hardening_config.yml: playbook to apply to all hosts some of the security
                        best practices, like
    - disable SSH root access
    - disable SSH password auth
    - enable SSH key auth

- jenkins_master.yml: playbook to configure the jenkins-master node according
                      to requirements (ie. install packages and tools, like
                      Java 8)

- yum_update_all.yml: playbook to apply all Yum updates to all target hosts
                      (it does not reboot the targets, yet!)


Dependencies:

- .inventory.txt: local inventory file for this set of playbooks

- files: folder containing the files that are needed for software installs, etc
         I will not commit these files for the time being, to avoid using up
         too much space on Github

- /etc/hosts: system file, needs to be configured with the IP addresses of the
              hosts from the inventory file

- /home/cloudusr/.ssh/jenkins_rscloud_rsa: SSH private key of the user that
              Ansible uses to connect to remote hosts

- remote user "cloudusr" needs to exist, be configured to accept the correct
      SSH key and have passwordless sudo access to all remote systems, or
      Ansible will fail to connect
