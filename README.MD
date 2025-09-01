
# Preparatorio - AWS Practitioner:



## 1. Vantagens da Computação em Nuvem

- Trocar despesa de capital (CAPEX) por despesa operacional (OPEX): pagar conforme demanda; não possuir hardware físico.
- Beneficiar-se de economias de escala massivas, resultando em preços reduzidos.
- Parar de adivinhar capacidade e escalar baseado no uso real.
- Aumentar velocidade e agilidade para lançar novos serviços.
- Parar de gastar com operação e manutenção de data centers próprios.
- Expandir globalmente em minutos, aproveitando infraestrutura global da AWS.

---

## 2. Três Fundamentos da Precificação AWS

- **Compute (Computação):** custo pelo uso de recursos computacionais (ex: EC2, Lambda, containers).
- **Storage (Armazenamento):** custo pelo espaço utilizado para guardar dados (ex: S3, EBS).
- **Data Out (Dados de saída):** custo pela transferência de dados para fora da AWS (internet). A entrada de dados (Data In) é geralmente gratuita.

---

## 3. Pontos para Escolha de Região AWS

- **Conformidade (compliance):** atender às leis e regulamentos locais, como a LGPD no Brasil.
- **Latência:** escolher uma região próxima dos usuários para reduzir atrasos e melhorar a experiência.
- **Preço:** custos dos serviços AWS podem variar entre regiões, influenciando o orçamento.

---

## 4. Serviços com Escopo Global e Regionais

- **Globais:** Route 53 (DNS), IAM (gerenciamento de identidade e acesso), CloudFront (CDN), AWS WAF (firewall).
- **Regionais:** EC2 (máquinas virtuais), S3 (armazenamento), RDS (banco de dados relacional).

---

## 5. Infraestrutura da AWS

- **Regiões:** agrupamentos geográficos com múltiplas Zonas de Disponibilidade (AZs).
- **Zonas de Disponibilidade (AZs):** data centers independentes com energia, rede e refrigeração próprios. Cada região tem pelo menos 2 AZs para garantir resiliência.
- **Edge Locations:** pontos de presença espalhados globalmente usados para acelerar a entrega de conteúdo via CDN, como no CloudFront.

---

## 6. Modelo de Responsabilidade Compartilhada AWS

- **AWS:** responsável pela segurança da nuvem — infraestrutura física, hardware, software, rede, data centers.
- **Cliente:** responsável pela segurança na nuvem — dados, identidade, aplicações, sistemas, redes e firewalls.
- Importante para o cliente entender essa divisão para garantir compliance e segurança.

---

## 7. Modelo Pay As You Go

- Paga-se apenas pelo uso efetivo dos recursos, sem necessidade de investimento antecipado ou contratos fixos.

---

## 8. Modelos de Cloud Computing

- **On-premises:** infraestrutura própria no local da empresa.
- **IaaS (Infrastructure as a Service):** aluguel de recursos virtuais (ex: EC2, S3).
- **PaaS (Platform as a Service):** plataforma para desenvolver e rodar aplicações (ex: RDS, ECS).
- **SaaS (Software as a Service):** software pronto para uso (ex: Gmail, WorkSpaces).

---

## 9. Diferença entre Tolerância a Falhas e Recuperação de Desastres

- **Tolerância a falhas:** manter o sistema funcionando mesmo quando partes falham, com redundância ativa.
- **Recuperação de desastres:** restaurar serviços após falhas severas, com possível downtime.



---

## 10. Política de Uso Aceitável da AWS (Acceptable Use Policy - AUP)

- Define o que não é permitido na plataforma AWS. 
- Proíbe uso ilegal, ofensivo ou prejudicial.
- Proíbe ataques, invasões, spam, abuso de rede, e mensagens fraudulentas.
- Link oficial: [https://aws.amazon.com/aup/](https://aws.amazon.com/aup/)

---

## 11. Serviços AWS e Seus Modelos de Nuvem

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

## 12. IAM: Usuários e Grupos
- **IAM** = Gerenciamento de Identidade e Acesso, serviço global
- A conta **root** é criada por padrão e não deve ser usada ou compartilhada
- **Usuários** são pessoas dentro da sua organização e podem ser agrupadas
- **Grupos** contêm apenas usuários, não podem conter outros grupos
- **Usuários** não precisam pertencer a um grupo, e um usuário pode pertencer a vários grupos.

### 13. IAM: Permissões
Na AWS, usuários e grupos podem receber políticas, que são documentos no formato JSON usados para definir exatamente o que cada usuário ou grupo pode ou não fazer dentro do ambiente. Essas políticas controlam as permissões de acesso aos recursos da nuvem. Para manter a segurança e a boa prática de governança, a AWS adota o princípio do menor privilégio, que recomenda conceder apenas as permissões estritamente necessárias para que o usuário execute suas funções, evitando riscos e acessos indevidos.

## 14. Estrutura de Políticas IAM (AWS)

Uma política IAM (Identity and Access Management) é composta por:

- **Version:** Versão da linguagem da política (sempre incluir `"2012-10-17"`)
- **Id:** Identificador opcional da política
- **Statement:** Uma ou mais declarações que definem permissões (obrigatório)

#### 14.1 Estrutura de uma declaração (Statement)

Cada `Statement` pode conter os seguintes elementos:

- **Sid:** Identificador da declaração (opcional)
- **Effect:** Define se a ação será **permitida (Allow)** ou **negada (Deny)**
- **Principal:** Conta, usuário ou função (role) a quem a política se aplica
- **Action:** Lista de ações que a política permite ou nega
- **Resource:** Lista de recursos aos quais as ações se aplicam
- **Condition:** Condições sob as quais a política entra em vigor (opcional)

> Exemplo de uso: você pode criar uma política que permite a um usuário listar objetos em um bucket S3 específico, apenas se ele estiver usando autenticação MFA.


## 15. IAM – Política de Senhas

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

## 16 Autenticação Multifator – MFA

- Os usuários têm acesso à sua conta e podem, possivelmente, alterar configurações ou excluir recursos na sua conta AWS.
- Você quer proteger sua **conta Root e usuários IAM**
- MFA = senha que **você sabe** + dispositivo de segurança que **você possui**

### 16.1 Exemplo de fluxo de login com MFA:
[Usuário: Alice] + [Senha] + [MFA] => [Login bem-sucedido]

- **Principal benefício do MFA**:  
  Se uma senha for roubada ou invadida, **a conta não será comprometida**

## 17. Como os usuários acessam a AWS?

- Para acessar a AWS, você tem três opções:
  - **AWS Management Console** (protegido por senha + MFA)
  - **AWS Command Line Interface (CLI)**: protegido por chaves de acesso
  - **AWS Software Developer Kit (SDK)**: para código, protegido por chaves de acesso

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
