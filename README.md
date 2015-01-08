ansible-dc-ec2-tutorial
=======================

This is the source code for a tutorial on using the ec2.py dynamic inventory feature of Ansible.  This requires the python boto library for Amazon EC2.

WARNING: terminate_instances.yaml terminates all instances in your cloud account!  You have been warned.


Installing:
-----------

Install ansible and boto::

    pip install -r requirements.txt

Make sure that ec2.py is executable::

    chmod a+x inventory/ec2.py

Set AWS_ACCESS_KEY and AWS_SECRET_KEY for Ansible and AWS_SECRET_KEY and AWS_SECRET_ACCESS_KEY for Boto::

    export AWS_ACCESS_KEY="AK******************"
    export AWS_ACCESS_KEY_ID="AK********************"
    export AWS_SECRET_KEY="***************************************"
    export AWS_SECRET_ACCESS_KEY="*************************************"

Set the AWS default region::

    export AWS_DEFAULT_REGION='us-east-1'

Disable host key checking::

    export ANSIBLE_HOST_KEY_CHECKING=False

Sanity test the ec2.py dynamic environment script::

    $ cd inventory
    $ ./ec2.py --list
    {
      "_meta": {
        "hostvars": {}
      }
    }
    $ cd ..

    Note: The ec2.py inventory script fails silently if AWS_ACCESS_KEY_ID is not set.

Galaxy Components:
------------------

Grab some external modules from Ansible Galaxy::

    mkdir galaxy
    $ ansible-galaxy -p galaxy install jdauphant.nginx
    - downloading role 'nginx', owned by jdauphant
    - downloading role from https://github.com/jdauphant/ansible-role-nginx/archive/v1.1.1.tar.gz
    - extracting jdauphant.nginx to galaxy/jdauphant.nginx
    - jdauphant.nginx was installed successfully

    [ansible-dc-ec2-tutorial] bschott@ironman-2 ~/Source/ansible-dc-ec2-tutorial (master)
    $ ansible-galaxy -p galaxy install flmmartins.postgres
    - downloading role 'postgres', owned by flmmartins
    - downloading role from https://github.com/flmmartins/ansible-postgres/archive/master.tar.gz
    - extracting flmmartins.postgres to galaxy/flmmartins.postgres
    - flmmartins.postgres was installed successfully

Provisioning Example:
---------------------

Start the provision_instances playbook::

    $ ansible-playbook -i ./inventory provision_instances.yaml



