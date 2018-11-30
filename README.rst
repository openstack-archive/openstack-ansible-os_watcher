========================
Team and repository tags
========================

.. image:: https://governance.openstack.org/tc/badges/openstack-ansible-os_watcher.svg
    :target: https://governance.openstack.org/tc/reference/tags/index.html

.. Change things from this point on

OpenStack Watcher
#################

Ansible Role that installs and configures OpenStack Watcher.

This role will install the following:
    * watcher-api
    * watcher-decision-engine
    * watcher-applier

The role will configure Watcher, but does not provision messaging
backend or MariaDB.

This role is intended to work primarily with OpenStack-Ansible, but
consuming this role by setting the appropriate variables should be
possible.  See the tests/test-install-watcher.yml for example
playbook.

Default Variables
=================

.. literalinclude:: ../../defaults/main.yml
   :language: yaml
   :start-after: under the License.

Example Playbook
================

.. code-block:: yaml

    - name: Install watcher service
      hosts: watcher_all
      user: root
      roles:
        - { role: "os_watcher", tags: [ "os-watcher" ] }
      vars:
        watcher_galera_password: "secrete"
        watcher_oslomsg_rpc_password: "secrete"
        watcher_service_password: "secrete"

Tags
====

This role supports two tags: ``watcher-install`` and ``watcher-config``.

The ``watcher-install`` tag can be used to install and upgrade.

The ``watcher-config`` tag can be used to maintain configuration of the service.

.. Change things from this point on

=========================
OpenStack-Ansible Watcher
=========================

Documentation for the project can be found at:
  https://docs.openstack.org/openstack-ansible-os_watcher/latest/

Release notes for the project can be found at:
  https://docs.openstack.org/releasenotes/openstack-ansible-os_watcher/

The project source code repository is located at:
  https://git.openstack.org/cgit/openstack/openstack-ansible-os_watcher/

The project home is at:
  https://launchpad.net/openstack-ansible

The project bug tracker is located at:
 https://bugs.launchpad.net/openstack-ansible
