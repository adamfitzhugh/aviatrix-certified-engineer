# Aviatrix Certified Engineer Study Notes

## High Performance Encryption
- Integrated into the Transit Network solution by building high performance encryption tunnel utilising all CPU cores, achieving line rate encryption throughput

## Firenet
- Cloud native firewall solutions are unscalable as custom routes are needed to be added, plus there's no way of source-natting traffic on active-active solutions.
- Aviatrix Transit Firenet solves this by deploying firewalls in the Transit VPC. This helps utilise firewall performance and management of network elements (as it's handled by Aviatrix)
- When deploying this solution with AWS, all users need to do is attach the Transit VPC to the AWS TGW.
- This is the same within Azure, except there will be no encryption without Aviatrix Gateways in the Spoke vNets.

## FQDN Egress
- Aviatrix enables FQDN security to permit VPC traffic outbound to the internet
- Supports TCP, UDP, HTTP & HTTPS
- This model replaces NAT gateway in AWS
- Instead of creating Transit Gateways in every VPC, you can now deploy these centrally and permit all internet traffic from a centralised security VPC for example

## Public Subnet Filtering Gateway
- Provides both ingress/egress security for AWS public subnets where instances have IP addresses.
- This includes ingress filtering via GuardDuty enforcement and Egress FQDN (see above)
- When deployed, this interacts with AWS GuardDuty so the Aviatrix Controller periodically polls AWS GuardDuty to find and block malicious source IP's from attacking the public subnet - it will program in stateful firewall rules into the filtering gateway

## Site to Cloud
- Aviatrix supports connectivity between its gateways in the cloud and on-prem by utilising Site to Cloud
- Without this, IPSec tunnels are used which are not easy to configure, nor is there a centralised place for operating them
- Supports TCP, UDP and overlapping IPs

## FlightPath
- Troubleshooting tool which displays side by side network information such as security groups, ACLs, route tables and entries to help you identify connectivity issues

## CoPilot
- Monitoring tool to check out graphical views of the platform as a whole. These include topologies, performance related stats, FlowIQ (identify traffic by source IP, dest IP, source port, dest port etc)

## VPC Tracker
- Collects and helps you manage your network CIDR ranges at a central location (similar to IPAM)
- You can check which VPCs you have deployed in your infra and also check to see that if and when you need to create anymore, whether that will cause overlapping address space
- VPC Tracker auto updates once a day