# Aula 01 - Instalação e Configuração do Terraform

## Objetivo

Aprender como instalar o Terraform e preparar o ambiente para criação de infraestrutura como código (IaC).

---

## O que é Terraform?

Terraform é uma ferramenta de Infrastructure as Code (IaC) desenvolvida pela HashiCorp que permite provisionar e gerenciar recursos de infraestrutura utilizando arquivos de configuração.

Com Terraform é possível criar recursos em provedores como:

- AWS
- Azure
- Google Cloud
- Kubernetes
- GitHub

---

## Instalação

### Windows

Download realizado através do site oficial:

https://developer.hashicorp.com/terraform/downloads

Passos:

1. Download do executável.
2. Extração do arquivo ZIP.
3. Adição do executável ao PATH do Windows.

```bash
$env:PATH=$env:PATH + "(;$pwd)"
```

### Verificação da instalação

Comando executado:

```bash
terraform --version