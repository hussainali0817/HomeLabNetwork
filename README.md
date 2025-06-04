# HomeLabNetwork
Week 2 projects for Cloud Support roadmap: Home lab network setup and NextWork AWS VPC projects
## Monday, June 2, 2025: Home Lab Network Setup
- Configured home lab network: Enabled DHCP on AT&T router (IP: 192.168.1.254, range: 192.168.1.64–192.168.1.253), assigned static IPs (desktop: 192.168.1.10 via Ethernet settings, Ubuntu VM: 192.168.1.11 via /etc/netplan/01-network-manager-all.yaml in VirtualBox, Bridged Adapter, interface: enp0s3). Tested connectivity with ping (desktop to VM: 192.168.1.11, VM to desktop: 192.168.1.10), 0% packet loss after troubleshooting (enabled ICMP via Windows Defender Firewall).
- Simulated IP conflict: Changed VM IP to 192.168.1.10 (same as desktop), ping failed (Request timed out). Troubleshooted: Checked IPs with `ip addr` and `ipconfig`, identified conflict, reverted VM to 192.168.1.11, retested connectivity—successful (ping replies: 0% packet loss).
- Note: Accidentally deleted the VPC and associated resources after completing the projects. Will recreate resources tomorrow for the "Testing VPC Connectivity" project.
## Tuesday, June 3, 2025: NextWork VPC Projects – Parts 0, 1, & 2
- Completed NextWork "AWS Networks Intro" project: Quick read-through, learned key concepts (e.g., VPC: virtual network in AWS, Subnet: smaller network within a VPC).
- Completed NextWork "Build a Virtual Private Cloud (VPC)" project: Created a VPC (name: NextWork VPC, CIDR: 10.0.0.0/16, VPC ID: [vpc-id]), created a public subnet (name: Public 1, CIDR: 10.0.0.0/24, Subnet ID: [subnet-id], Availability Zone: [e.g., us-east-1a], enabled auto-assign public IPv4 address), created and attached an internet gateway (name: NextWork IG, ID: [igw-id]).
- Completed NextWork "VPC Traffic Flow and Security" project: Created a route table (name: NextWork route table, ID: [rtb-id], added route to NextWork IG), created a security group (name: NextWork Security Group, ID: [sg-id], allowed HTTP port 80 from Anywhere-IPv4), created a network ACL (name: NextWork Network ACL, ID: [acl-id], allowed all traffic inbound/outbound, associated with Public 1).
## Wednesday, June 4, 2025: NextWork VPC Projects – Part 2 (Completion)
- Recreated NextWork VPC (after accidental deletion), including public/private subnets, internet gateway, route tables, NACLs, security groups.
- Launched two EC2 instances: NextWork Public Server (public subnet) and NextWork Private Server (private subnet).
- Tested connectivity: Connected to public EC2 via EC2 Instance Connect, pinged private EC2 (IP: 10.0.1.247), pinged internet (8.8.8.8).
- Troubleshooted EC2 Instance Connect failure by adding temporary SSH rule, allowed ICMP in private NACL for ping test.
- Cleaned up resources: Deleted network interfaces, VPC, and verified removal.
- Note: Screenshots below are from Tuesday (before VPC rebuild), so IDs differ from today’s setup.
- Screenshots:
  - EC2 Instance Connect terminal: ![EC2 Connect](NextWork-Public-EC2-Connect.png)
  - Ping to private EC2: ![Ping Private](NextWork-Ping-Private-EC2.png)
  - Ping to internet: ![Ping Internet](NextWork-Ping-Internet.png)
  - Public Security Group rules: ![Public SG Rules](NextWork-Public-SG-Rules.png)
  - Private NACL rules: ![Private NACL Rules](NextWork-Private-NACL-Rules.png)
