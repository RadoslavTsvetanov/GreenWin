# GreenWin

## About

GreenWin is a B2B cloud infrastructure platform that helps businesses reduce their carbon footprint while maintaining competitive pricing and near-zero cost abstraction. We provide intelligent tools and services that enable companies to make environmentally conscious decisions without sacrificing performance or significantly increasing operational costs.

Our platform integrates seamlessly with your existing cloud infrastructure, offering carbon-aware routing and scheduling solutions that work with the providers you already use. By making small, incremental optimizations—the "death by a thousand cuts" approach in reverse—GreenWin helps you achieve meaningful carbon reductions across your entire infrastructure.

## Features

### Green Router

The Green Router is an intelligent traffic routing service that dynamically directs requests to the most eco-friendly AWS region in real-time.

**How it works:**
- Deploys your Lambda functions across multiple AWS regions using a multi-region deployment strategy
- Lambda code storage is essentially free and won't impact your AWS bill
- Monitors real-time carbon intensity data via API to determine the greenest available region
- Automatically routes incoming requests to the region with the lowest carbon footprint at that moment
- Maintains performance while reducing environmental impact

This approach ensures your workloads run in the most sustainable location without manual intervention or infrastructure changes.

### Eco Timer

The Eco Timer is a predictive scheduling service for workloads that have flexible execution windows.

**How it works:**
- Accepts tasks with time range requirements (e.g., "complete between Thursday 1 PM and 6 PM")
- Uses a trained machine learning model to predict optimal execution timing
- Determines both the best region and the best time within that region for running your workload
- Minimizes carbon emissions by scheduling tasks during periods of low carbon intensity

**Technical Implementation:**
We implemented a PatchTST (Patch Time Series Transformer) architecture for our prediction model. This choice was driven by:
- Fast training times—crucial in a hackathon environment
- Ease of implementation and deployment
- Excellent performance on relatively linear and simple time-series data
- Comparable accuracy to more complex models for carbon intensity prediction

The model analyzes historical carbon intensity data to make informed predictions about future optimal execution windows.

---

## Architecture

The platform consists of:
- **Backend**: NestJS-based API service handling routing logic, carbon data integration, and Lambda orchestration
- **Frontend**: Next.js dashboard for monitoring and configuration
- **ML Model**: Python-based PatchTST model for carbon intensity prediction

## Getting Started

See individual component READMEs for setup instructions:
- [Backend Setup](./GreenWinBackend/README.md)
- [Frontend Setup](./GreenWinFrontend/README.md)

## Future Improvements

### Multi-Cloud Provider Support
Expand beyond AWS to support multiple cloud providers including Azure, Google Cloud Platform, and others. This will enable:
- Cross-cloud carbon optimization
- Provider preferences (e.g., "Azure only" deployments)
- Best-in-class pricing across all major cloud platforms

### Regional Preferences & Compliance
Add configurable regional constraints to meet regulatory and compliance requirements:
- Geographic restrictions (e.g., "Europe only" for GDPR compliance)
- Custom region allowlists/blocklists
- Compliance-aware routing that respects data sovereignty laws

### Regional Router Deployment
Evolve the Green Router from a centralized service to a distributed, multi-region architecture:
- Deploy router instances across all supported regions
- Reduce latency by processing routing decisions closer to the request origin
- Improve scalability and fault tolerance
- Enable faster response times while maintaining carbon-aware routing

### Green Buckets
Introduce intelligent storage management for carbon-efficient data lifecycle:
- Automatically identify and migrate stale data to eco-friendly storage tiers (AWS Glacier, Azure Archive, etc.)
- Reduce carbon footprint of long-term storage by using less resource-intensive storage options
- Configurable policies for data age, access patterns, and archival rules
- Cost savings through automatic tier optimization

---

**GreenWin** - Sustainable infrastructure, competitive pricing, zero compromises.
