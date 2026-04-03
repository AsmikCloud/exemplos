# exemplos
Primeiro cenario - simulacao com cliente

🏗️ Projeto: Infraestrutura Escalável para Aplicação Web (e-Commerce ou SaaS)
Esta infraestrutura simula uma empresa que não pode parar e que precisa proteger dados sensíveis de clientes.

1. Camada de Rede (A Fundação)

VPC Personalizada: Criar uma rede /16.

Multi-AZ: Use pelo menos 2 Zonas de Disponibilidade (ex: us-east-1a e us-east-1b).

Subnets (6 no total):

2 Públicas: Para o Application Load Balancer (ALB) e NAT Gateways.

2 Privadas (App): Para as instâncias EC2 ou Containers (ECS/EKS). Sem IP público.

2 Privadas (Dados): Exclusivas para o Banco de Dados (RDS), com regras de firewall (Security Groups) que só aceitam conexão vinda da camada de App.

2. Camada de Processamento (O Coração)
Aqui você demonstra que domina automação e containers.

Auto Scaling Group (ASG): Configure instâncias que nascem e morrem sozinhas baseadas no uso de CPU.

Docker & ECS (Fargate): Em vez de gerenciar servidores puros, suba sua aplicação em containers. Isso mostra que você está alinhado com o mercado moderno.

Application Load Balancer (ALB): O único ponto de entrada da internet, distribuindo o tráfego e fazendo o Health Check (se uma instância travar, o ALB para de mandar tráfego para ela).

3. Camada de Dados e Persistência
Amazon RDS (Multi-AZ): Configure um banco MySQL ou PostgreSQL. Ative a réplica em outra zona para que, se a zona "A" cair, a zona "B" assuma em segundos.

Amazon S3: Para armazenar imagens ou arquivos estáticos da aplicação, com políticas de acesso que impedem que os arquivos fiquem expostos publicamente por erro.

4. Segurança e Governança (O Diferencial do seu Relatório)
Isso é o que você vai vender nos seus 3 meses de consultoria:

AWS WAF: Bloqueio de ataques SQL Injection e Cross-Site Scripting (XSS).

IAM Roles: Nunca use chaves Access Key / Secret Key dentro do código. Use Roles anexadas às instâncias/containers.

CloudWatch Logs & Alarms: Crie um alarme que te avise por e-mail se a fatura passar de 10 dólares (essencial para PMEs).
