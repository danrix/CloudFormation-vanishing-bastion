# CloudFormation-vanishing-bastion

This repo holds CloudFormation template files and related resources to generate an EC2 instance bastion host in a subnet of a VPC along with all it's routes, tables, security groups, and other resources needed to spin up the set up.

**Note**: This repo holds elements referenced in the article:

[The Case of the Vanishing Bastion](https://www.medium.com "The Case of the Vanishing Bastion")

This is part of a larger project. A link to the whole repo can be found in the follow up article:

[Automating the Vanishing Bastion](https://www.medium.com "Automating the Vanishing Bastion")


###

## bastion_template_base.yaml

It the CloudFormation Template file used to build the resources mentioned.

The template has placeholders for 3 variables: {0}, {1}, and {2} which correspond to "Parameters base path", "user name", "password" which are substituted by string values using a Lambda function in the full project.

### Parameters base path

When used manually, this yaml template must include the full path to a series of AWS Parameter Store parameters in the first section of the file. These are then referenced elsewhere in the template. The parameters are:

- **vpcId**
        Id of the VPC
- **igwId**
        Id of the Internet Gateway. Assumed existing in this project. 
- **publicSubnetCIDR**
        The CIDR block to be assigned to the public subnet.
- **publicSubnetAZ**
        Availability Zone for the public subnet.
- **amiId**
        Id of the image used to build the EC2 instance (has to be built and configured prior to this)
- **ec2InstanceType**
        See catalog of EC2 instance types to select the most appropriate.
- **ec2KeyPair**
        Encryption key pair to be used. MUST exist and you must have access to it.
- **ec2PrivateIp**
        Private IP through which the instance can be accessed from within the VPC, if necessary.
- **ec2InternalBastionIp**
        The IP (in CIDR block format) of the "inner" host with which the "external" bastion host can communicate.


