1. Create new iam user `aws-admin` and attach the administrator policy to it.

2. Login with `aws-admin`.

3. Create VPC `dev_vpc` `10.0.0.0/16` and create one public `dev_public_subnet 10.0.2.0/16` and private `dev_private_subnet 10.0.3.0/16` subnet.

4. Create a ec2 instance named `nginx_server` in public subnet and install nginx. Index page should be accessible via public dns. Also create new security group named `dev_sg` for the instances.

5. Make the IP address of ec2 static.

6. Create a ec2 instance named `bastion_host` in public subnet and `test_instance` in private subnet. Make passwordless authentication between root user of both servers. 

7. Install mysql in `test_instance` and create one sample database named `mydb`. Only MySQL and SSH port should be accessible from `bastion_host`.`bastion_host`

8. Attach EBS of `20GB` to `test_instance` and move datadir of mysql to newly attached partition.

9. Take AMI of all instances and write terraform script to spin up the above infra structure.

10. Write anisble playbook to install the applications on `nginx_server` and `test_instance`. Also update below code in my.cnf.
```
[client-test]
port    = 3306
socket  = /var/run/mysqld/mysqld.sock
```
