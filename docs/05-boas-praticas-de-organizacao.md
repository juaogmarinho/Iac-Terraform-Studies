# Aula 05 - Boas práticas de organização de arquivos

## Objetivo

Aprender a organizar, como dividir o código em *main.tf*, *variables.tf* e *outputs.tf* para manter o projeto limpo e organizado.
- main.tf: recursos principais e providers.
- variables.tf / outputs.tf: interfaces do projeto.
- terraform.tfvars: valores reais das variáveis.

#### Main.tf: Núcleo da Infraestrutura

- main.tf concentra o provider e os recursos principais do projeto.
- Recursos principais(ex: Instância EC2)
- Lógica central do provisionamento

#### Variables.tf e Outputs.tf: Contrato de entrada e saída

- Separa entradas e saídas, reduz risco e melhora a colaboração
- variables.tf: definições de variable
- outputs.tf: definições de output (IP's, URL's)
- Mudanças isoladas: menos impactos no *main.tf*

#### Terraform.tfvars: Valores e cuidado com sensíveis

- terraform.tfvars: guarda valores reais e pode conter dados sensíveis
- Atribuição de valores (ex: região = "us-east1")
- Troca de ambiente via .tfvard (dev/stage/prod)
- Não compartilhar publicamente se houver segredos