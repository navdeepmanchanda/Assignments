### Task 1

> Create a vpc not by wizard this time but manually, having 2 public subnets and 2 private subnets and 2 protected subnets.

> setup should be highly available

> Create 1 IGW and 2 NGW in each availability zone and make the appropriate routes in route tables

> Main route will remain intact, instead make 4 route tables

-   public\_route\_table
-   private\_route\_table\_1
-   private\_route\_table\_2
-   protected\_route\_table

VPC

Subnets:

Route Table:

Internet Gateway:

------------------------------------------------------------------------------------------------------------------------

### Task 2

> Make LAMP setup with 2 instances in each private subnets.

> Server-1 should serve a webpage that would say "Hi! i am server 1"

> Server-2 should serve a webpage that would say "Hi! i am server 2"

copy pem files of private instance in to public instances usig scp command to access private instances.

Then, connect to private instances using their pem files.

Next, Installled LAMP server on private instances using below command:

sudo yum install apache2 php libapache2-mod-php mysql-server libapache2-mod-auth-mysql php-m

scp -i "Public\_2.pem" /home/guggu/Downloads/Private\_2.pem ec2-user@13.127.117.179:/tmp/

Accessing private instances through public Instances.

Load Balancer