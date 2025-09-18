
# Preparatorio - AWS Practitioner:



## Vantagens da Computação em Nuvem

- Trocar despesa de capital (CAPEX) por despesa operacional (OPEX): pagar conforme demanda; não possuir hardware físico.
- Beneficiar-se de economias de escala massivas, resultando em preços reduzidos.
- Parar de adivinhar capacidade e escalar baseado no uso real.
- Aumentar velocidade e agilidade para lançar novos serviços.
- Parar de gastar com operação e manutenção de data centers próprios.
- Expandir globalmente em minutos, aproveitando infraestrutura global da AWS.

---

## Três Fundamentos da Precificação AWS

- **Compute (Computação):** custo pelo uso de recursos computacionais (ex: EC2, Lambda, containers).
- **Storage (Armazenamento):** custo pelo espaço utilizado para guardar dados (ex: S3, EBS).
- **Data Out (Dados de saída):** custo pela transferência de dados para fora da AWS (internet). A entrada de dados (Data In) é geralmente gratuita.

---

## Pontos para Escolha de Região AWS

- **Conformidade (compliance):** atender às leis e regulamentos locais, como a LGPD no Brasil.
- **Latência:** escolher uma região próxima dos usuários para reduzir atrasos e melhorar a experiência.
- **Preço:** custos dos serviços AWS podem variar entre regiões, influenciando o orçamento.

---

## Serviços com Escopo Global e Regionais

- **Globais:** Route 53 (DNS), IAM (gerenciamento de identidade e acesso), CloudFront (CDN), AWS WAF (firewall).
- **Regionais:** EC2 (máquinas virtuais), S3 (armazenamento), RDS (banco de dados relacional).

---

## Infraestrutura da AWS

- **Regiões:** agrupamentos geográficos com múltiplas Zonas de Disponibilidade (AZs).
- **Zonas de Disponibilidade (AZs):** data centers independentes com energia, rede e refrigeração próprios. Cada região tem pelo menos 2 AZs para garantir resiliência.
- **Edge Locations:** pontos de presença espalhados globalmente usados para acelerar a entrega de conteúdo via CDN, como no CloudFront.

---

## Modelo de Responsabilidade Compartilhada AWS

- **AWS:** responsável pela segurança da nuvem — infraestrutura física, hardware, software, rede, data centers.
- **Cliente:** responsável pela segurança na nuvem — dados, identidade, aplicações, sistemas, redes e firewalls.
- Importante para o cliente entender essa divisão para garantir compliance e segurança.

---

## Modelo Pay As You Go

- Paga-se apenas pelo uso efetivo dos recursos, sem necessidade de investimento antecipado ou contratos fixos.

---

## Modelos de Cloud Computing

- **On-premises:** infraestrutura própria no local da empresa.
- **IaaS (Infrastructure as a Service):** aluguel de recursos virtuais (ex: EC2, S3).
- **PaaS (Platform as a Service):** plataforma para desenvolver e rodar aplicações (ex: RDS, ECS).
- **SaaS (Software as a Service):** software pronto para uso (ex: Gmail, WorkSpaces).

---

## Diferença entre Tolerância a Falhas e Recuperação de Desastres

- **Tolerância a falhas:** manter o sistema funcionando mesmo quando partes falham, com redundância ativa.
- **Recuperação de desastres:** restaurar serviços após falhas severas, com possível downtime.



---

## Política de Uso Aceitável da AWS (Acceptable Use Policy - AUP)

- Define o que não é permitido na plataforma AWS. 
- Proíbe uso ilegal, ofensivo ou prejudicial.
- Proíbe ataques, invasões, spam, abuso de rede, e mensagens fraudulentas.
- Link oficial: [https://aws.amazon.com/aup/](https://aws.amazon.com/aup/)

---

## Serviços AWS e Seus Modelos de Nuvem

``` 
AWS Serviços

├── IaaS (Infraestrutura como Serviço)
│ ├── Amazon EC2
│ │ └─ Máquinas virtuais para rodar apps
│ ├── Amazon S3
│ │ └─ Armazenamento de objetos (arquivos, imagens)
│ ├── Amazon EBS
│ │ └─ Armazenamento em blocos para EC2 (tipo HD virtual)
│ ├── Amazon CloudFront
│ │ └─ CDN para distribuir conteúdo globalmente
│
├── PaaS (Plataforma como Serviço)
│ ├── Amazon RDS
│ │ └─ Banco de dados gerenciado (MySQL, PostgreSQL, etc)
│ ├── AWS Lambda
│ │ └─ Computação serverless por função (FaaS)
│ ├── Amazon ECS
│ │ └─ Orquestração de containers Docker
│ ├── Amazon DynamoDB
│ │ └─ Banco NoSQL gerenciado
│
└── SaaS (Software como Serviço)
└── Amazon WorkSpaces
└─ Desktop virtual na nuvem para usuários
```

## IAM: Usuários e Grupos
- **IAM** = Gerenciamento de Identidade e Acesso, serviço global
- A conta **root** é criada por padrão e não deve ser usada ou compartilhada
- **Usuários** são pessoas dentro da sua organização e podem ser agrupadas
- **Grupos** contêm apenas usuários, não podem conter outros grupos
- **Usuários** não precisam pertencer a um grupo, e um usuário pode pertencer a vários grupos.

### IAM: Permissões
Na AWS, usuários e grupos podem receber políticas, que são documentos no formato JSON usados para definir exatamente o que cada usuário ou grupo pode ou não fazer dentro do ambiente. Essas políticas controlam as permissões de acesso aos recursos da nuvem. Para manter a segurança e a boa prática de governança, a AWS adota o princípio do menor privilégio, que recomenda conceder apenas as permissões estritamente necessárias para que o usuário execute suas funções, evitando riscos e acessos indevidos.

## Estrutura de Políticas IAM (AWS)

Uma política IAM (Identity and Access Management) é composta por:

- **Version:** Versão da linguagem da política (sempre incluir `"2012-10-17"`)
- **Id:** Identificador opcional da política
- **Statement:** Uma ou mais declarações que definem permissões (obrigatório)

#### Estrutura de uma declaração (Statement)

Cada `Statement` pode conter os seguintes elementos:

- **Sid:** Identificador da declaração (opcional)
- **Effect:** Define se a ação será **permitida (Allow)** ou **negada (Deny)**
- **Principal:** Conta, usuário ou função (role) a quem a política se aplica
- **Action:** Lista de ações que a política permite ou nega
- **Resource:** Lista de recursos aos quais as ações se aplicam
- **Condition:** Condições sob as quais a política entra em vigor (opcional)

> Exemplo de uso: você pode criar uma política que permite a um usuário listar objetos em um bucket S3 específico, apenas se ele estiver usando autenticação MFA.


## IAM – Política de Senhas

- Senhas fortes = maior segurança para sua conta
- Na AWS, você pode configurar uma política de senhas:
  - Definir um comprimento mínimo para a senha
  - Exigir tipos específicos de caracteres:
    - Letras maiúsculas
    - Letras minúsculas
    - Números
    - Caracteres não alfanuméricos (ex: !, @, #, etc.)
  - Permitir que todos os usuários IAM alterem suas próprias senhas
  - Exigir que os usuários alterem suas senhas após um determinado tempo (expiração de senha)
  - Impedir o reuso de senhas

## Autenticação Multifator – MFA

- Os usuários têm acesso à sua conta e podem, possivelmente, alterar configurações ou excluir recursos na sua conta AWS.
- Você quer proteger sua **conta Root e usuários IAM**
- MFA = senha que **você sabe** + dispositivo de segurança que **você possui**

### Exemplo de fluxo de login com MFA:
[Usuário: Alice] + [Senha] + [MFA] => [Login bem-sucedido]

- **Principal benefício do MFA**:  
  Se uma senha for roubada ou invadida, **a conta não será comprometida**

## Como os usuários acessam a AWS?

- Para acessar a AWS, você tem três opções:
  - **AWS Management Console** (protegido por senha + MFA)
  - **AWS Command Line Interface (CLI)**: protegido por chaves de acesso
  - **AWS Software Developer Kit (SDK)**: para código, protegido por chaves de acesso




| **Forma de Acesso**      | **Proteção Padrão**                                | **Uso Típico**                           | **Riscos Principais**                                                                 | **Boas Práticas**                                                                 |
|---------------------------|----------------------------------------------------|-------------------------------------------|----------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| **AWS Management Console** | Senha + MFA (para usuários humanos)               | Acesso via navegador web (interface gráfica) | Phishing de credenciais; senhas fracas; sem MFA a conta fica vulnerável                 | Exigir MFA sempre, aplicar senhas fortes, usar SSO/Federation quando possível       |
| **AWS CLI**               | Access Key ID + Secret Access Key (arquivos locais) | Automação, scripts, administração via terminal | Chaves podem vazar em logs, repositórios ou máquinas comprometidas; sem MFA direto     | Usar **STS (credenciais temporárias)**, rotacionar chaves, nunca hardcodear, usar `aws-vault` |
| **AWS SDK**               | Access Key ID + Secret Access Key (ou IAM Role)    | Integração em código (ex.: boto3, Java SDK) | Chaves hardcoded no código ou expostas em repositórios                                 | Usar **IAM Roles** em vez de chaves fixas, credenciais temporárias, nunca expor chaves em código |


- As chaves de acesso são geradas através do Console da AWS
- Os próprios usuários gerenciam suas chaves de acesso
- **As chaves de acesso são secretas, assim como uma senha. Não compartilhe elas.**
- **Access Key ID** é equivalente a um nome de usuário
- **Secret Access Key** é equivalente a uma senha

# Exemplo (Falso) de Chaves de Acesso

> Use chaves de acesso para fazer requisições seguras via REST ou HTTP Query às APIs da AWS.  
> **Para sua proteção, nunca compartilhe suas chaves secretas com ninguém.**  
> Como boa prática, recomendamos a rotação frequente das chaves.  
> [Saiba mais](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html)

---

### Criar chave de acesso

| **Access key ID**         | **Criada**                | **Último uso** | **Status**  |
|---------------------------|---------------------------|----------------|-------------|
| AKIASK4E37PV4TU3RD6C      | 2020-05-25 15:13 UTC+0100 | N/A            | Ativa       |

---

- **Access key ID:** `AKIASK4E37PV4983d6C`
- **Secret Access Key:** `AZPN3zojWozWCndljhB0Unh8239aIbzbzO5fqqkZq`
- ⚠️ **Lembre-se:** _não compartilhe suas chaves de acesso 



---


# Recursos de IaaS, PaaS e SaaS na AWS
| **Modelo**                             | **Descrição**                                                                                                                                    | **Exemplos na AWS**                                                                                                                                                                                                                                      | **Quando usar**                                                                                                                                                 |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **IaaS (Infrastructure as a Service)** | Infraestrutura básica: servidores virtuais, armazenamento, redes e segurança. O cliente controla o sistema operacional, middleware e aplicações. | - **Amazon EC2** (servidores virtuais)  <br> - **Amazon S3** (armazenamento de objetos) <br> - **Amazon EBS** (volumes de armazenamento em bloco) <br> - **Amazon VPC** (rede virtual privada)                                                           | Quando a empresa quer **controle total da infraestrutura** e flexibilidade para configurar sistemas conforme a necessidade. Ideal para migrar sistemas legados. |
| **PaaS (Platform as a Service)**       | Plataforma para desenvolver, testar e implantar aplicações sem gerenciar servidores diretamente.                                                 | - **AWS Elastic Beanstalk** (deploy de apps sem gerenciar servidores) <br> - **AWS Lambda** (serverless functions) <br> - **Amazon RDS** (banco de dados gerenciado) <br> - **AWS Elastic Kubernetes Service (EKS)** e **ECS** (containers orquestrados) | Quando o foco é **desenvolver e escalar aplicações** rapidamente, sem se preocupar com a manutenção da infraestrutura.                                          |
| **SaaS (Software as a Service)**       | Aplicativos prontos, fornecidos como serviço, acessados via navegador ou API.                                                                    | - **Amazon Chime** (videoconferência e colaboração) <br> - **Amazon WorkMail** (e-mail corporativo) <br> - **Amazon WorkDocs** (armazenamento e colaboração de documentos)                                                                               | Quando a empresa quer **usar software pronto** sem precisar se preocupar com instalação, atualização ou gerenciamento de servidores.                            |



## AWS Wavelength
O **AWS Wavelength** incorpora serviços de computação e armazenamento da AWS em redes **5G**, fornecendo infraestrutura de **computação de borda móvel** para desenvolvimento, implantação e escalabilidade de aplicações de **latência ultrabaixa**.

---

## AWS Outposts
O **AWS Outposts** é uma família de soluções totalmente gerenciadas que fornecem infraestrutura e serviços da AWS para praticamente qualquer local da borda ou **on-premises**, proporcionando uma experiência híbrida verdadeiramente consistente.


# Modelo de Responsabilidade Compartilhada (AWS)

## Cliente (Responsabilidade pela segurança **IN** the Cloud)
- **Customer Data**
- **Platform, Applications, Identity & Access Management**
- **Operating System, Network & Firewall Configuration**
- **Client-side Data Encryption & Data Integrity Authentication**
- **Server-side Encryption (File System and/or Data)**
- **Networking Traffic Protection** (Encryption, Integrity, Identity)

---

## AWS (Responsabilidade pela segurança **OF** the Cloud)
### Software
- **Compute**
- **Storage**
- **Database**
- **Networking**

### Hardware / Infraestrutura Global
- **Regions**
- **Availability Zones**
- **Edge Locations**


# Amazon EC2 – Elastic Compute Cloud

Serviço conhecido como **Máquinas Virtuais** na AWS.  
Permite criar e gerenciar servidores virtuais (instâncias) na nuvem.  
Oferece flexibilidade para escolher o tipo de instância conforme a necessidade do projeto.


## Escalabilidade no EC2

### Tipos de Escalabilidade

- **Escalabilidade Horizontal (Scale Out / Scale In)**
  - Adição ou remoção de múltiplas instâncias EC2.
  - Permite lidar com variação de carga distribuindo em mais servidores.
  - Ex.: Auto Scaling Group + Elastic Load Balancer (ELB).

- **Escalabilidade Vertical (Scale Up / Scale Down)**
  - Aumento ou diminuição da capacidade **de uma única instância**.
  - Ex.: mudar de uma instância t2.micro para uma m5.large.
  - Simples, mas limitada ao tamanho máximo da instância disponível.



# Elastic Load Balancer (ELB)

O **ELB** é um serviço gerenciado da AWS que distribui automaticamente o tráfego entre instâncias **EC2**.  
Funciona no nível de região e é associado automaticamente a instâncias do grupo de balanceamento.

## Tipos de ELB
- **Application Load Balancer (ALB)**: ideal para aplicações web. Suporta roteamento baseado em conteúdo (Camada 7).  
- **Network Load Balancer (NLB)**: alta performance e baixa latência. Opera na Camada 4 (TCP).  
- **Gateway Load Balancer (GLB)**: encaminha tráfego para appliances de terceiros (ex.: firewalls virtuais).  

## Recursos Avançados do ELB
- Health Checks personalizados.  
- Sticky Sessions (Sessões Persistentes).  
- Roteamento baseado em regras.  
- Integração com containers (Amazon ECS e Amazon EKS).  

---

# Auto Scaling

O **Auto Scaling** ajusta automaticamente a quantidade de instâncias **EC2** com base em métricas como CPU e memória.  
Garante capacidade suficiente para lidar com a demanda, sem desperdício de recursos.  

---

# Diferença entre ELB e Auto Scaling

| **Serviço** | **Função Principal** | **Benefícios** |
|-------------|-----------------------|----------------|
| **ELB** | Distribui o tráfego entre instâncias EC2 | Balanceamento de carga, alta disponibilidade |
| **Auto Scaling** | Ajusta a quantidade de instâncias conforme a demanda | Escalabilidade automática, economia de custos |
| **Juntos** | **ELB** distribui tráfego + **Auto Scaling** adiciona/remove instâncias | Garantem disponibilidade, performance e escalabilidade automática |


---

## Tipos de Instâncias EC2
| **Tipo de Instância**            | **Características**                         | **Casos de Uso**                                |
|----------------------------------|---------------------------------------------|------------------------------------------------|
| **Gerais**                       | Equilíbrio entre CPU, memória e rede        | Aplicações comuns, servidores web, dev/teste   |
| **Otim. para Memória**           | Alta capacidade de RAM                      | Bancos de dados, caches, analytics em memória  |
| **Otim. para Armazenamento**     | Alta performance de disco (IOPS elevados)   | Data lakes, Big Data, processamento de logs    |
| **Otim. para Computação**        | Alto desempenho de CPU                      | Machine learning, simulações, processamento científico |


---

## Opções de Pagamento do Amazon EC2
| **Modelo de Pagamento**  | **Descrição**                                          | **Quando Usar**                                      |
|---------------------------|------------------------------------------------------|------------------------------------------------------|
| **On-Demand**             | Paga apenas pelo tempo de uso, sem compromisso       | Cargas imprevisíveis, testes, ambientes temporários   |
| **Reservadas**            | Compromisso de 1 ou 3 anos com desconto              | Cargas estáveis e previsíveis a longo prazo           |
| **Saving Plans**          | Economia por hora, flexível entre instâncias         | Quando quer desconto mas precisa de flexibilidade     |
| **Spot**                  | Usa capacidade ociosa com até 90% de desconto        | Tarefas tolerantes a interrupções, batch jobs, CI/CD  |
| **Hosts Dedicados**       | Servidores físicos exclusivos                        | Conformidade de licenças e requisitos regulatórios    |



# EBS – Elastic Block Store

Serviço conhecido como **armazenamento em blocos** da AWS.  
Usado geralmente com instâncias **EC2** para armazenar dados persistentes.  

---

## Tipos de Volumes EBS

- **General Purpose SSD (gp2/gp3)**  
  - Equilíbrio entre preço e performance.  
  - Usado para a maioria das aplicações comuns.  

- **Provisioned IOPS SSD (io1/io2)**  
  - Alta performance com IOPS provisionados.  
  - Indicado para bancos de dados críticos e aplicações que exigem alto throughput.  

- **Throughput Optimized HDD (st1)**  
  - Otimizado para throughput (taxa de transferência).  
  - Ideal para data lakes, Big Data e cargas de trabalho de streaming.  

- **Cold HDD (sc1)**  
  - Baixo custo para dados acessados com pouca frequência.  
  - Bom para arquivamento de longo prazo.  

---

## Características importantes do EBS
- **Persistência:** dados não se perdem quando a instância EC2 é encerrada (se configurado).  
- **Escalabilidade:** pode aumentar ou diminuir a capacidade conforme necessário.  
- **Snapshot:** backups incrementais no **Amazon S3**.  
- **Alta disponibilidade:** replicado automaticamente dentro da mesma **AZ (Availability Zone)**.  


# Armazenamento na AWS

- **HDD (Hard Disk Drive)**
  - Mais espaço, menor custo, mas mais lento.
  - Usado em volumes como **st1** (Throughput Optimized) e **sc1** (Cold HDD).

- **SSD (Solid State Drive)**
  - Mais rápido, mas com menos espaço.
  - Usado em volumes como **gp2/gp3** (General Purpose) e **io1/io2** (Provisioned IOPS).

- **Snapshots**
  - Backups incrementais de volumes EBS.
  - Armazenados no **Amazon S3**.
  - Permitem restaurar volumes ou criar **AMIs**.

- **AMI (Amazon Machine Image)**
  - Imagem usada para lançar instâncias EC2.
  - Contém SO, apps e configurações.

- **EFS (Elastic File System)**
  - Sistema de arquivos escalável e elástico baseado em NFS.
  - Compartilhado entre múltiplas instâncias EC2.
  - Ideal para aplicações que precisam de armazenamento **compartilhado**.

- **FSx (File System X)**
  - Serviço totalmente gerenciado para sistemas de arquivos de terceiros.
  - Exemplos: **FSx for Windows File Server**, **FSx for Lustre**.

- **FSx Lustre (HPC)**
  - Sistema de arquivos de alto desempenho (HPC).
  - Otimizado para workloads intensivas em computação e armazenamento, como machine learning, Big Data e HPC.

# Comparação de Serviços de Armazenamento AWS

| **Serviço** | **Tipo de Armazenamento** | **Características** | **Casos de Uso** |
|-------------|----------------------------|---------------------|------------------|
| **EBS (Elastic Block Store)** | **Bloco** (Block Storage) | Associado a uma instância **EC2**; volumes persistentes; suporta **HDD e SSD**; snapshots para backup. | Armazenamento de SO, bancos de dados, aplicações que precisam de discos persistentes. |
| **EFS (Elastic File System)** | **Arquivo** (File Storage – NFS) | Sistema de arquivos totalmente gerenciado; escalável; pode ser acessado por múltiplas instâncias EC2 ao mesmo tempo. | Aplicações que precisam de **armazenamento compartilhado**; diretórios de usuários; microsserviços. |
| **FSx for Windows File Server** | **Arquivo** (Windows FS) | Sistema de arquivos compatível com Windows (SMB, AD, NTFS); totalmente gerenciado. | Aplicações baseadas em Windows; migração de workloads on-premises para nuvem. |
| **FSx for Lustre** | **Arquivo** (High Performance) | Sistema de arquivos de **alto desempenho (HPC)**; integração com **S3**; latência baixa e throughput muito alto. | HPC, machine learning, Big Data, renderização, analytics em larga escala. |


# Banco de Dados

## Relacionais (Banco de Dados Estruturados, SQL)  
Os **bancos de dados relacionais** são ideais para aplicações que exigem consistência e integridade de **dados**.

---

## Não Relacionais (Banco de Dados Não Estruturados, NO-SQL)  
**Bancos de dados não relacionais** são mais adequados para aplicações que exigem alta escalabilidade e flexibilidade no esquema de **dados**.

---

# AWS RDS (Banco de Dados Relacional)

### Tipos de RDS AWS:
- Aurora
- MySQL
- Oracle
- Postgres
- MariaDB
- MS SQL

---

# ElastiCache (In Memory)

O Amazon ElastiCache é um serviço totalmente gerenciado, compatível com Redis e Memcache, que oferece desempenho econômico e em tempo real para aplicações modernas.  

O ElastiCache pode ser escalado para centenas de milhões de operações por segundo com tempo de resposta de microssegundos e oferece segurança e confiabilidade de nível corporativo.

---

# DynamoDB
- **NoSQL**  
- Já começa com 3 zonas de disponibilidades  
- Serverless  

---

# Glue
- **ETL (Extrair, Transformar, Carregar)**  
- Muito utilizado por Analytics  

---

# Neptune
- Muito utilizado por redes sociais que exigem grandes quantidades de links entre elas


---

# S3 – Simple Storage Service (Bucket)

* Serviço para armazenar objetos
* Paga pelo uso
* Pode ser utilizado para muitas utilidades
* Nome Único mundialmente
* Cria um endereço na Web

---

# Categorias de Armazenamento do S3

O Amazon S3 oferece diferentes classes de armazenamento para atender a variados casos de uso:

## 1. **S3 Standard**

* Alta durabilidade e disponibilidade.
* Recomendado para dados acessados frequentemente.

## 2. **S3 Intelligent-Tiering**

* Move objetos automaticamente entre camadas de acesso.
* Reduz custos sem impactar desempenho.

## 3. **S3 Standard-IA (Infrequent Access)**

* Para dados acessados com pouca frequência.
* Mais barato que o Standard, mas cobra por recuperação.

## 4. **S3 One Zone-IA**

* Armazena dados em uma única zona de disponibilidade.
* Custos menores, porém menor resiliência.

## 5. **S3 Glacier Instant Retrieval**

* Recuperação rápida de dados de arquivamento.
* Custo muito menor que o Standard.

## 6. **S3 Glacier Flexible Retrieval**

* Armazenamento de baixo custo para arquivamento.
* Recuperação em minutos a horas.

## 7. **S3 Glacier Deep Archive**

* Mais barato para armazenamento de longo prazo.
* Recuperação em até 12 horas.

## 8. **S3 Outposts**

* Oferece armazenamento S3 em ambientes on-premises.
* Ideal para requisitos de residência de dados.

---

Boa! Além das **categorias de armazenamento**, o **Amazon S3** também possui o recurso de **versionamento**, que é muito importante para controle de dados.

---

#  Versionamento no S3

O **versionamento** permite que você mantenha várias versões de um mesmo objeto dentro de um bucket. Assim, é possível recuperar, restaurar ou mesmo proteger dados contra exclusão acidental.

## Principais Características

* **Controle de versões:** cada alteração cria uma nova versão do objeto, preservando as anteriores.
* **Recuperação de dados:** é possível restaurar versões antigas em caso de perda ou corrupção.
* **Proteção contra exclusão:** quando um objeto é deletado, o S3 insere um *delete marker* (marcador de exclusão), mas as versões anteriores continuam armazenadas.
* **Integração com MFA Delete:** adiciona uma camada extra de segurança exigindo autenticação multifator para apagar versões.

## Estados do Versionamento

1. **Unversioned (padrão):** o bucket não tem versionamento habilitado.
2. **Enabled (ativado):** o S3 passa a armazenar múltiplas versões dos objetos.
3. **Suspended (suspenso):** novas versões deixam de ser criadas, mas as versões antigas continuam existindo.

## Exemplo de uso

* Um arquivo `relatorio.pdf` pode ter:

  * Versão 1: upload inicial
  * Versão 2: alterações de conteúdo
  * Versão 3: exclusão → gera *delete marker*

---

# Criptografia no S3

Quando você guarda dados no **Amazon S3**, pode querer que eles fiquem protegidos. A criptografia é como colocar um **cadeado** nos seus arquivos. Existem duas formas principais:

---

## 1. **Server Side Encryption (SSE)**

* O **próprio S3 faz a criptografia** dos dados quando eles chegam no bucket.
* Ele guarda os arquivos já trancados e, quando alguém autorizado pede acesso, o S3 usa as chaves para destrancar.
* É simples para o usuário, porque a AWS faz quase todo o trabalho.

---

## 2. **Client Side Encryption (CSE)**

* Aqui, **o usuário criptografa os dados antes de enviar para o S3**.
* O bucket só armazena os arquivos já protegidos.
* A AWS não tem acesso às chaves — apenas o usuário pode decifrar.
* Garante mais controle, mas também mais responsabilidade.

---

Em resumo:

* **SSE:** o S3 cuida da segurança para você.
* **CSE:** você mesmo cuida da segurança, e a AWS só armazena os dados já protegidos.



---

# O que é o Storage Gateway?

![Fluxo de dados do servidor local para a AWS usando o Storage Gateway.](./assets/diagrama-storage-gateway.png)

O **AWS Storage Gateway** é um serviço que conecta seu **servidor local (on-premises)** à **nuvem da AWS**. Ele serve como uma "ponte" (gateway) para mover ou sincronizar dados entre sua infraestrutura física e os serviços de armazenamento da AWS (como S3, Glacier ou EBS).

---

# Características principais

* **Migração e backup**: Permite copiar arquivos, volumes ou fitas virtuais de um servidor físico para a nuvem.
* **Híbrido**: Pode ser instalado como um **dispositivo físico** no seu datacenter ou como uma **máquina virtual** (VM).
* **Integração**: Funciona com serviços como **S3** (armazenamento de objetos), **Glacier** (arquivamento de longo prazo) e **EBS** (volumes de bloco).

---

# 🛠️ Modos de operação do Storage Gateway

1. **File Gateway**

   * Usa protocolos de arquivo (NFS/SMB).
   * Ideal para armazenar arquivos no S3 de forma simples.

2. **Volume Gateway**

   * Funciona como discos virtuais (iSCSI).
   * Permite backups automáticos no S3/EBS.

3. **Tape Gateway**

   * Emula fitas de backup físicas.
   * Permite usar soluções de backup antigas, mas armazenando na nuvem.

---
 Em resumo:
O **Storage Gateway** é como um **túnel** que liga seu datacenter à AWS, permitindo **backup, migração e integração** entre sistemas locais e a nuvem.


---

# Snow Family (Snowcone, Snowball, Snowmobile)

* **O que é?**
  Conjunto de dispositivos físicos da AWS usados para **mover grandes quantidades de dados** do seu datacenter para a nuvem.

  * **Snowcone:** pequeno, portátil (até 8TB).
  * **Snowball:** médio porte (50–80TB).
  * **Snowmobile:** um caminhão inteiro (até 100PB).

* **Quando usar?**

  * Quando você tem **muitos dados (terabytes ou petabytes)** que seriam lentos ou caros de transferir pela internet.
  * Locais com **conexão de rede limitada ou inexistente**.
  * Migração única ou periódica de grande volume de dados.

---

# Storage Gateway

* **O que é?**
  Serviço que funciona como um **"conector híbrido"** entre o seu ambiente local e a AWS. Ele não transporta fisicamente dados, mas sim faz **integração contínua pela rede**.

  * Pode expor **arquivos (File Gateway)**, **volumes (Volume Gateway)** ou **fitas virtuais (Tape Gateway)**.
  * Sincroniza e envia dados para a AWS em tempo real ou quase real.

* **Quando usar?**

  * Se você precisa de **acesso contínuo** entre sua infraestrutura local e a nuvem.
  * Para **backup, recuperação e extensão** de armazenamento local para a AWS.
  * Quando a **rede suporta** a transferência de dados de forma constante.

---

#  Resumindo a diferença

* **Snow Family:** transporte de dados em massa usando dispositivos físicos → ideal para migração inicial ou locais sem boa internet.
* **Storage Gateway:** integração em tempo real entre local e nuvem pela rede → ideal para operação híbrida e backups contínuos.

---

Um jeito fácil de lembrar:

* **Preciso mandar um caminhão de dados de uma vez só? → Snow Family**
* **Preciso conectar meu sistema local e a AWS no dia a dia? → Storage Gateway**

---


#  O que é uma VPC?
![Fluxo VPC com Subnet Publica e Subnet Privada.](./assets/diagrama-vpc.png)
A **VPC** é como se fosse a sua **rede privada dentro da nuvem da AWS**.
É um ambiente isolado onde você define **endereços IP, sub-redes, regras de roteamento e segurança** para os recursos que vai usar (como EC2, RDS, etc).

---

# Principais características

* **Isolamento**: sua VPC é separada das demais, como se fosse uma rede só sua dentro da AWS.
* **Controle de rede**: você decide quais máquinas podem se comunicar, quem pode acessar de fora e quem só fica interno.
* **Sub-redes**: você pode dividir a VPC em **subnets públicas e privadas**.

  * **Subnets públicas** → acessíveis pela internet (ex: servidores web).
  * **Subnets privadas** → não acessíveis diretamente da internet (ex: banco de dados).
* **Segurança**: usa **Security Groups** e **NACLs (Network ACLs)** para controlar tráfego de entrada e saída.
* **Integração**: pode conectar sua VPC com sua rede local via **VPN** ou **Direct Connect**.

---

# Quando usar

Você **sempre usa uma VPC** quando cria recursos de rede na AWS.

* Se você não criar, a AWS gera uma **default VPC** automaticamente.
* Se você precisa de **maior segurança e personalização**, cria sua própria VPC.

---

Em resumo:
A VPC é o **“condomínio fechado”** onde você organiza e protege os recursos da sua aplicação dentro da AWS.

---

Boa! Vamos falar sobre **NACL (Network Access Control List)** dentro da VPC da AWS 👇

---

# O que é uma NACL?

Uma **NACL** é como uma **porteira de segurança** que controla o tráfego que entra e sai de uma **subnet** na sua VPC.
Ela funciona em nível de **sub-rede (subnet)**, diferente dos **Security Groups**, que atuam em nível de instância (ex: EC2).

---

# Características principais

* **Stateless (sem estado):**

  * Isso significa que se você permitir entrada (*inbound*), não significa automaticamente que a saída (*outbound*) vai ser permitida.
  * Precisa configurar **regras de entrada e saída separadas**.

* **Regras numeradas:**

  * Cada regra tem um número (ordem de avaliação).
  * A NACL analisa as regras de cima para baixo e aplica a primeira que corresponder.

* **Permite ou nega:**

  * Você pode **permitir (ALLOW)** ou **negar (DENY)** tráfego.
  * Diferente dos Security Groups, que só permitem.

* **Aplicada por subnet:**

  * Todas as instâncias dentro da subnet associada vão herdar as regras da NACL.

---
# Exemplo de uso

* Você tem uma **subnet pública** com servidores web.

  * NACL pode permitir tráfego HTTP (porta 80) de entrada e saída.
* Você tem uma **subnet privada** com banco de dados.

  * NACL pode negar tráfego externo e só permitir acesso da subnet pública.

---

# NACL vs Security Group

| **NACL**                        | **Security Group**                        |
| ------------------------------- | ----------------------------------------- |
| Age em **subnet**               | Age em **instância**                      |
| **Stateless** (entrada ≠ saída) | **Stateful** (entrada = saída automática) |
| Permite **ALLOW** e **DENY**    | Apenas **ALLOW**                          |
| Usada para regras mais amplas   | Usada para controle fino por instância    |

---

 Resumindo:
A **NACL é a primeira camada de defesa da subnet**, funcionando como um firewall básico.
Já o **Security Group é a defesa mais próxima da instância**, permitindo regras mais específicas.


---

# O que é VPC Peering?

O **VPC Peering** é uma forma de **conectar duas VPCs** (Virtual Private Clouds) para que os recursos dentro delas consigam se comunicar **como se estivessem na mesma rede privada**.

É como se você fizesse uma “ponte” entre duas redes isoladas dentro da AWS.

---

# Características principais

* **Conexão ponto a ponto**: ligação direta entre duas VPCs.
* **Tráfego privado**: a comunicação não passa pela internet, é feita pela própria rede da AWS.
* **Região e conta**: pode ser feito entre VPCs da **mesma região** ou de **regiões diferentes**, e até entre **contas diferentes** da AWS.
* **Configuração de rotas**: é preciso atualizar as **tabelas de rotas** para que as subnets saibam como se comunicar.
* **Não suporta transição**: se a VPC A está conectada à VPC B, e a VPC B à VPC C, **A não consegue falar com C automaticamente**. Cada peering deve ser direto.

---

# Exemplos de uso

* **Organizações com múltiplas VPCs**: separar ambientes de produção, homologação e desenvolvimento, mas permitindo comunicação quando necessário.
* **Integração entre contas**: empresas diferentes que precisam compartilhar recursos (ex: uma API hospedada em outra conta).
* **Expansão regional**: conectar aplicações em VPCs de diferentes regiões.

---


 Em resumo:
O **VPC Peering** é ótimo para conectar **duas ou poucas VPCs**.


Boa! Agora vamos falar de **AWS Transit Gateway** 🚀

---

# O que é o Transit Gateway?

O **Transit Gateway (TGW)** é um serviço da AWS que funciona como um **hub central de rede**, permitindo conectar várias **VPCs**, conexões **VPN** e **Direct Connect** de forma simples e escalável.

Pensa nele como um **roteador gigante da AWS** que organiza e controla o tráfego entre diferentes redes.

---

# Principais características

* **Hub-and-Spoke**: em vez de criar vários **VPC Peerings ponto a ponto**, todas as VPCs se conectam ao Transit Gateway, que faz a comunicação entre elas.
* **Escalabilidade**: suporta milhares de VPCs.
* **Gerenciamento simplificado**: em vez de dezenas ou centenas de conexões de peering, você administra tudo em um ponto central.
* **Segurança e controle**: permite definir **tabelas de roteamento específicas** para controlar como cada rede se comunica.
* **Multi-região e multi-conta**: pode conectar VPCs em contas diferentes ou até em regiões distintas.

---

# Quando usar?

* Quando você tem **muitas VPCs** que precisam se comunicar entre si.
* Para conectar **ambientes complexos** (produção, testes, parceiros, filiais, etc.).
* Quando precisa **integrar sua rede local** (via VPN ou Direct Connect) com várias VPCs de uma só vez.
* Para **substituir a malha de VPC Peering**, que se torna inviável em larga escala.

---

# Transit Gateway vs VPC Peering

| **VPC Peering**                           | **Transit Gateway**                                |
| ----------------------------------------- | -------------------------------------------------- |
| Conexão **ponto a ponto** entre duas VPCs | Conexão centralizada em **hub-and-spoke**          |
| Simples e barato para poucas VPCs         | Escalável para centenas/milhares de VPCs           |
| Não é transitivo (A–B e B–C ≠ A–C)        | Comunicação gerenciada e controlada via roteamento |
| Difícil de administrar em larga escala    | Gerenciamento simplificado                         |

---

 Resumindo:

* **Poucas VPCs?** Use **VPC Peering**.
* **Muitas VPCs / rede híbrida complexa?** Use **Transit Gateway**.

---


# O que é um VPC Endpoint?

Um **VPC Endpoint** é uma forma de acessar serviços da AWS **de dentro da sua VPC**, **sem precisar sair para a internet pública**.
Ele cria um **atalho privado** entre a sua rede (VPC) e os serviços da AWS, usando a infraestrutura interna da Amazon.

---

# Tipos de VPC Endpoints

1. **Gateway Endpoint**

   * Usado para serviços como **Amazon S3** e **DynamoDB**.
   * É configurado como um **gateway** na tabela de rotas da VPC.
   * Tráfego nunca sai para a internet.

2. **Interface Endpoint (PrivateLink)**

   * Cria uma **interface de rede elástica (ENI)** na sua subnet.
   * Usado para a maioria dos outros serviços da AWS (ex: SSM, KMS) e também para serviços de parceiros.
   * Comunicação privada entre VPC e serviço via **PrivateLink**.

---

# Benefícios

* **Segurança**: tráfego nunca passa pela internet, reduzindo risco de ataque.
* **Desempenho**: menor latência e mais confiável, já que usa a rede privada da AWS.
* **Controle**: você pode usar **IAM Policies** e **Security Groups** para gerenciar quem acessa o quê.

---

# Exemplos de uso

* Sua aplicação dentro da VPC precisa acessar **S3** para salvar arquivos → você cria um **Gateway Endpoint para S3**.
* Sua aplicação precisa usar **AWS Systems Manager** (SSM) para gerenciar instâncias EC2 sem acesso à internet → você cria um **Interface Endpoint para o SSM**.
* Você quer acessar um serviço de terceiros integrado ao **PrivateLink** → usa um **Interface Endpoint** para esse serviço.

---

Em resumo:
O **VPC Endpoint** é como abrir uma **porta privada** para falar com os serviços da AWS, sem precisar passar pela internet.

---


Boa! Vamos falar de **VPN Site-to-Site** na AWS 👇

---

# O que é uma VPN Site-to-Site?

A **VPN Site-to-Site** (ou IPsec VPN) conecta sua rede local (datacenter, filial ou escritório) à sua **VPC na AWS** através da internet de forma **segura e criptografada**.
É como criar um **“túnel privado”** entre sua rede on-premises e a nuvem.

---

# Características principais

* **Criptografia IPsec**: protege os dados que viajam pela internet.
* **Dois túneis redundantes**: a AWS cria sempre 2 túneis para garantir alta disponibilidade.
* **Integração com VPC**: você configura a VPN a partir de um **Virtual Private Gateway** (no lado da AWS) e um **Customer Gateway** (no seu lado).
* **Roteamento**: suporta **roteamento estático** ou **dinâmico (BGP)** para manter as rotas sempre atualizadas.

---

# Quando usar

* Conectar sua rede local à AWS sem precisar de um **link dedicado** (como o AWS Direct Connect).
* Solução rápida para ambientes **híbridos** (parte on-premises, parte na nuvem).
* Ideal para **ambientes de teste, desenvolvimento ou workloads pequenos/médios**.
* Quando você quer segurança, mas não precisa da baixa latência e largura de banda do Direct Connect.

---


---

# O que é o Direct Connect?

O **AWS Direct Connect (DX)** é um serviço que cria uma **conexão de rede dedicada** (física) entre o seu datacenter, escritório ou provedor de colocation e a AWS.
É como se fosse um **“cabo exclusivo”** que liga sua rede à nuvem da Amazon.



# Principais características

* **Conexão dedicada**: não passa pela internet pública.
* **Baixa latência e alta performance**: ideal para aplicações críticas ou que movimentam muito tráfego.
* **Largura de banda previsível**: opções de 1 Gbps, 10 Gbps e até múltiplas conexões para escalar.
* **Integração com VPC**: pode ser usado junto com **VPC, Transit Gateway ou VPN**.
* **Segurança**: como não usa a internet, reduz riscos de exposição e ataques.

---

# Quando usar

* **Workloads de missão crítica** que exigem **baixa latência estável**.
* **Grandes volumes de dados** que ficariam caros e lentos via internet ou VPN.
* **Ambientes híbridos** (parte on-premises e parte em AWS).
* **Conformidade**: empresas que precisam atender requisitos de auditoria/regulatórios.

---


# VPN Site-to-Site vs Direct Connect

| **VPN Site-to-Site**               | **Direct Connect**                            |
| ---------------------------------- | --------------------------------------------- |
| Usa **internet pública**           | Usa **link dedicado**                         |
| Mais barato e rápido de configurar | Mais caro e requer instalação física          |
| Latência variável                  | Latência baixa e estável                      |
| Ideal para uso flexível ou inicial | Ideal para produção crítica com muito tráfego |

---

 Em resumo:

* **Preciso de uma conexão rápida, barata e segura para minha rede on-premises → VPN Site-to-Site.**
* **Preciso de performance estável, baixa latência e alto volume de tráfego → Direct Connect.**

---



#  O que é o PrivateLink?

O **AWS PrivateLink** é um serviço que permite acessar **serviços da AWS** (ou de parceiros, ou até os seus próprios) de forma **privada**, **sem expor o tráfego à internet pública**.

Ele funciona criando **Interface Endpoints (ENIs)** dentro da sua VPC que se conectam diretamente ao serviço desejado via a **rede interna da AWS**.

---

# Características principais

* **Tráfego privado**: comunicação feita totalmente dentro da rede da AWS, sem passar pela internet.
* **Segurança**: reduz a superfície de ataque, já que não expõe serviços a IPs públicos.
* **Simplicidade**: conecta sua VPC a serviços da AWS (S3, KMS, SSM, etc.), a serviços de terceiros ou até a serviços que você mesmo publicar.
* **Isolamento**: cada endpoint é criado como uma **ENI (Elastic Network Interface)** na sua subnet.

---

# Exemplos de uso

* Acessar **S3 ou DynamoDB** sem precisar de IP público ou NAT Gateway.
* Empresas que expõem APIs para parceiros usando PrivateLink (comunicação privada entre contas).
* Criar um **serviço interno** (como uma API) em uma VPC e permitir que outras VPCs ou contas acessem via PrivateLink.

---

# PrivateLink vs VPC Peering

| **PrivateLink**                               | **VPC Peering**                             |
| --------------------------------------------- | ------------------------------------------- |
| Conecta **serviços específicos**              | Conecta **toda a rede** (VPCs inteiras)     |
| Comunicação via **endpoint privado**          | Comunicação direta entre instâncias/subnets |
| Mais seguro e restrito (acesso só ao serviço) | Mais amplo (tudo na rede pode falar)        |
| Ideal para expor APIs/serviços privados       | Ideal para integração total entre VPCs      |

---

 Em resumo:
O **PrivateLink** é usado quando você quer **acessar serviços de forma privada e controlada**, sem abrir sua rede inteira.



---

# O que são VPC Flow Logs?

O **VPC Flow Logs** é um recurso da AWS que **captura informações sobre o tráfego de rede** que entra e sai da sua **VPC**, **subnets** ou **interfaces de rede (ENIs)**.

É como um **registro detalhado** de quem falou com quem, quando, e se o tráfego foi aceito ou negado.

---

# Características principais

* **Níveis de captura**:

  * Pode ser habilitado na **VPC inteira**, em uma **subnet específica** ou em uma **ENI (Elastic Network Interface)**.

* **Destino dos logs**:

  * **Amazon CloudWatch Logs** → para monitoramento em tempo real.
  * **Amazon S3** → para análise e arquivamento.

* **Informações capturadas**:

  * IP de origem e destino.
  * Porta de origem e destino.
  * Protocolo.
  * Ação (ACCEPT ou REJECT).
  * Bytes transferidos.

* **Não captura payload**:

  * Ele registra apenas **metadados** do tráfego, não o conteúdo da comunicação.

---

# Para que serve?

* **Segurança**: detectar acessos suspeitos ou não autorizados.
* **Auditoria**: verificar quem acessou o quê e quando.
* **Depuração**: entender problemas de conectividade entre instâncias e serviços.
* **Custos e performance**: identificar tráfego inesperado que pode impactar conta ou desempenho.

---

# Exemplo de uso

* Você suspeita que uma instância **não está recebendo conexões externas** → habilita Flow Logs na subnet e confirma se o tráfego está sendo **REJECT** por uma NACL ou Security Group.
* Uma equipe de **segurança** precisa registrar todo o tráfego para auditoria → habilita Flow Logs no nível da VPC e manda os logs para o S3.

---

 Em resumo:
O **VPC Flow Logs** é como uma **câmera de vigilância da sua rede** dentro da AWS: ele não mostra o conteúdo da conversa, mas mostra **quem falou com quem, quando e se foi permitido**.


