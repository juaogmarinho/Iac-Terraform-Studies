# 🚀 Terraform Infrastructure as Code Studies

Repositório criado para documentar meus estudos sobre **Infrastructure as Code (IaC)** utilizando **Terraform**, abordando desde conceitos fundamentais até a publicação de serviços em ambientes cloud.

---

## 📖 Sobre o Projeto

Este repositório reúne laboratórios, exemplos práticos e documentações desenvolvidas durante minha jornada de aprendizado em Terraform.

O objetivo é registrar a evolução dos estudos, aplicar boas práticas de Infraestrutura como Código e construir uma base sólida para provisionamento automatizado de recursos em nuvem.

---

## 🎯 Objetivos

- Compreender os conceitos de Infrastructure as Code (IaC)
- Aprender os fundamentos do Terraform
- Provisionar recursos em ambientes cloud
- Automatizar tarefas de infraestrutura
- Aplicar boas práticas de segurança
- Trabalhar com módulos reutilizáveis
- Integrar Terraform em pipelines CI/CD
- Documentar projetos e laboratórios práticos

---

## 📚 Conteúdo Estudado

### ✅ Módulo 1 – Revolução da Infraestrutura como Código

- Gestão manual de infraestrutura
- O que é IaC
- Benefícios da Infraestrutura como Código
- Principais ferramentas de mercado
- Modelo Declarativo vs Imperativo

### ✅ Módulo 2 – Primeiros Passos com Terraform

- Instalação e configuração
- Sintaxe da linguagem HCL
- Recursos, Variáveis e Outputs
- Terraform Init
- Terraform Plan
- Terraform Apply
- Terraform Destroy
- Primeiro provisionamento

### ✅ Módulo 3 – Publicando um Serviço Simples

- Provisionamento de Máquina Virtual
- Configuração de Security Groups
- User Data para automação
- Instalação automática de softwares
- Deploy de uma aplicação Hello World

### ✅ Módulo 4 – Boas Práticas e Próximos Passos

- Gerenciamento de Secrets
- Terraform State
- Remote Backend
- Estruturação com Módulos
- Integração com CI/CD
- Referências e materiais complementares

---

## 🗂 Estrutura do Repositório

```text
iac-terraform-studies/
│
├── docs/
│   ├── aula-01
│   ├── aula-02
│   ├── aula-03
│   └── aula-04
│
├── examples/
│   ├── resource-group
│   ├── virtual-machine
│   ├── hello-world
│   └── modules
│
├── .gitignore
└── README.md
```

---

## 🛠 Tecnologias Utilizadas

- Terraform
- HCL (HashiCorp Configuration Language)
- Git
- GitHub
- Azure (Labs)
- Linux

---

## 🔄 Fluxo Básico Terraform

```bash
terraform init
terraform plan
terraform apply
terraform destroy
```

### Processo

```text
Código Terraform
       ↓
terraform init
       ↓
terraform plan
       ↓
terraform apply
       ↓
Infraestrutura Criada
```

---

## 📌 Boas Práticas Aprendidas

- Nunca armazenar senhas em arquivos `.tf`
- Utilizar variáveis para dados sensíveis
- Armazenar o State remotamente
- Versionar toda a infraestrutura no Git
- Criar módulos reutilizáveis
- Automatizar deploys com CI/CD

---

## 📈 Próximos Estudos

- Azure Resource Manager
- Azure Virtual Network
- Azure Storage Account
- Azure Key Vault
- Terraform Modules Avançados
- Terraform Cloud
- GitHub Actions
- Azure DevOps Pipelines

---

## 📚 Referências

- https://developer.hashicorp.com/terraform
- https://registry.terraform.io
- https://learn.microsoft.com
- https://github.com/hashicorp/terraform

---
