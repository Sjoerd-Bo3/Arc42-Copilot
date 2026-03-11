---
mode: 'ask'
description: 'Generate arc42 Chapter 7: Deployment View'
---

# Generate arc42 Chapter 7: Deployment View

I am working on arc42 architecture documentation.
Please help me write **Chapter 7: Deployment View** for `docs/arc42/arc42-template.md`.

## Context questions

Please ask me:

1. **What cloud provider or infrastructure is used?** (AWS, Azure, GCP, on-premises, hybrid)
2. **How is the system deployed?** (containers, VMs, serverless, PaaS, bare metal)
3. **What environments exist?** (production, staging, development, test)
4. **How are components mapped to infrastructure?** (which service runs where)
5. **What managed services are used?** (databases, message brokers, caches, CDNs)
6. **What are the key infrastructure differences between environments?** (scale, data, connectivity)
7. **Are there any disaster recovery or multi-region aspects?**

## Output format

Generate Markdown content ready to replace the placeholder in Chapter 7.

Structure:
- 7.1 Infrastructure Overview: A **PlantUML deployment diagram** using `node`, `rectangle`, `database`, and `cloud` elements showing nodes and deployed components
- 7.2 Environment Mapping: A table of environments and their notable characteristics

Use `plantuml` fenced code blocks. See `docs/arc42/pitstop-example.md` Chapter 7 for a reference deployment diagram.

## Tips

- Keep the diagram focused on what matters architecturally — skip boilerplate cloud infrastructure.
- Map building blocks from Chapter 5 to deployment nodes explicitly.
- Note any infrastructure decisions that constrain or enable architecture choices.
- Keep production and non-production differences visible — they matter for understanding risks.
- If using container orchestration (Kubernetes), show the cluster structure.
- This should match the actual deployment, not the ideal one.
