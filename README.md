#  AWS-EMR

Analyzing Big Data with Amazon EMR

![image](https://user-images.githubusercontent.com/48589838/77052931-91a99180-69f3-11ea-83dc-e9c47f0215f7.png)

![image](https://user-images.githubusercontent.com/48589838/77053019-b0a82380-69f3-11ea-89f0-f7b8a6d2a33a.png)

![image](https://user-images.githubusercontent.com/48589838/77053034-b6056e00-69f3-11ea-82ea-5fa1bb5d14e5.png)



## Steps

### 1.Create an Amazon S3 Bucket
For more information about creating a bucket, see Create a Bucket in the Amazon Simple Storage Service Getting Started Guide. After you create the bucket, choose it from the list and then choose Create folder, replace New folder with a name that meets the requirements, and then choose Save.

### 2.Create an Amazon EC2 Key Pair
You must have an Amazon Elastic Compute Cloud (Amazon EC2) key pair to connect to the nodes in your cluster over a secure channel using the Secure Shell (SSH) protocol. If you already have a key pair that you want to use, you can skip this step. If you don't have a key pair, follow one of the following procedures depending on your operating system.

Creating Your Key Pair Using Amazon EC2 in the Amazon EC2 User Guide for Windows Instances[https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2-key-pairs.html#having-ec2-create-your-key-pair]

Creating Your Key Pair Using Amazon EC2 in the Amazon EC2 User Guide for Linux Instances. Use this procedure for Mac OS as well.[https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#having-ec2-create-your-key-pair]

### 3. Launch Your Sample Amazon EMR Cluster
Sign in to the AWS Management Console and open the Amazon EMR console at https://console.aws.amazon.com/elasticmapreduce/.

Choose Create cluster.

On the Create Cluster - Quick Options page, accept the default values except for the following fields:

Enter a Cluster name that helps you identify the cluster, for example, My First EMR Cluster.

Under Security and access, choose the EC2 key pair that you created in Create an Amazon EC2 Key Pair.

Choose Create cluster.

### 4.Allow SSH Connections to the Cluster From Your Client
To remove the inbound rule that allows public access using SSH for the ElasticMapReduce-master security group

The following procedure assumes that the ElasticMapReduce-master security group has not been edited previously. In addition, to edit security groups, you must be logged in to AWS as a root user or as an IAM principal that is allowed to manage security groups for the VPC that the cluster is in. For more information, see Changing Permissions for an IAM User and the Example Policy that allows managing EC2 security groups in the IAM User Guide.

Open the Amazon EMR console at https://console.aws.amazon.com/elasticmapreduce/.

Choose Clusters.

Choose the Name of the cluster.

Under Security and access choose the Security groups for Master link.

Edit security groups from EMR cluster status.Choose ElasticMapReduce-master from the list.

Choose Inbound, Edit.

Find the rule with the following settings and choose the x icon to delete it:

Type SSH Port22Source Custom 0.0.0.0/0 Scroll to the bottom of the list of rules and choose Add Rule.

For Type, select SSH.

This automatically enters TCP for Protocol and 22 for Port Range.

For source, select My IP.

This automatically adds the IP address of your client computer as the source address. Alternatively, you can add a range of Custom trusted client IP addresses and choose Add rule to create additional rules for other clients. In many network environments, IP addresses are allocated dynamically, so you may need to periodically edit security group rules to update the IP address of trusted clients.

Choose Save.

Optionally, choose ElasticMapReduce-slave from the list and repeat the steps above to allow SSH client access to core and task nodes from trusted clients.

### 5.Process Data By Running The Hive Script as a Step

### 6.Terminate the Cluster and Delete the Bucket


https://aws.amazon.com/getting-started/projects/analyze-big-data/
