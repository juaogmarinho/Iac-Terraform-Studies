# Provisionando uma máquina virtual

## Objetivo 

### Preparação

- Crie uma pasta para este módulo (ex: modulo-3-webserver).
- Crie o arquivo main.tf.

### Escolha da imagem (AMI)

**Para criar um servidor, o Terraform precisa saber qual sistema operacional instalar. Na AWS, isso é definido pelo ID da AMI (Amazon Machine Image).**

- Desafio: os IDs de AMI mudam conforme a região (uma AMI Ubuntu na Virgínia tem um ID diferente da mesma AMI em São Paulo).
- Solução: o ID (ex: "ami-12345") pode ser fixado ou, de forma mais avançada, podemos usar um data source para buscar a AMI mais recente automaticamente.

### Definição de recurso

- Adicione o bloco do provedor e o recurso da instância no tf.
- Utilize uma AMI (Amazon Machine Image) do Ubuntu Server.
```bash
    Acesse o console da AWS (EC2 > Launch Instance).

    Selecione o sistema "Ubuntu".

    Copie o ID da AMI listado (ex: ami-04b70...).

    Substitua o valor no seu código.

    provider "aws" {
        region = "us-east-1"
    }
    resource "aws_instance" "web_server" {
        # Substitua pelo ID da AMI do Ubuntu na sua região (verifique no console da AWS)
        ami = "ami-0c7217cdde317cfec" 
        instance_type = "t3.micro"
        tags = {
            Name = "ServidorWeb-Terraform"
        }
    }

    terraform init

    terraform validate
```
### Validação

Execute terraform init e terraform validate. O comando validate verifica se a sintaxe está correta sem precisar conectar na nuvem.