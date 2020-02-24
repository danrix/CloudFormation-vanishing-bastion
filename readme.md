# CloudFormation-vanishing-bastion
A bastion host stack in AWS that is spun-up and torn-down automatically, on demand.

The project consists of 8 elements:

- A CloudFormation stack yaml file that generates:
    
    1. A public subnet within an existing VPC

    2. Route tables, routes, and associations between the newly created subnet and an existing IGW

    3. Security Groups:

        - to allow RDP
