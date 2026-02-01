# n8n Workflows & Nodes Monorepo

A monorepo for n8n workflows, custom nodes, and automation scripts. This repository provides a centralized location for managing your n8n workflow exports and custom TypeScript nodes.

## 📁 Repository Structure

```
n8n-workflows-nodes/
├── workflows/          # JSON exports of n8n workflows
│   └── .gitkeep
├── nodes/             # Custom TypeScript nodes for n8n
│   └── .gitkeep
└── README.md          # This file
```

## 🚀 Getting Started

### Prerequisites

- [n8n](https://n8n.io/) installed (locally or via Docker)
- Node.js 16.x or higher (for custom nodes development)
- npm or yarn package manager

## 📥 Importing Workflows

### Method 1: Import from File (Recommended)

1. Navigate to your n8n instance (e.g., `http://localhost:5678`)
2. Click on **"Workflows"** in the left sidebar
3. Click the **"Add Workflow"** button or open an existing workflow
4. Click on the **three dots menu (⋮)** in the top right corner
5. Select **"Import from File"**
6. Choose a workflow JSON file from the `workflows/` directory
7. Click **"Import"** to add the workflow to your n8n instance

### Method 2: Import from URL

If you have the workflow JSON file hosted online:

1. Open n8n and navigate to the workflow section
2. Click on **"Import from URL"**
3. Paste the URL to the JSON file
4. Click **"Import"**

### Method 3: Copy/Paste Workflow JSON

1. Open the workflow JSON file from the `workflows/` directory
2. Copy the entire contents of the JSON file
3. In n8n, click **"Import from Clipboard"**
4. Paste the JSON content
5. Click **"Import"**

## 📤 Exporting Workflows

To export your n8n workflows to this repository:

1. Open the workflow you want to export in n8n
2. Click on the **three dots menu (⋮)** in the top right corner
3. Select **"Download"**
4. Save the downloaded JSON file to the `workflows/` directory
5. Commit and push the file to this repository

**Naming Convention:** Use descriptive names for your workflow files, e.g.:
- `email-notification-workflow.json`
- `data-sync-workflow.json`
- `slack-alert-workflow.json`

## 🔧 Using Custom Nodes

### Installing Custom Nodes

Custom TypeScript nodes in the `nodes/` directory can be installed in your n8n instance:

1. **For local n8n installation:**
   ```bash
   # Navigate to your n8n custom nodes directory
   cd ~/.n8n/custom
   
   # Copy or symlink the custom node files
   cp /path/to/this/repo/nodes/* .
   
   # Restart n8n
   n8n restart
   ```

2. **For Docker installation:**
   ```bash
   # Mount the nodes directory as a volume
   docker run -it --rm \
     --name n8n \
     -p 5678:5678 \
     -v ~/.n8n:/home/node/.n8n \
     -v /path/to/this/repo/nodes:/home/node/.n8n/custom \
     n8nio/n8n
   ```

3. **For n8n cloud or managed instances:**
   - Custom nodes need to be published as npm packages
   - Refer to [n8n's documentation on community nodes](https://docs.n8n.io/integrations/creating-nodes/)

### Developing Custom Nodes

To develop custom nodes:

1. Follow the [n8n node development guide](https://docs.n8n.io/integrations/creating-nodes/)
2. Place your TypeScript node files in the `nodes/` directory
3. Each node should follow n8n's node structure:
   ```typescript
   import { INodeType, INodeTypeDescription } from 'n8n-workflow';
   
   export class YourCustomNode implements INodeType {
     description: INodeTypeDescription = {
       // Node configuration
     };
     
     async execute() {
       // Node logic
     }
   }
   ```

## 📖 Additional Resources

- [n8n Documentation](https://docs.n8n.io/)
- [n8n Community Forum](https://community.n8n.io/)
- [Creating Custom Nodes](https://docs.n8n.io/integrations/creating-nodes/)
- [n8n Workflow Templates](https://n8n.io/workflows/)

## 🤝 Contributing

To contribute workflows or custom nodes:

1. Fork this repository
2. Create a feature branch (`git checkout -b feature/new-workflow`)
3. Add your workflow JSON files to `workflows/` or custom nodes to `nodes/`
4. Commit your changes (`git commit -m 'Add new workflow'`)
5. Push to the branch (`git push origin feature/new-workflow`)
6. Open a Pull Request

## 📝 License

This repository is maintained for personal/organizational use. Please check with the repository owner for license information.

## 💡 Tips

- **Backup regularly:** Export your workflows regularly to keep this repository up to date
- **Version control:** Use meaningful commit messages when adding or updating workflows
- **Documentation:** Add comments in your workflow JSON files to explain complex logic
- **Security:** Never commit workflows containing sensitive credentials or API keys
- **Testing:** Test imported workflows in a development environment before using in production
