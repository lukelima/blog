---
title:  "Termos frequentemente utilizados em Cloud Computing"
img: 
description: "Um compilado de termos comumente usados ao falar sobre Cloud Computing"
keywords: cloud, estudos, anotações
date: 2020-11-07 11:00:00 +0530
blog: true
author: "Lucas Lima da Silva"
---

## Início
Estou estudando para o exame Az-900 da Microsoft e percebi que alguns termos são repetidos com frequencia. Assim sendo, decidi criar um compilado desses termos e seus significados.

## Termos

### Cloud provider
Uma empresa que fornece uma plataforma baseada em nuvem, infraestrutura, aplicação ou outros serviços para as organizações e indivíduos.

### Public cloud
Nessa modalidade, tudo pertence a algum cloud provider. Os serviços geralmente são acessados via conexão segura (internet). Usuários dessa modalidade podem compartilhar economizar custos compartilhando recursos computacionais com outros usuários de nuvem (sem que os dados de um usuário sejam acessados pelo outro).

### Private cloud
Nessa modalidade, uma organização possui um serviço de nuvem, o qual é administrado e mantido por ela. Ela cria um ambiente que disponibiliza acesso ao datacenter e recursos dentro da organização.

### Hybrid cloud
Nessa modalidade, a empresa utiliza alguns recursos específicos em nuvem pública e outros em nuvem privada.

### IaaS - Infrastructure as a service
Categoria mais básica de serviços de computação em nuvem, na qual é possível contratar servidores, máquinas virtuais, armazenamento, redes e sistemas operacionais. Exemplos incluem **DigitalOcean, AWS, Microsoft Azure** etc.

### PaaS - Platform as a service
Fornece um ambiente para criar, testar e lançar aplicações, geralmente acompanhados por sistemas de gerenciamento de bancos de dados e business analytics. Você não precisa instalar um sistema operacional, servidor ou atualizações de sistemas. Exemplos incluem: **Heroku, Azure** etc.

### SaaS - Software as a service
Software destinado ao usuário final. Geralmente é licenciado por uma inscrição anual ou mensal, como o Microsoft 365.

### High availability - Alta disponibilidade
É a capacidade de manter um sistema em funcionamento por longos períodos de tempo, havendo pouco ou nenhum tempo de inatividade (downtime).

### Scability - Escalabilidade
É um conceito que se refere à capacidade de ampliar ou remover recursos de um sistema para aguentar uma carga específica, como picos de acessos durante promoções, datas comemorativas etc. Nem sempre é feito de forma automática.

* **Escalabilidade Vertical (scaling up ou vertical scaling)**: trata-se de adicionar novos recursos, como mais CPU ou recursos de memória para uma VM.

* **Escalabilidade Horizontal (scaling out ou horizontal scaling)**: trata-se de adicionar novas instâncias (novas VMs ou containers) e fazer balanceamento de carga para que os acessos fiquem distribuidos entre essas instâncias.

### Elasticity
Refere-se à capacidade de adicionar ou remover recursos conforme a necessidade. A diferença entre escalabilidade e elasticidade é que a **última é feita automaticamente**.

### Fault tolerance - Tolerância a falhas
Refere-se à capacidade de manter um sistema funcionando mesmo que haja alguma falha em um componente, um serviço etc. 

### Disaster recovery - Recuperação de desastres
É a capacidade de se recuperar de eventos que derrubaram um serviço em nuvem. 

### SLA
Um acordo contratual pelo qual um fornecedor define o núvel de serviço, responsabilidades, prioridades e outras garantias sobre disponibilidade, performance etc.

## Fontes
* [Explore key cloud concepts](https://docs.microsoft.com/en-us/learn/modules/discuss-why-cloud-services/4-explore-key-cloud-concepts);
* [Mini-glossary: Cloud computing terms you should know](https://www.techrepublic.com/blog/the-enterprise-cloud/mini-glossary-cloud-computing-terms-you-should-know/);
* [A Cloud Computing Glossary](https://www.cloudwatchhub.eu/cloud-computing-glossary-0);
* [Escalabilidade em Cloud Computing: por que ela é essencial?](https://www.fwc.com.br/blog/escalabilidade-em-cloud-computing-por-que-ela-e-essencial/);
* [IaaS vs PaaS vs SaaS Enter the Ecommerce Vernacular: What You Need to Know, Examples & More](https://www.bigcommerce.com/blog/saas-vs-paas-vs-iaas/#the-three-types-of-cloud-computing-service-models-explained)