# Aula 06 - Configurando um grupo de segurança

## Objetivo

Na nuvem, o tráfego é bloqueado por padrão.

Abordagem do conceito de firewall stateful na nuvem e da importância de liberar portas específicas, como 80 e 22.

### Por que security groups importam

- Tráfego é bloqueado por padrão
- Security groups controlam acesso à distância
- Firewall virtual de entrada e saída
- Controle de acessos ao servidor web
- Tráfego permitido por regra explícita

### Conceito de Security Group (Ingress e Egress)

- Security Group controla Ingress e Egress e é stateful por padrão
- Ingress: *tráfego de entrada*
- Egress: *tráfego de saída*
- Stateful: *resposta liberada automaticamente*

### Portas do servidor web no Ingress

- Servidor web típico exige liberação de portas para navegadção e administração
- 80 *(HTTP)*: acesso ao site via HTTP
- 443 *(HTTPs)*: acesso ao site via HTTPs
- 22 *(SSH)*: administração remota (opcional ao site)

### CIDR: /03 e /0

- CIDR define faixas de IP para permitir o acesso , do mais restrito ao mais amplo
- /32: um único IP específico (Ex: ["203.0.113.15/32"])
- /0: todos os IP's possíveis (0.0.0.0/0)

### Egress e associação do SG à instância

- Criar o SG não basta, é necessário associá-los ao recurso e definir saídas
- Egress comum: liberar tudo (0.0.0.0/0)
- Associação via *vpc_security_group_ids* na **EC2**
- Dependência gerenciada automaticamente no Terraform