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