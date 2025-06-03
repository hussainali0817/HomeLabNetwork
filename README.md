# HomeLabNetwork
Week 2 projects for Cloud Support roadmap: Home lab network setup and NextWork AWS VPC projects
## Monday, June 2, 2025: Home Lab Network Setup
- Configured home lab network: Enabled DHCP on AT&T router (IP: 192.168.1.254, range: 192.168.1.64–192.168.1.253), assigned static IPs (desktop: 192.168.1.10 via Ethernet settings, Ubuntu VM: 192.168.1.11 via /etc/netplan/01-network-manager-all.yaml in VirtualBox, Bridged Adapter, interface: enp0s3). Tested connectivity with ping (desktop to VM: 192.168.1.11, VM to desktop: 192.168.1.10), 0% packet loss after troubleshooting (enabled ICMP via Windows Defender Firewall).
- Simulated IP conflict: Changed VM IP to 192.168.1.10 (same as desktop), ping failed (Request timed out). Troubleshooted: Checked IPs with `ip addr` and `ipconfig`, identified conflict, reverted VM to 192.168.1.11, retested connectivity—successful (ping replies: 0% packet loss).
- Note: Accidentally deleted the VPC and associated resources after completing the projects. Will recreate resources tomorrow for the "Testing VPC Connectivity" project.
