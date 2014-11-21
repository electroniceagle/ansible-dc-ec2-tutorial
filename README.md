ansible-dc-ec2-tutorial
=======================

This is the source code for a tutorial on using the ec2.py dynamic inventory feature.


Installing:
-----------

Install ansible and boto::

    pip install -r requirements.txt

Make sure that ec2.py is executable::

    chmod a+x ec2.py

Set AWS_ACCESS_KEY and AWS_SECRET_KEY::

    export AWS_ACCESS_KEY="***********************"
    export AWS_SECRET_KEY="***************************************"

Sanity test the ec2.py dynamic environment script::

    $ ./ec2.py --list
    {
      "_meta": {
        "hostvars": {}
      }
    }
