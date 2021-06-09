---
title:  "Anotações 2 - Desafio de habilidades de nuvem Azure Developer"
img: 
description: "Anotações dos estudos do Desafio de habilidades de nuvem Azure Developer."
keywords: cloud, azure, estudos, anotações, LearnInPublic
date: 2021-06-09 07:12:00 +0530
blog: true
author: "Lucas Lima da Silva"
---

## Criar uma lógica sem servidor com o Azure Functions

Com a computação serverless, seu provedor em nuvem gerencia o provisionamento e a manutenção da infraestrutura. permitindo  que você se concentre por completo na criação da lógica do aplicativo. O Azure Functions é um componente fundamental da oferta de computação sem servidor do Azure e possibilita que você execute trechos de código ou funções , escritos na linguagem de programação  de sua escolha, na nuvem.

## Decidir se a computação sem servidor é ideal para suas necessidades de negócios

### O que é computação sem servidor ?

Pode ser considerada uma FaaS (função como serviço) ou um microsserviço hospedade em uma plataforma de nuvem. Sua lógica de negócios é executada como funções e você não precisa provisionar nem dimensionar a infrestrutura manualmente.

Azure fornece várias maneiras de criar esse tipo de arquitetura. As mais comuns são aplicativos lógicos e azure functions.

### Azure Functions

Plataforma de aplicativos sem servidor que permite hospedar uma lógica de negócios que possa ser executada sem provisionar infra.  Fornece escalabilidade intrínseca e vc só é cobrado pelo que usa.

## Benefícios de uma solução de computação sem servidor

### Evita alocação excessiva de infraestrutura

Resolve o problema de alocação escalando ou reduzindo verticalmente de forma automática e você é cobrado apenas quando a função está processando o trabalho

### Lógica sem estado

As instâncias de função são criadas e destruídas sob demanda. Caso estado seja necessário, pode ser armazenado em um serviço de armazenamento

### Controlada por eventos

- Executadas apenas em resposta a um evento (trigger);
- Você não precisa escrever um código para inspecionar filas, blobs, hubs etc.

### As funções podem ser usadas em ambientes de computação tradicionais

Caso o projeto precise mudar, você pode implementar as alterações em ambiente local, e só implantar o app quando estiver funcionando corretamente.

## Desvantagens de uma solução de computação sem servidfor

### Tempo de execução

Por padrão, as funções possuem um tempo limite de 5 minutos, mas esse tempo pode ser configurado para 10 min. Se a função exigir mais que isso, é possível hospedá-la em uma VM.

- **Se for uma função HTTP trigger, o tempo será reduzido para 2,5 min.**
- **Há a opção de usar Durable Functions, que permite orquestrar as execuções de várias funções sem tempo limite.**

### Frequência de execução

Se for para executar uma função várias vezes por vários clientes, talvez seja melhor hospedar o serviço em uma VM.

Durante o dimensionamento, apenas 1 instância do app pode ser criada a cada 10s num total de 200 instâncias, e cada instância pode atender várias execuções simultâneas.

## Exercício - Criar um aplicativo de funções no portal do Azure

### O que é um aplicativo de funções?

Funções são hospedadas em um contexto de execução chamado de **aplicativo de funções**. Você define os aplicativos de funções para agrupar logicamente e estruturar as funções e um recurso de computação no Azure.

### Escolher um plano de serviço

- **Plano de serviço de consumo**: dimensionamento automático e cobra você durante a execução das funções. Fornecido com tempo de limite de 5 min (configurável até 10min);
- **Plano do serviço de aplicativo do Azure:** sem tempo de limite, fazendo com que a function seja executada continuamente em uma VM definida. Você é responsável por gerenciar os recursos do app. Poderá ser melhor se as funções forem executadas continuamente ou se as funções precisarem de mais potência de processamento do que o plano de consumo pode fornecer.

### Requisitos da conta de armazenamento

- aplicativo de funções precisa ser vinculado a uma conta de armazenamento que será usada para operações internas, como log e gerenciamento de gatilhos de execução.

## Executar o código sob demanda com o Azure Functions

### Gatilhos

Funções são controladas por eventos, o que significa que são executadas em resposta a um evento chamado **gatilho**

| Serviço                    | Descrição do gatilho                                                                                                                                        |
|----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Armazenamento de Blobs     | Inicia uma função quando um blob novo ou atualizado é detectado.                                                                                            |
| Azure Cosmos DB            | Inicia uma função quando inserções e atualizações são detectadas.                                                                                           |
| Grade de Eventos           | Inicia uma função quando um evento é recebido da Grade de Eventos.                                                                                          |
| HTTP                       | Inicia uma função com uma solicitação HTTP.                                                                                                                 |
| Eventos do Microsoft Graph | Inicia uma função em resposta a um webhook de entrada do Microsoft Graph. Cada instância desse gatilho pode reagir a um tipo de recurso do Microsoft Graph. |
| Armazenamento de filas     | Inicia uma função quando um novo item é recebido em uma fila. A mensagem da fila é fornecida como entrada para a função.                                    |
| Barramento de Serviço      | Inicia uma função em resposta a mensagens de uma fila do Barramento de Serviço.                                                                             |
| Temporizador               | Inicia uma função de acordo com um agendamento.                                                                                                             |
---

### Associações (bindings)

Maneira declarativa de conectar dados e serviços à função. As associações sabem como se comunicar com serviços diferentes, o que significa que você não precisa escrever um código na função para se conectar a fontes de dados e gerenciar conexões. Um gatilho é um tipo especial de associação de entrada que tem a funcionalidade adicional de iniciar a execução.

### Definir uma associação de exemplo

Suponha que você deseje gravar uma nova linha no Armazenamento de Tabelas do Azure sempre que uma nova mensagem é exibida no Armazenamento de Filas do Azure. Esse cenário pode ser implementado usando um *gatilho* do Armazenamento de Filas do Azure e uma *associação de saída* do Armazenamento de Tabelas do Azure.

O snippet a seguir é o arquivo *function.json* para este cenário.

```jsx
{
  "bindings": [
    {
      "name": "order",
      "type": "queueTrigger",
      "direction": "in",
      "queueName": "myqueue-items",
      "connection": "MY_STORAGE_ACCT_APP_SETTING"
    },
    {
      "name": "$return",
      "type": "table",
      "direction": "out",
      "tableName": "outTable",
      "connection": "MY_TABLE_STORAGE_ACCT_APP_SETTING"
    }
  ]
}
```

Este exemplo é uma ilustração simples de como podemos configurar associações para uma função. Podemos alterar a saída para email usando uma associação do SendGrid, colocar um evento em um Barramento de Serviço para notificar outro componente em nossa arquitetura ou, até mesmo, ter várias associações de saída para efetuar push de dados para vários serviços.

### Proteger os gatilhos HTTP

Gatilhos HTTP permitem que você use chaves de API para bloquear chamadores desconhecidos, exigindo a presença da chave em cada solicitação.