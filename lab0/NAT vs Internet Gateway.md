# NAT vs Internet Gateway in AWS

In AWS, both NAT Gateway and Internet Gateway are used to enable instances in a Virtual Private Cloud (VPC) to access the internet, but they serve different purposes and are used in different scenarios.

### Internet Gateway
- **Purpose**: Provides a way for instances in your VPC to directly access the internet.
- **Scope**: Allows both inbound and outbound traffic.
- **Usage**: Typically associated with public subnets, where instances need to be accessible from the internet (e.g., web servers).
- **Configuration**: You attach an Internet Gateway to your VPC and then route traffic from your public subnets to it via route tables.

### NAT Gateway
- **Purpose**: Allows instances in private subnets to access the internet for outbound traffic (e.g., downloading updates, accessing APIs), but prevents inbound traffic initiated from the internet.
- **Scope**: Only outbound traffic.
- **Usage**: Used in private subnets where instances should not be directly accessible from the internet but need internet access for outbound connections (e.g., application servers, database servers).
- **Configuration**: You create a NAT Gateway in a public subnet, and then route traffic from your private subnets to it via route tables.

### Key Differences
- **Accessibility**: Internet Gateway allows both inbound and outbound traffic, making instances publicly accessible. NAT Gateway only allows outbound traffic, keeping instances private.
- **Security**: Using a NAT Gateway enhances security by ensuring that instances in private subnets are not directly accessible from the internet.
- **Subnet Association**: Internet Gateways are associated with public subnets, while NAT Gateways are used for private subnets but must be deployed in a public subnet.

### Example Scenarios
- **Internet Gateway**: If you have a web server that needs to serve content to the public, you place it in a public subnet and route traffic through an Internet Gateway.
- **NAT Gateway**: If you have an application server that needs to fetch updates or send data to an external service, but you don't want it to be publicly accessible, you place it in a private subnet and route its outbound traffic through a NAT Gateway.

In summary, use an Internet Gateway when you need direct internet access for your instances, and use a NAT Gateway when you want to provide internet access for private instances without exposing them to inbound internet traffic.
