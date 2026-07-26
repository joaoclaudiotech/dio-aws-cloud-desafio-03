# Desafio 02 - Automação de Infraestrutura com AWS CloudFormation
Repositório do segundo desafio do curso Cloud com AWS da [DIO](https://www.dio.me/). O objetivo foi entender e praticar a automação de infraestrutura como código (IaC) utilizando o AWS CloudFormation.
## O que eu aprendi

* CloudFormation: é o serviço da AWS que permite criar e gerenciar recursos de infraestrutura através de templates (código), em vez de configurá-los manualmente.
* Template: é o arquivo em YAML ou JSON que descreve os recursos que serão provisionados (EC2, VPC, Security Groups etc.).
* Stack: é o conjunto de recursos criados a partir de um template, gerenciado como uma unidade única pelo CloudFormation.
* Designer/Canvas: é a ferramenta visual do CloudFormation que mostra o diagrama da arquitetura descrita no template.

## Arquitetura
Diagrama gerado pelo Designer/Canvas do CloudFormation representando os recursos provisionados pelo template:

![Diagrama de arquitetura](./images/diagrama-canvas.png)

## O que eu fiz na prática

1. Criei uma stack no CloudFormation a partir de um template pronto

![Criação da stack](images/criacao-stack.png)

2. Visualizei o diagrama da infraestrutura no Designer/Canvas

![Designer/Canvas](images/designer-canvas.png)

3. Analisei o código do template em YAML/JSON

![Código do template](images/codigo-template.png)

4. Verifiquei os outputs da stack (ID da instância e IP público)

![Outputs da stack](images/outputs-stack.png)

## Minhas impressões
O maior desafio foi entender o motivo da falha na criação da instância EC2: o erro indicava que o tipo `t2.micro` não era mais elegível para o Free Tier na minha conta, sendo necessário trocar para `t3.micro`. Isso me mostrou como o CloudFormation lida com falhas — fazendo rollback automático dos recursos já criados para manter a stack consistente, e que uma stack em `ROLLBACK_COMPLETE` não pode ser atualizada, sendo necessário excluí-la e criar uma nova. Ficou mais claro como os parâmetros tornam o template reutilizável para diferentes cenários. Pretendo usar esse conhecimento para automatizar a criação de ambientes de teste e desenvolvimento de forma padronizada.

## Referências

* [Documentação AWS - Automatizando com AWS CloudFormation](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/Welcome.html)

Feito durante o curso Cloud com AWS da [DIO](https://www.dio.me/).