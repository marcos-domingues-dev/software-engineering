# 1. Sistemas monolíticos

---

- [1. Sistemas monolíticos](#1-sistemas-monolíticos)
  - [1.1. O que é?](#11-o-que-é)
  - [1.2. Monolito em primeiro - Quando utilizar?](#12-monolito-em-primeiro---quando-utilizar)
  - [1.3. Tipos de Monolítos](#13-tipos-de-monolítos)
  - [1.4. Sistemas monolíticos modulares](#14-sistemas-monolíticos-modulares)
    - [1.4.1. Exemplo de contextos](#141-exemplo-de-contextos)
    - [1.4.2. Características](#142-características)
    - [1.4.3. Segregação de banco de dados](#143-segregação-de-banco-de-dados)
    - [1.4.4. Modulares](#144-modulares)
    - [1.4.5. Pontos de Antenção](#145-pontos-de-antenção)
    - [1.4.6. Estrutura de Projeto](#146-estrutura-de-projeto)
    - [1.4.7. Comunicação entre módulos](#147-comunicação-entre-módulos)

<br>

---

## 1.1. O que é?

- Abordagem tradicional
- Tudo em um
- Unidade de Deployment

[^1]

<br>

> Aplicações monolíticas
> 
> Um aplicativo monolítico é um aplicativo de software de camada única no qual a interface do usuário e o código de acesso são dados e combinados em um único programa a partir de uma única plataforma.
> 
> É autônomo e independente de outros aplicativos de computação.
Um aplicativo monolítico descreve uma aplicação de software que é projetada sem modularidade.
> 
> A modularidade é desejável, em geral, pois suporta a reutilização de partes da lógica da aplicação e também a manutenção por reparo ou substituição de partes da aplicação sem a necessidade de substituição em atacado.[^2]

<br>
	
```
Outras abordagens
- Microserviços
- Serverless
- Edge Computing - Perto da borda (próximo do usuario).
```

---

<br>

> :bulb: **OpenIA:** "Explique resumidamente o que é 'Monolíto'"
>
> A arquitetura monolítica é um padrão de arquitetura de software em que todo o sistema é construído como um único componente ou módulo. Isso significa que todos os componentes do sistema, como a interface do usuário, o banco de dados e a lógica de negócios, estão acoplados juntos em um único bloco de código. Embora possa ser mais fácil de desenvolver e manter inicialmente, os sistemas monolíticos tendem a se tornar complexos e difíceis de escalar com o tempo. Com a adoção da arquitetura limpa (Clean Architecture), os desenvolvedores se concentram em separar as preocupações em camadas distintas, permitindo que o código seja mais modular e independente. Isso facilita a manutenção e a evolução do sistema ao longo do tempo, além de permitir uma maior flexibilidade na adição de novas funcionalidades. A arquitetura limpa incentiva o desenvolvimento de sistemas com baixo acoplamento, alta coesão e testabilidade, tornando-o uma abordagem popular para a construção de sistemas escaláveis e de fácil manutenção.[^3]

<br>

---

## 1.2. Monolito em primeiro - Quando utilizar?

- Projetos de modelo não claro
- Instabilidade no Core
- Evitar complexidade no Deploy
		
> "Monolith First - Martin Fowler"

<br>

---

## 1.3. Tipos de Monolítos

- Single process
- Monolitos distribuídos
- Black box	
	
```
Single Process
- Alto acoplamento
- Modular
- Modular c/ banco de dados segregados
```

<br>

---

## 1.4. Sistemas monolíticos modulares

> "DDD - O ponto de partida"

<br>

---

### 1.4.1. Exemplo de contextos
- Catálogo
- Carrinho Compras
- Checkout
- Pagamento
- Suporte ao cliente
- Marketing
- Programa de pontos
- Lista de casamento

<br>

---

### 1.4.2. Características
- Contextos isolados
- Bounded contexts - conversam através de contrados e facades
- Entidades podem ser duplicadas
- Equipes especializadas por Módulos
- Alta coesão - O que muda junto permanece junto

<br>

---

### 1.4.3. Segregação de banco de dados
- Separado por schema

<br>

---

### 1.4.4. Modulares
- Unico deploy
- Unica operação
- Observabilidade simplificada
- Comunicação interna
- Única linguagem
- Menos governança

<br>

---

### 1.4.5. Pontos de Antenção

Módulo
> Framework
> Shared Kernel - políticas de atualização

<br>

---

### 1.4.6. Estrutura de Projeto

DDD: Aplicação > Domínios > Subdomínios (Mapa de Contexto)
- Core domain
- Support Subdomain
- Generic Subdomain

<br>

```
Context Map

* product-adm
* store-catalog	-> Main-Context
* customer-adm
* checkout
* payment       -> Generic (Gateway / de prateleira)
* invoice       -> Generic (Nota Fiscal / de prateleira)
```

<br>

---

### 1.4.7. Comunicação entre módulos

- Como isolar os contextos?
- Como evitar o acoplamento?

Resposta: Criar 'Facade'

```
EXEMPLO:
	Checkout não acessa tabela PRODUTOS.		
	Aciona módulo facade do 'store-catalog' (API)
	
DINÂMICA
	- Checkout
		-- store-catalog
		-- customer-adm
		-- payment
		-- invoice
```


[^1]: Curso FullCycle - Sistemas monolíticos<br>
  Consultado em: 11/01/2023<br>
  Disponível em: https://plataforma.fullcycle.com.br

[^2]: Aplicações Monolíticas<br>
  Consultado em: 05/04/2023<br>
  Disponível em: https://pt.wikipedia.org/wiki/Sistema_operacional_monol%C3%ADtico#Aplica%C3%A7%C3%B5es_monol%C3%ADticas

[^3]: OpenIA -> "Explique resumidamente o que são 'Sistemas monolíticos'"<br>
  Consultado em: 05/04/2023<br>
  Disponível em: https://chat.openai.com/chat