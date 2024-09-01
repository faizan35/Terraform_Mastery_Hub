# Terraform Mastery Hub <img src="./Img/terraform-logo.png" width="35">

## < --- In Progress --- >

### Prerequisite

- HCL Learning repo
- AWS CLI

### [1. **Introduction to Terraform**](./01-Introduction-to-Terraform.md)

- **What is Terraform?**: Understand the basics, including its purpose, how it works, and why it's used in infrastructure as code (IaC).
- **Infrastructure as Code (IaC)**: Learn the principles of IaC and why Terraform is a popular choice.
- **Terraform vs. Other IaC Tools**: Compare Terraform with other IaC tools like Ansible, CloudFormation, and Chef.

### [2. **Terraform Basics**](./02-Terraform-Basics.md)

- **Installation and Setup**: How to install and configure Terraform on different platforms.
- **Terraform CLI Commands**: Familiarize yourself with commands like `terraform init`, `terraform plan`, `terraform apply`, `terraform destroy`, and `terraform fmt`.
- **Understanding Configuration Files**: Learn the structure of Terraform configuration files, including `main.tf`, `variables.tf`, `outputs.tf`, and `terraform.tfvars`.
- **Providers**: Understand how providers work and how to configure them (AWS, Azure, GCP, etc.).

### [3. **Terraform Language Deep Dive**](./03-Terraform-Language-Deep-Dive.md)

- **Terraform Configuration Language (HCL)**: Master the HashiCorp Configuration Language (HCL), focusing on syntax, expressions, and data types.
- **Variables**: Learn how to define and use variables, including variable types, default values, and input variables.
- **Outputs**: Understand how to use outputs to pass information between modules or display useful information.
- **Data Sources**: Learn how to fetch information from other parts of your infrastructure.
- **Resource Lifecycle**: Understand the lifecycle of resources in Terraform, including `create`, `read`, `update`, and `delete` operations.

### [4. **Terraform State Management**](./04-Terraform-State-Management.md)

- **State Files**: Learn how Terraform uses state files to map real-world resources to your configuration.
- **Backend Configuration**: Understand different backend types (local, remote) and how to configure them.
- **State Locking**: Explore the concept of state locking to prevent race conditions.
- **State Management Commands**: Commands like `terraform state`, `terraform refresh`, and `terraform import`.

### [5. **Terraform Modules**](./05-Terraform-Modules.md)

- **What are Modules?**: Understand the purpose and benefits of using modules in Terraform.
- **Creating and Using Modules**: Learn how to create reusable modules, structure your code, and use existing modules from the Terraform Registry.
- **Module Versioning**: Explore how to version and manage modules.
- **Module Composition**: Understand how to organize complex infrastructure by composing multiple modules.

### [6. **Terraform Best Practices**](./06-Terraform-Best-Practices.md)

- **Code Organization**: Learn how to organize Terraform code for readability, scalability, and maintainability.
- **DRY Principle**: Understand the "Don't Repeat Yourself" principle and how to apply it in Terraform.
- **Error Handling**: Strategies for handling errors in Terraform configurations.
- **Collaborative Workflows**: Learn about Terraform Cloud, Terraform Enterprise, and other collaborative tools.

### [7. **Advanced Terraform Features**](./07-Advanced-Terraform-Features.md)

- **Terraform Workspaces**: Learn how to manage multiple environments using workspaces.
- **Loops and Conditionals**: Explore advanced HCL features like `count`, `for_each`, and `if` statements.
- **Dynamic Blocks**: Understand how to create dynamic configurations using dynamic blocks.
- **Terraform Functions**: Deep dive into built-in functions for string manipulation, math, type conversion, etc.

### [8. **Terraform with CI/CD**](./08-Terraform-with-CI-CD.md)

- **Integration with CI/CD Pipelines**: Learn how to integrate Terraform with Jenkins, GitLab CI, GitHub Actions, etc.
- **Automated Infrastructure Deployment**: Implement automated deployment pipelines using Terraform.
- **Testing Infrastructure as Code**: Learn how to test Terraform configurations using tools like `terraform validate`, `terraform plan`, and `Terratest`.

### [9. **Terraform Security**](./09-Terraform-Security.md)

- **Securing State Files**: Best practices for securing Terraform state files, especially when using remote backends.
- **IAM and Role-Based Access Control**: Learn how to manage access controls in Terraform.
- **Sensitive Data Management**: Handling sensitive information, like passwords and API keys, securely.

### [10. **Terraform in Production**](./10-Terraform-in-Production.md)

- **Scalability and Performance Optimization**: Learn how to optimize Terraform configurations for large-scale environments.
- **Disaster Recovery**: Implement strategies for disaster recovery using Terraform.
- **Drift Management**: Understand how to detect and manage drift between your Terraform configurations and the actual state of your infrastructure.
- **Debugging and Troubleshooting**: Learn how to debug and troubleshoot Terraform issues in production environments.

### 11. **Real-World Projects**

- **Create Multi-Cloud Infrastructure**: Implement projects that deploy resources across AWS, Azure, and GCP using Terraform.
- **Hybrid Cloud Deployments**: Work on projects involving on-premises and cloud infrastructure.
- **Microservices Infrastructure**: Build infrastructure to support microservices, including Kubernetes clusters.
- **Networking with Terraform**: Create and manage complex network architectures using Terraform.
- **Terraform with Monitoring Tools**: Integrate Terraform with monitoring tools like Prometheus, Grafana, etc.

### 12. **Staying Updated**

- **Terraform Releases**: Keep up with new features, deprecations, and best practices by following Terraform release notes.
- **Community and Contributions**: Engage with the Terraform community, contribute to open-source modules, and follow industry trends.

### 13. **Interview Preparation**

- **Terraform Use Cases**: Be prepared to discuss various use cases, including multi-cloud strategies, infrastructure automation, and IaC best practices.
- **Scenario-Based Questions**: Practice solving scenario-based problems where you need to design or troubleshoot Terraform configurations.
- **Hands-On Demonstrations**: Be ready to demonstrate your skills through live coding or hands-on challenges during interviews.
