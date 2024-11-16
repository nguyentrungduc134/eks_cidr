# eks_cidr
# README: Configuring Secondary CIDR Block and Subnets for AWS VPC  

This guide explains how to configure a secondary CIDR block for your VPC, add subnets within it, and use private subnets in a node group.

## Steps  

### 1. Add a Secondary CIDR Block  
Specify the secondary CIDR block in your VPC module configuration:  
```hcl
secondary_cidr_blocks = ["10.2.0.0/16"]
```

### 2. Define Subnets (Including Secondary CIDR Block)  
Include subnets from the secondary CIDR block alongside existing private subnets:  
```hcl
private_subnets = ["10.0.1.0/24", "10.0.2.0/24", "10.2.1.0/24"]
```

### 3. Use Private Subnets in Node Group  
Point the `subnet_ids` parameter in the node group configuration to the VPC's private subnets:  
```hcl
subnet_ids = module.vpc.private_subnets
```

By following these steps, you can integrate secondary CIDR blocks into your infrastructure seamlessly.
