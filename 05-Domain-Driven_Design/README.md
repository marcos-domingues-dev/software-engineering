# 1. Domain-Driven Design

- [1. Domain-Driven Design](#1-domain-driven-design)
  - [1.1. Características do DDD](#11-características-do-ddd)
    - [1.1.1. Linguagem Ubíqua (geral e universal)](#111-linguagem-ubíqua-geral-e-universal)
    - [1.1.2. Model Driven Design – MDD](#112-model-driven-design--mdd)
    - [1.1.3. Arquitetura em Camadas - Layered Architecture](#113-arquitetura-em-camadas---layered-architecture)
      - [1.1.3.1. Interface de Usuário](#1131-interface-de-usuário)
      - [1.1.3.2. Aplicação](#1132-aplicação)
      - [1.1.3.3. Domínio](#1133-domínio)
      - [1.1.3.4. Blocos de Construção (building blocks)](#1134-blocos-de-construção-building-blocks)
      - [1.1.3.5. Padrões de Contexto (Bounded contexts)](#1135-padrões-de-contexto-bounded-contexts)
      - [1.1.3.6. Núcleo do Domínio (Core Domain)](#1136-núcleo-do-domínio-core-domain)
  - [1.2. Template para descrever uma História](#12-template-para-descrever-uma-história)
  - [1.3. Template para descrever um cenário de teste](#13-template-para-descrever-um-cenário-de-teste)


Desenvolver software com foco no coração (domínio)
	
Tendo o objetivo de entender suas regras, processos e complexidades,separando-as assim de outros pontos complexos que normalmente são adicionados durante o processo de desenvolvimento.[^1]

> The Domain-driven design are aimed aclerating software projects that have to deal with complicated domains.
>
> It is an extensive design practices, tecniques and principles.[^2]

---

<br>

> :bulb: **OpenIA:** "Me explique resumidamente o que é Domain-driven design"
> 
> Domain-driven design (DDD) é uma abordagem para o desenvolvimento de software que se concentra no domínio do problema a ser resolvido. Em vez de se concentrar em tecnologia ou detalhes de implementação, DDD enfatiza a compreensão profunda do domínio de negócios e a modelagem do software em torno desse domínio.
> 
> A abordagem DDD se concentra em identificar as entidades centrais do domínio e como elas se relacionam umas com as outras. O processo de modelagem começa com a captura do conhecimento do domínio em um modelo rico, que é refinado ao longo do tempo à medida que a equipe de desenvolvimento ganha mais compreensão do problema.
> 
> O objetivo final do DDD é criar um software que reflita com precisão as necessidades do domínio e permita que as equipes de desenvolvimento se comuniquem facilmente com os especialistas do domínio. Além disso, a abordagem DDD promove a modularidade do código, tornando-o mais fácil de manter e escalonar.
> 
> Em resumo, o Domain-driven design (DDD) é uma abordagem para o desenvolvimento de software que se concentra no domínio do problema a ser resolvido, em vez de tecnologia ou detalhes de implementação. A abordagem DDD enfatiza a compreensão profunda do domínio de negócios e a modelagem do software em torno desse domínio, identificando as entidades centrais e como elas se relacionam. O objetivo final do DDD é criar um software que reflita com precisão as necessidades do domínio e promova a modularidade do código.[^3]

<br>

---

## 1.1. Características do DDD

- Linguagem Ubíqua (geral e universal)
- Modelo Abstrato
- Arquitetura em Camadas
- Blocos de Construção
- Padrões de Contexto
- Core Domain

### 1.1.1. Linguagem Ubíqua (geral e universal)

- Expressa o conhecimento dos especialistas de negócio

### 1.1.2. Model Driven Design – MDD

- Modelo abstrato

### 1.1.3. Arquitetura em Camadas - Layered Architecture

| Camada               | Descrição                              |
| :------------------- | :------------------------------------- |
| Interface de Usuário | View                                   |
| Aplicação            | Conectar a View às camadas inferiores; |
| Domínio              | Lógicas de negócio                     |
| Infra-estrutura      | Persistência de dados, e-mail, Filas   |

#### 1.1.3.1. Interface de Usuário
- (Disparada) [Botões do Controle]
- Comunicar com o usuário: receber comando como mostrar resultados;

#### 1.1.3.2. Aplicação
- (Quando) [Operações do controle]
- Onde é disparada a lógica de negócio que está em outra camada, ou é chamada alguma tarefa técnica de banco de dados, como o início de uma transação e seu respectivo final

#### 1.1.3.3. Domínio
- (O que)
- É esta camada que dá valor à aplicação, ela iterage com todas as camadas da aplicação.
1. Recebe chamadas da camada de aplicação;
2. Dispara requisições para a camada de infraestrutura;
3. Devolve valores para a camada de Aplicação;
4. Retorna o resultado para a interface com o usuário;

> PREMISAS DAS CAMADAS
> - Estar completamente desassociada uma da outra, se comunicando sempre através de interfaces;
> - A camada inferior nunca dispara operações na camada superior;

#### 1.1.3.4. Blocos de Construção (building blocks)

| Bloco            | Descrição                                                             |
| :--------------- | :-------------------------------------------------------------------- |
| Entidades        | Bean com ID                                                            |
| Objetos de valor | Bean sem ID                                                            |
| Agregados        | Entidades ou Objetos de Valores encapsulados                          |
| Fábricas         | Criação dos Agregados ou dos Objetos de Valores                       |
| Serviços         | Lógica de negócio                                                     |
| Repositórios     | Administra o ciclo de vida de Entidades, Objetos de Valor e Agregados |
| Módulos          | Abstrações de um domínio (pacotes, namespaces)                        |

#### 1.1.3.5. Padrões de Contexto (Bounded contexts)

Relação entre times - Bounded contexts (contextos delimitados)

- Mapa de contextos
- Produtor-Consumidor
- Conformista
- Núcleo compartilhado
- Camada anti-corrupção (Ex.: Transações)
- Caminhos Separados
- Serviço Aberto de Funcionalidades e Linguagem Publicada (API)

#### 1.1.3.6. Núcleo do Domínio (Core Domain)

- Doc.: Sentença da Visão de Domínio
- Sub-domínios genéricos (Soluções de prateleira)

<br>

---

## 1.2. Template para descrever uma História
Funcionalidade : [Nome]
- Para [ Valor ao Negócio ]
- Eu, como [ Papel ]
- Desejo poder realizar [ Funcionalidade ]

## 1.3. Template para descrever um cenário de teste
Cenário : [ Nome ]
- Dado que [ Estado inicial do sistema ]
- Quando [ Ação a ser realizada no sistema ]
- Então [ Coisas que o sistema deve fazer após a ação do Quando ]


[^1]: Curso FullCycle - Arquitetura de Software<br>
  Consultado em: 06/01/2023<br>
  Disponível em: https://plataforma.fullcycle.com.br

[^2]: Domain-Driven Design: Tackling Complexity in the Heart of Software (English Edition) 1ª Edição, eBook Kindle<br>
  Consultado em: 03/04/2023<br>
  Disponível em: https://www.amazon.com.br/Domain-Driven-Design-Tackling-Complexity-Software-ebook/dp/B00794TAUG/ref=sr_1_2?keywords=domain+driven+design&qid=1680574402&sprefix=Domain%2Caps%2C260&sr=8-2

[^3]: OpenIA -> "Apresente resumidamente o que é Domain-driven design"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 03/04/2023