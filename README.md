# AWS NAT Gateway Cost Estimator & Blueprint

A blueprint and interactive cost calculator designed to model, visualize, and understand AWS NAT Gateway pricing across different VPC architectures. It breaks down monthly cloud bills precisely the way AWS meters them: gateway-hours, data processing, cross-AZ data transfer, Elastic IPs, and internet egress.

---

## Features

* **Interactive VPC Configuration:** Choose from 16+ global AWS Regions with dynamic live rate fetching.
* **Architecture Modeling:** 
  * **Single NAT Gateway:** One shared gateway in a single AZ (with automated cross-AZ tracking for multi-AZ private subnets).
  * **One per AZ:** High-availability deployment with dedicated gateways in every Availability Zone.
  * **Regional NAT Gateway:** Modern pattern billed per active AZ.
* **Live Visual Routing Diagram:** An embedded, responsive SVG schematic showing real-time data paths from private subnets through NAT gateways, internet gateways (IGW), and out to the internet.
* **Detailed Monthly Ledger:** Itemized calculations covering hourly charges, data processing, public IPv4/Elastic IP costs, round-trip cross-AZ transfers, and internet egress.

---

## Understanding the Billing Logic

### 1. NAT Gateway Hourly & Data Processing
* **Gateway-Hours:** Billed hourly for each active NAT Gateway ($/hr based on the region).
* **Data Processing:** Billed per GB for all data passing through the gateway.

### 2. Cross-AZ Data Transfer (Inter-AZ)
When using a **Single NAT Gateway** architecture across multiple Availability Zones (e.g., instances in AZ B sending traffic to a NAT Gateway in AZ A):
* AWS charges **$0.01/GB** for data moving out of an AZ and **$0.01/GB** for data moving into an AZ.
* Because network requests and responses complete a full cycle across the AZ boundary, the calculator properly accounts for a **round-trip rate of $0.02/GB** for cross-AZ traffic.

---

## Getting Started

1. Download or clone the repository containing the `NAT Gateway Calculator Fix.html` (or index.html) file.
2. Open the file directly in any modern web browser.
3. Configure your desired region, gateway architecture, AZ count, and monthly data transfer volume to see the real-time financial ledger and architecture diagram update instantly.

---

## License
Provided for planning and estimation purposes. Always verify final budgets and exact pricing against the official [AWS VPC Pricing Page](https://aws.amazon.com/vpc/pricing/).
