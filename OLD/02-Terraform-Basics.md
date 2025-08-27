### 2. **Terraform Basics**

#### **Installation and Setup**

Terraform can be installed on various platforms, including Linux, macOS, and Windows. Here’s how to install it on each:

- **Linux/macOS**:

  1. **Download the Binary**: Visit the [Terraform Downloads](https://www.terraform.io/downloads) page and download the appropriate package for your OS.
  2. **Extract the Binary**: Use the terminal to unzip the downloaded file:
     ```bash
     unzip terraform_<VERSION>_linux_amd64.zip
     ```
  3. **Move the Binary to a Directory in Your PATH**:
     ```bash
     sudo mv terraform /usr/local/bin/
     ```
  4. **Verify Installation**:
     ```bash
     terraform -v
     ```
     This command should display the installed version of Terraform.

- **Windows**:
  1. **Download the Binary**: Go to the [Terraform Downloads](https://www.terraform.io/downloads) page and download the Windows version.
  2. **Extract the Binary**: Unzip the downloaded file using an archive tool like WinRAR or 7-Zip.
  3. **Add Terraform to PATH**:
     - Right-click on ‘This PC’ and go to ‘Properties’.
     - Click on ‘Advanced system settings’ and then ‘Environment Variables’.
     - In the ‘System variables’ section, find the ‘Path’ variable, select it, and click ‘Edit’.
     - Click ‘New’ and add the path where Terraform is extracted (e.g., `C:\terraform`).
  4. **Verify Installation**:
     Open Command Prompt and type:
     ```bash
     terraform -v
     ```
     You should see the installed version of Terraform.

#### **Terraform CLI Commands**

The Terraform CLI (Command Line Interface) is your main interaction point with Terraform. Here are the most important commands:

- **`terraform init`**:
  - Initializes a Terraform configuration. It downloads the necessary provider plugins and prepares the working directory.
  - Example:
    ```bash
    terraform init
    ```
- **`terraform plan`**:

  - Creates an execution plan, showing what actions Terraform will take to achieve the desired state.
  - Example:
    ```bash
    terraform plan
    ```

- **`terraform apply`**:

  - Applies the changes required to reach the desired state of the configuration.
  - Example:
    ```bash
    terraform apply
    ```

- **`terraform destroy`**:

  - Destroys the infrastructure managed by the Terraform configuration.
  - Example:
    ```bash
    terraform destroy
    ```

- **`terraform fmt`**:
  - Formats your Terraform configuration files to follow the standard style convention.
  - Example:
    ```bash
    terraform fmt
    ```

#### **Understanding Configuration Files**

Terraform configurations are written in HashiCorp Configuration Language (HCL) and typically organized into several files:

- **`main.tf`**:

  - This is the core file where you define the primary resources and infrastructure. It usually contains provider blocks, resource definitions, and data sources.
  - Example:

    ```hcl
    provider "aws" {
      region = "us-west-2"
    }

    resource "aws_instance" "example" {
      ami           = "ami-12345678"
      instance_type = "t2.micro"
    }
    ```

- **`variables.tf`**:

  - This file is used to define input variables for your Terraform configuration. It allows you to pass dynamic values into your configuration.
  - Example:
    ```hcl
    variable "instance_type" {
      description = "Type of instance to be created"
      default     = "t2.micro"
    }
    ```

- **`outputs.tf`**:

  - Outputs are used to extract and display information from your Terraform configuration. They are useful for sharing data between modules or for display purposes after an `apply`.
  - Example:
    ```hcl
    output "instance_id" {
      value = aws_instance.example.id
    }
    ```

- **`terraform.tfvars`**:
  - This file is used to set values for the variables defined in `variables.tf`. It allows you to pass different configurations for different environments or scenarios.
  - Example:
    ```hcl
    instance_type = "t2.large"
    ```

#### **Providers**

Providers are one of the core concepts in Terraform. They are responsible for creating and managing resources on a particular platform (e.g., AWS, Azure, GCP).

- **How Providers Work**:

  - Terraform uses providers to interface with the APIs of various cloud platforms and services. Each provider knows how to manage the specific resources offered by that platform.
  - A provider is defined in your configuration using a `provider` block, which specifies the provider to use and any necessary configuration (e.g., credentials, region).

- **Configuring Providers**:

  - To use a provider, you first need to configure it in your Terraform files.
  - Example: **AWS Provider**:

    ```hcl
    provider "aws" {
      region = "us-west-2"
      access_key = "your-access-key"
      secret_key = "your-secret-key"
    }
    ```

    **Azure Provider**:

    ```hcl
    provider "azurerm" {
      features = {}
    }
    ```

    **GCP Provider**:

    ```hcl
    provider "google" {
      credentials = file("<path-to-credentials>.json")
      project     = "<your-project-id>"
      region      = "us-central1"
    }
    ```

  - **Provider Plugins**: When you run `terraform init`, Terraform downloads the necessary provider plugins, which are executable binaries that interact with the APIs of the platforms they support.

Understanding these basics of Terraform will set a solid foundation for more advanced topics and practical applications.
