# CloudFormation-vanishing-bastion

This repo holds CloudFormation template files and related resources to generate an EC2 instance bastion host in a subnet of a VPC along with all its routes, tables, security groups, and other resources needed to spin up the stack.

**Note**: This repo holds elements referenced in the article:

[The Case of the Vanishing Bastion](https://medium.com/@rixdan/the-case-of-the-vanishing-bastion-2f6f85c3a62 "The Case of the Vanishing Bastion")

This is part of a larger project. A link to the whole repo can be found in the follow up article:

[Automating the Vanishing Bastion](https://not.ready.yet "Automating the Vanishing Bastion")



## bastion_template_base.yaml

This is the CloudFormation Template file used to build the resources mentioned.

The template has placeholders for 3 variables: {0}, {1}, and {2} which correspond to "Parameters base path", "user name", and "password". These variables are substituted with string values using a Lambda function in the full project. For testing, and to manually build this stack with CloudFormation, replace the placeholders with the appropriate strings.

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
        Id of the image used to build the EC2 instance (has to be build and configured prior to this)
- **ec2InstanceType**
        See catalog of EC2 instance types to select the most appropriate.
- **ec2KeyPair**
        Encryption key pair to be used. MUST exist and you must have access to it.
- **ec2PrivateIp**
        Private IP through which the instance can be accessed from within the VPC, if necessary.
- **ec2InternalBastionIp**
        The IP (in CIDR block format) of the "inner" host with which the "external" bastion host can communicate.

### User name and password

If used manually, substitute placeholder {1} for a username and {2} for a long, complex, password (Windows comformant).

