## What is Terraform?
Infrastructure as a code tool that automates the provisioning, management, and versioning of infrastructure.

Based on HCL (HashiCorp Configuration Language)
Its a human readable language used in terraform to define infrastructure resources in a clear, structured and reusable way. It acts a infrstructure blueprint.

Terraform helps in:
- codifying the infrastructure making it easier to scale and destroy using single command.
- standardizing workflow since single tool is being used to manage infrastructure.
- using the same workflows among all type of cloud services (aws, azure, on prem infra) making it platform agnostic

Benefits of terraform:
- Version control and auditibility: Every change in infrstructure is going ton be tracked in version control system. Easy rollbacks and troubleshooting.
- Automation and efficiency: Eliminating all the repititive tasks
- Scalability and flexibility: Terraform helps in scaling infras up and down simply by modifying the code.
- Collaboration: Just like developers collaborate in application development, infras teams can now collaborate on infeastructure code by makinf changes through pull requests and reviewing each other's code.
- Consistency and repeatability: Environments have lower chances of being non-identical since they are created using the same terraform codebase, reducing human errors.

## Basics of HCL
Terraform configuration Language to describe infrastructure that terraform manages.
Declarative language: Used to define infra configuration
Easy to read and write: Clean human readable syntax
Terraform Primary Interface: HCL acts as Primary interface used to create and managed infras.

Syntax of HCL:
```bash
# single-line comment
block_type "block_label" "block_label" {
  first_argument  = expression or value
  second_argument = expression or value
  third           = expression or value
}

attribute_abc = "value_1"
attribute_2   = "value_2"
```
Terraform config files will have .tf extensions.
HCL example codeblock:
```bash
# main.tf

# Retrieve the list of AZs in the current AWS region
data "aws_availability_zones" "available" {}
data "aws_region" "current" {}

# Define the VPC
resource "aws_vpc" "vpc" {
  cidr_block = var.vpc_cidr

  tags = {
    Name        = var.vpc_name
    Environment = "demo_environment"
    Terraform   = "true"
  }
}
```
Data Blocks: Used to fetch information from APIs like getting list of available AWS Availability Zones.
Resource Block: Defines a specific infra object like in this case it is VPC
Arguments: The specific settings or configurations to a resource like cidr or tags.
Here we are creating a resource block which has resouce type set to aws_vpc along with name/unique identifier as vpc
Resource type is not something self created. These are pre-defined in Providers.

Blocks:
Blocks are delineated by {} : All content within the block are areguments and values to one particular resource.
Blocks startes with a keyword: It defines what type of block it is. In this case it is a Resource Block.
Block have named values: 

