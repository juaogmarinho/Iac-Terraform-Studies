# Aula 03 - Recursos, Variáveis e saídas

## Objetivo

### Recursos (Resources)

Os recursos representam os componentes reais da Infraestrutura que o Terraform irá criar, modificar ou remover.

Exemplos:
- Máquina virtual
- Rede virtual
- Grupo de recursos
- Banco de dados
- Bucket de armazenamento

### Sintaxe básica

Exemplo:
```bash
    resource "<TIPO>"
        "<NOME>"{
        ...
    }
```

- Tipo: tipo do recurso disponibilizado pelo provedor
- Nome: identificador local usado dentro do terraform

Exemplo no Azure:
```bash
    resource "azurerm_resource_group"
        "rg"{
            name = "rg-producao"
            location = "Brazil South"
        }
```
Referenciando o recurso:
azurerm_resource_group.rg.name

### Variáveis

As variáveis torname o código reutilizável e flexível.

Sem variáveis:

```bash
    resource "azurerm_resource_group"
        "rg"{
            name = "rg-producao"
            location = "Brazil South"
        }
```

Com variáveis:

```bash
    varibale "resource_group_name"{
        type = string
    }

    varibale "location"{
        type = string
    }
```
Uso:
```bash
    resource "azurerm_resource_group"
        "rg"{
            name = var.resource_group_name
            localtion = var.location
        }
```
### Definindo os valores:

Valor padrão:
```bash
    varibale "location"{
        type = string
        default = "Brazil South"
    }
```

### Tipos de variáveis

String:
```bash
    variable "nome"{
        type = string
    }
```
Número:
```bash
    variable "cpu"{
        type = number
    }
```
Booleano:
```bash
    variable "habilitado"{
        type = bool
    }
```
Lista:
```bash
    variable "subnets"{
        type = lists(string)
    }
```
Exemplo:
```bash
    subnets = [
        "subnet1",
        "subnet2",
        "subnet3"
    ]
```
Mapa:
```bash
    variable "tags"{
        type = map(string)
    }
```

## Saídas (Outputs)

Os outputs exibem informações após a execução do Terraform.

São úteis para:
- Mostrar IP's criados
- Mostrar ID's de recursos
- Compartilahr dados entre módulos
- Facilitar integrações

Exemplo:
```bash
    output "resource_group_name{
        value = azure_resource_group.rg.name
    }
```
Após o terraform apply:
```bash
    Outputs:
    
    resource_grou_name = "rg-producao"
```
Exemplo exibindo o IP público:
```bash
    output "public_IP"{
        value = azurerm_public_ip.vm_ip.ip_addres
    }
```
Resultado:
```bash
    Outputs:

    public_ip = "20.100.50.10"
```
Output sensível (Para evitar exibir dados confidenciais):
```bash
    output "senha"{
        value = random_password.admin.result
        sensitive = true
    }
```