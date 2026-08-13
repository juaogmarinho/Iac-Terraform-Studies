# Subindo Hello World na Nuvem

## Objetivo

Utilizar a união de EC2, security group e user data para subir um site funcional e acessá-lo via IP público.

### Código

```bash
    provider "aws" { region = "us-east-1" }
 
    # 1. Criar o Grupo de Segurança
    resource "aws_security_group" "permitir_web" {
    name        = "permitir_trafego_web"
    description = "Libera HTTP"
    
    ingress {
        from_port   = 80
        to_port     = 80
        protocol    = "tcp"
        cidr_blocks = ["0.0.0.0/0"] # Aberto para o mundo
    }
    
    egress {
        from_port   = 0
        to_port     = 0
        protocol    = "-1" # Libera tudo para saida
        cidr_blocks = ["0.0.0.0/0"]
    }
    }
    
    # 2. Criar a Instância com Script de Boot
    resource "aws_instance" "servidor" {
    ami           = "ami-04b70fa74e45c3917" # Ubuntu Server 24.04 LTS (Verifique o ID atual na AWS se falhar)
    instance_type = "t3.micro"
    
    # Vinculando o Security Group criado acima
    vpc_security_group_ids = [aws_security_group.permitir_web.id]
    
    # Script para instalar o Apache e criar a pagina
    user_data = <<-EOF
                #!/bin/bash
                apt-get update
                apt-get install -y apache2
                echo "<h1>Minicurso Terraform - Sucesso!</h1>" > /var/www/html/index.html
                systemctl enable apache2
                systemctl start apache2
                EOF
    
    tags = { Name = "ServidorWebTerraform" }
    }
    
    # 3. Output para mostrar o IP no final
    output "ip_publico" {
    value = aws_instance.servidor.public_ip
    }
```

### Teste

- Copie o IP exibido no output (Ex: 54.123.45.67)
- Cole no seu navegador. Você deve ver a mensagem *Minicurso Terraform - Sucesso!*

### Destruição

**Não esqueça: terraform destroy -auto-approve para apagar tudo.**