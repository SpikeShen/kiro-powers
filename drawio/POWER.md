---
name: "drawio"
displayName: "Draw.io Architecture Diagrams"
description: "Create and manage AWS architecture diagrams and other technical diagrams using Draw.io. Supports programmatic diagram creation, modification, and inspection through the Draw.io MCP server."
keywords: ["drawio", "draw.io", "diagram", "architecture", "architecture-diagram", "aws-architecture", "flowchart", "network-diagram", "infrastructure-diagram", "vpc-diagram", "system-design", "technical-diagram", "diagrams.net"]
author: "custom"
---

# Draw.io Architecture Diagrams Power

This power provides programmatic control over Draw.io diagrams through the Draw.io MCP server. It's designed for creating and managing AWS architecture diagrams and other technical diagrams directly from Kiro.

## Prerequisites

1. **Node.js** (v20 or higher)
   - Check: `node --version`

2. **Draw.io MCP Browser Extension**
   - Install from your browser's web store
   - This extension enables communication between Draw.io and the MCP server

3. **Draw.io** must be open in your browser before using diagram tools

## Quick Start

Open Draw.io in your browser, then try:

```
"Create an AWS VPC architecture diagram"
"Add an EC2 instance to the diagram"
"Connect the load balancer to the web servers"
"Show me all shapes in the current diagram"
```

## Available Tools

### Diagram Inspection

- **get-selected-cell** — Get the currently selected cell with all its attributes
- **list-paged-model** — Paginated view of all cells in the diagram, supports filtering
- **get-shape-categories** — List available shape categories from the library
- **get-shapes-in-category** — List all shapes in a specific category
- **get-shape-by-name** — Find a specific shape by name

### Diagram Modification

- **add-rectangle** — Create a rectangle with custom position, size, text, and style
- **add-cell-of-shape** — Add a cell of a specific shape type from the library (e.g., AWS icons)
- **add-edge** — Create a connection between two cells
- **edit-cell** — Update an existing cell's properties (text, position, size, style)
- **edit-edge** — Update an existing edge (label, source, target, style)
- **set-cell-shape** — Apply a library shape's style to an existing cell
- **delete-cell-by-id** — Remove a cell from the diagram

## AWS Architecture Diagram Workflow

When creating AWS architecture diagrams, follow this approach:

### Step 1: Discover Available AWS Shapes
Use `get-shape-categories` to find AWS-related categories, then `get-shapes-in-category` to browse available AWS icons (EC2, S3, Lambda, VPC, etc.).

### Step 2: Plan the Layout
Before adding shapes, plan the layout:
- VPC boundaries as large rectangles
- Availability Zones as nested regions
- Subnets grouped logically (public/private)
- Services placed within their respective subnets

### Step 3: Add Components
Use `add-cell-of-shape` for AWS service icons and `add-rectangle` for grouping elements like VPCs and subnets. Position elements with x/y coordinates for clean alignment.

### Step 4: Connect Components
Use `add-edge` to draw connections between services. Add labels to edges to describe traffic flow or protocols.

### Step 5: Review and Refine
Use `list-paged-model` to inspect the full diagram structure. Use `edit-cell` and `edit-edge` to adjust positions, labels, and styles.

## Style Tips

- Use consistent colors for different tiers (e.g., blue for compute, green for storage, orange for networking)
- Add text labels to all components for clarity
- Group related services within boundary rectangles
- Use dashed lines for optional or async connections
- Keep the layout left-to-right or top-to-bottom for readability

## Common Patterns

### VPC with Public/Private Subnets
```
1. Create VPC boundary rectangle
2. Add public subnet and private subnet rectangles inside
3. Place ALB/NLB in public subnet
4. Place EC2/ECS/Lambda in private subnet
5. Add NAT Gateway in public subnet
6. Connect with edges showing traffic flow
```

### Serverless Architecture
```
1. Add API Gateway
2. Add Lambda functions
3. Add DynamoDB / S3 / other services
4. Connect with edges showing event flow
5. Add CloudWatch for monitoring
```

### Microservices Architecture
```
1. Add ALB at the entry point
2. Add ECS/EKS services
3. Add RDS/DynamoDB for data layer
4. Add SQS/SNS for async communication
5. Connect services with labeled edges
```
