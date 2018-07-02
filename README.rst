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

The role will configure Watcher, but does not provision RabbitMQ or
MariaDB.

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
        watcher_developer_mode: True
        watcher_galera_address: 10.100.102.101
        watcher_galera_database: watcher
        watcher_galera_user: watcher
        watcher_galera_password: "secrete"
        watcher_rabbitmq_port: "{{ rabbitmq_port }}"
        watcher_rabbitmq_servers: "{{ rabbitmq_servers }}"
        watcher_rabbitmq_use_ssl: "{{ rabbitmq_use_ssl }}"
        watcher_rabbitmq_password: "secrete"
        watcher_rabbitmq_userid: watcher
        watcher_rabbitmq_vhost: /watcher
        watcher_requirements_git_install_branch: master
        watcher_service_adminurl: "http://{{ internal_lb_vip_address }}:9322"
        watcher_service_password: "secrete"
        watcher_service_project_domain_id: default
        watcher_service_project_name: service
        watcher_service_region: RegionOne
        watcher_service_user_domain_id: default
        watcher_service_user_name: watcher
        watcher_bin: "/openstack/venvs/watcher-{{ watcher_venv_tag }}/bin"
        watcher_venv_tag: "testing"

Tags
====

This role supports two tags: ``watcher-install`` and ``watcher-config``.

The ``watcher-install`` tag can be used to install and upgrade.

The ``watcher-config`` tag can be used to maintain configuration of the service.

.. Change things from this point on

======================================
OpenStack-Ansible Watcher
======================================

Documentation for the project can be found at:
  https://docs.openstack.org/openstack-ansible-os_watcher/latest/

Release notes for the project can be found at:
  https://docs.openstack.org/releasenotes/openstack-ansible-os_watcher/

The project home is at:
  https://launchpad.net/openstack-ansible
