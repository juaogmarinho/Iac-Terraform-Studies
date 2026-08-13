# Aula 07 - Usando user_data para instalar softwares

## Objetivo

Exemplo de como injetar script's de inicialização em Bash para instalar software's automaticamente no primeiro boot da instância

### Bootstrapping com User Data

- Automatização de instalação e configuração no primeiro boot da máquina
- Máquina recém-criada "vazia"
- Instalação automática de Apache ou Nginx
- User Data como base do bootstrapping

### O que é user_data (EC2)

- Atributo da instância para executar script único ao final do boot inicial
- Atributo user_data na instância (EC2)
- Script Bash (Linux) ou PowerShell (Windows)
- Execução única no boot inicial

## Exemplo de Script (User Data)

```bash
    #!/bin/bash

    apt-get update
    
    apt-get install -y apache2

    echo "<h1> Ola Mundo via Terraform </h1>" | sudo tee /var/www/html/index.html

    systemctl start apache2
```
- Atualização de repositórios e instalação do **Apache2**
- Criação de **index.html** via **tee** em */var/www/html/index.html*
- Inicialização do serviço com *systemctl start*

### Injetando o script no Terraform

- O Cscript pode ficar inline no recurso ou ser lido de arquivo externo
- Argumento *user_data* no recurso **aws_instance** (main.tf)
- Script inline no código Terraform
- Uso de *file("script.sh") para arquivo externo

### Troubleshooting

- Falha no script não impede criação da instância nem gera erro no Terraform
- Instância criara e em "Running" mesmo com script falhando

### Como investigar

- A verificação via SSH e logs do *cloud-init* revela a saída real do script
- Conexão via SSH na máquina
- Log: */var/log/cloud-init-output.log*
- Leitura com: *cat /var/log/cloud-init-output.log*