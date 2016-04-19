ansible-role-dcos
=========

An ansible role that uses cloudformation to deploy a DCOS cluster.

Requirements
------------
* ansible (2.0.1.0)
* boto3 (1.3.0)


Role Variables
--------------

| variable | description | default
|----------|-------------|---------
| `vpc_id` | `the id of the vpc you intend to deploy to` | `empty` |
| `slave_instance_type` | `the ec2 instance size for your your mesos slaves/workers` | `m3.xlarge` |
| `public_slave_instance_type` | `the ec2 instance size for your public faceing slave/worker` | `m3.xlarge` |
| `master_instance_type` | `the ec2 instance size for your mesos masters` | `m3.xlarge` |
| `stack_creation_timeout` | `A resource signal set on the asg creation` | `PT45M`
| `key_name` | `Required: Specify your AWS EC2 Key Pair.` | `empty`
| `master_instance_count` `Required: Specify the number of master nodes or accept the default` | `3` |
| `public_slave_instance_count` `Required: Specify the number of public agent nodes or accept the default.` | `1` |
| `slave_instance_count` | `Required: Specify the number of private agent nodes or accept the default.` | `5` |
| `admin_location` | `Optional: Specify the IP range to whitelist for access to the admin zone. Must be a valid CIDR.` | `0.0.0.0/0` |
| `region` | `the AWS region you are deploying to.` | `us-west-2` |
| `private_subnet` | `the valid id's of the private subnets in your VPC you wish to deploy your slaves to.` | `empty` |
| `public_subnet` | `the valid id's of the public subnets in your VPC you wish to deploy your master and public slave nodes to.` | `empty` |
| `cfn_template_url` | `the s3 url where your template will be uploaded to.` | `https://s3.amazonaws.com/{{ cfn_template_bucket }}/{{ environ }}/{{dcos_tpl}}` |


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: ansible-role-dcos, vpc_id: 42, key_name: adams, private_subnet: , private_subnet: , cfn_template_bucket: douglas }

License
-------

BSD

Author Information
------------------

Adrian Herrera
