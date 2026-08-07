# Aula 02 - A sintaxe básica da HCL

## Objetivo 

Entender a sintaxe básica de utilização do HCL (HashiCorp Configuration Language).

---

## HCL no Terraform

- HCL equilibra legibilidade humana e interpretação por máquina no Terraform.
- Linguiagem HashiCorp Configuration Language
- Estrutura orientada a blocos
- Leitura diária de configuração

## Estrutura em blocos

- Blocos são a unidade central: tipo, labels e um corpo com configurações
```bash
tipo_do_bloco "label_tipo" "nome_local" {...}
```
- Labels para identificar o objeto
- Corpo com argumentos do recurso

# Exemplo de bloco resource

```bash
resource "aws_instance"
    "servidor_web" {
    ami = "ami-0c55b159cbfafe1f0"
    instance_type = "t2.micro"
    }
```
- Resource define o tipo do bloco: criação de um objeto
- "aws_instance" indica o recurso do provedor (AWS)
- "servidor_web" define o nome local para referência interna
- instance_type define o tipo de instancia que será criada

## Argumentos e sintaxe

- Argumentos são pares chave = valor; aspas e tipos seguem regras diretas
- Atribuição com sinal de igual =
- Strings com aspas duplas; números e bool sem aspas
- Interpolação: aws_instance.sservidor_web.id

## Tipos de dados na HCL

- Tipos básicos e coleções evitam erros e suportam configurações complexas
- String, Numer, Bool
- List: sequência ordenada com []
- Map: pares chave/valor com {}

# Exemplos: Lista e Map

```bash
cidr blocks = ["10.0.0.0/16", "192.168.1.0/24"]

tags = {
    Env = "Produção
    Time = "DevOps
}
```
- List para múltiplos valores, como cidr_blocs
- Map para configurações por chave, como tags
- Map útil para tags e variações por ambiente