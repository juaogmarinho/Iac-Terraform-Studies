# Criando seu primeiro recurso

## Objetivo 

Escrever o primeiro arquivo *.tf* e provisionar um recurso real na AWS.
```bash
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}

provider "aws" {
  region = "us-east-1"
}

resource "aws_s3_bucket" "meu_primeiro_bucket" {
  # Buckets S3 exigem nomes globais únicos.
  # Adicione números aleatórios ao final para não dar erro de "Already Exists"
  bucket = "minicurso-terraform-nome-unico-123" 
  
  tags = {
    Name        = "Meu Bucket"
    Environment = "Dev"
  }
}
```
Execução do ciclo:
```bash
    terraform init
```
Saída:
```bash
    Initializing provider plugins...
    - Finding hashicorp/aws versions matching "~> 5.0"...
    - Installing hashicorp/aws v5.100.0...
    - Installed hashicorp/aws v5.100.0 (signed by HashiCorp)

    Terraform has created a lock file .terraform.lock.hcl to record the provider
    selections it made above. Include this file in your version control repository
    so that Terraform can guarantee to make the same selections by default when
    you run "terraform init" in the future.

    Terraform has been successfully initialized!

    You may now begin working with Terraform. Try running "terraform plan" to see
    any changes that are required for your infrastructure. All Terraform commands
    should now work.

    If you ever set or change modules or backend configuration for Terraform,
    rerun this command to reinitialize your working directory. If you forget, other
    commands will detect it and remind you to do so if necessary.
```
Planejar:
```bash
    terraform plan
```
Saída:
```bash
    Plan: 1 to add, 0 to change, 0 to destroy.
```
Aplicar:
```bash
    terraform apply

    Do you want to perform these actions?
    Only 'yes' will be accepted to approve.
    
    Enter a value:

    Yes
```