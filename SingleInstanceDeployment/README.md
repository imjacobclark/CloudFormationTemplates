# Single instance deployment
Creates a private VPC, Subnet, Internet Gateway, Route table, routes and a single instance fronted by a load balancer.

###### VPC
* 10.0.0.0/16 (65536 addresses)

###### Subnet
* Single subnet within above VPC
* 10.0.1.0/24 (256 addresses)
* Gives instances in this subnet public IPv4 when launched

###### Internet (Default) Gateway
* Attached to the VPC

###### Route table
* Routing the public internet to the internet (default) gateway (0.0.0.0/0)
###### Security Group/Firewall
* Allows 80 into instances within the VPC
* Allows no outbound traffic from instances within the VPC

###### Instance
* t2.nano Ubuntu 16.10 instance
* Runs user-data to bring up a sample Docker container on port 80
* Above security group attached

###### Elastic Load Balancer
* Fronts a single instance
* Routes port 80 fom the public internet to port 80 on the instance
* Default security group as above
* Default subnet as above
* Checks port 80 for instance health
* Above security group attached
