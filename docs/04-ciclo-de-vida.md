## Aula 04 - Ciclo de vida: init, plan, apply, destroy

## Objetivo

Entender o ciclo de vida do Terraform, ele mostra como o Terraform sai do código e chega à Infraestrutura real.

### Visão geral do ciclo

Escrever o código -> terraform init -> terraform plan -> terraform apply -> Infraestrutura criada

Quando necessário: terraform destroy - Infraestrutura removida

### Terraform Init

O comando **initi** inicializa o projeto Terraform.

É sempre o **primeiro comando** executado em um novo diretório Terraform.

#### O que ele faz?

- Baixa os providers necessários (Azure, AWS, GPC e etc.)
- Configura o backend do estado (State)
- Cria a pasta *.Terraform*
- Baixa Módulos externos

Exemplo:
```bash
    Initializing the backend...

    Initializing provider plugins...

    Terraform has been successfully initialized!
```
#### Quando executar?
- Ao criar um projeto novo
- Após alterar providers
- Após alterar a configuração do backend
- Após baixar um projeto Terraform existente

### Terraform Plan

O comando **plan** faz uma simulação.

Ele compara: **Código Terraform X Infraestrutura Atual** e mostra exatamente o que será alterado.

Exemplo:
```bash
    Símbolo
    +Criar recurso
    ~Alterar recurso
    -Remover recurso
    -/+Recriar recurso

    + criar VM
    ~ alterar tamanho da VM
    - remover Storage Account
```
Boa prática: Sempre execute **terraform plan** antes de **terraform apply** para evitar mudanças inesperadas.

### Terraform Apply

O comando **apply** executa efetivamente as mudanças.

É aqui que a Infraestrutura é criada, modificada ou removida.

Exemplo:
```bash
    terraform apply
```
O Terraform exibirá algo semelhante a:
```bash
    Plan: 2 to add, 0 to change, 0 to destroy.

    Do you want to perform these actions?
```
Digite:
```bash
    yes
```
Exemplo prático:
```bash
    resource "azurerm_resource_group"
        "rg"{
            name = "rg-treinamento"
            location = "Brazil South"
        }
```
Fluxo:
```bash
    terraform init
    terraform plan
    terraform apply
```
Resultado:
```bash
    Resource Group criado no Azure
```

### Terraform Destroy

Remove todos os rescursos gerenciados pelo Terraform.

Exemplo:
```bash
    terraform destroy
```
Saída:
```bash
    Terraform will perform the following actions:

    - destroy

    Plan: 0 to add, 0 to change, 1 to destroy;
```
Confirmação:
```bash
    Do you really want to destroy all resources?
```
Digite:
```bash
    yes
```

### Como o Terraform sabe o que mudou?

Através do **Terraform State** (terraform.tfstate)

O State guarda informações sobre:
- Recursos criados
- ID's dos recursos
- Configurações aplicadas
- Relacionamentos entre recursos

Exemplo:
```bash
    terraform.tfstate

    {
        "resources": [
            {
            "type" = "azurerm_resource_group",
            "name" = "rg"
            }
        ]
    }
```
Quando executa:
```bash
    terraform plan
```
O Terraform compara:
```bash
    Código atual
        vs
    terraform.tfstate
        vs
    Infraestrutura Real
```
e identifica as mudanças necessárias.

### Resumo para entrevistas

**terraform init**
inicializa o projeto e baixa providers/módulos.
**terraform plan**
simula e mostra as mudanças que serão realizadas.
**terraform apply**
executa as mudanças e cria/altera recursos.
**terraform destroy**
remove os recursos gerenciados pelo Terraform.
**terraform.tfstate**
arquivo que mantém o estado da infraestrutura para que o Terraform saiba o que já existe.