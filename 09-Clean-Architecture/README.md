# 1. Clean Architecture

<br>

---

- [1. Clean Architecture](#1-clean-architecture)
  - [1.1. Origem](#11-origem)
  - [1.2. Relação com outras abordagens:](#12-relação-com-outras-abordagens)
  - [1.3. Camadas](#13-camadas)
    - [1.3.1. Camada de Entities](#131-camada-de-entities)
    - [1.3.2. Camada de Use Cases](#132-camada-de-use-cases)
    - [1.3.3. Camada de Adapters](#133-camada-de-adapters)
    - [1.3.4. Camada de Frameworks e Drivers](#134-camada-de-frameworks-e-drivers)
  - [1.4. Entendendo DTOs](#14-entendendo-dtos)
  - [1.5. Presenters](#15-presenters)
  - [1.6. Entities vs DDD](#16-entities-vs-ddd)
  - [1.7. Relação com 'Notification Pattern'](#17-relação-com-notification-pattern)

---

<br>

## 1.1. Origem

- Robert C. Martin - 2012
- Livro
- Proteção do domínio da aplicação
- Baixo acoplamento
- Orientado a caso de uso - ( intention oriented )

[^1]

<br>

---

## 1.2. Relação com outras abordagens:

- Domain-driven design (DDD) by Eric Evan
- Arquitetura Hexagonal ('Ports and Adapters') by Alistair Cockburn
- Onion Architecture by Jeffrey Palermo

> "Todas elas têm o mesmo objetivo, que é a separação de interesses. Todas elas conseguem essa separação dividindo o software em camadas.
>
> Cada uma dessas arquiteturas produz sistemas que são:
> 
> - Independente de Frameworks. A arquitetura não depende da existência de alguma biblioteca de software carregada de recursos. Isso permite que você use tais estruturas como ferramentas, em vez de ter que amontoar seu sistema em suas restrições limitadas.
> - Testável. As regras de negócios podem ser testadas sem interface do usuário, banco de dados, servidor Web ou qualquer outro elemento externo.
> - Independente da IU. A IU pode mudar facilmente, sem alterar o resto do sistema. Uma IU da Web pode ser substituída por uma IU de console, por exemplo, sem alterar as regras de negócios.
> - Independente de banco de dados. Você pode trocar Oracle ou SQL Server por Mongo, BigTable, CouchDB ou qualquer outra coisa. Suas regras de negócios não estão vinculadas ao banco de dados.
> - Independente de qualquer agência externa. Na verdade, suas regras de negócios simplesmente não sabem nada sobre o mundo exterior."
>
> Robert C. Martin (Uncle Bob).[^2]

<br>

---

<br>

> :bulb: **OpenIA:** "Explique resumidamente o que é 'Clean Architecture'"
>
> Clean Architecture é uma abordagem de engenharia de software que visa criar sistemas de software altamente modularizados e independentes de tecnologia, mantendo a arquitetura do sistema flexível e extensível. Ele é baseado no princípio de separação de interesses, o que significa que o código deve ser organizado em camadas, cada uma responsável por uma preocupação específica.
> 
> A arquitetura limpa consiste em quatro camadas principais: Entidades, Casos de Uso, Adaptadores e Frameworks e Drivers. As Entidades representam o núcleo da aplicação e contêm a lógica de negócios e as regras de domínio. Os Casos de Uso implementam os casos de uso específicos da aplicação, usando as Entidades como base. Os Adaptadores são responsáveis pela comunicação entre as camadas e pela adaptação dos dados de entrada e saída para os formatos esperados pelas outras camadas. Os Frameworks e Drivers são as camadas mais externas e são responsáveis pela interação com o mundo exterior, como a interface do usuário e os serviços externos.
> 
> A arquitetura limpa também enfatiza a importância da separação de conceitos técnicos e de negócios, permitindo que a equipe de desenvolvimento se concentre na lógica de negócios e na resolução de problemas do cliente, em vez de se preocupar com a tecnologia subjacente. Além disso, ela promove o uso de testes automatizados para garantir que o sistema seja robusto e fácil de manter.[^3]

---

<br>

````
--------------------------------------------------------------------------------
> PONTOS IMPORTANTES SOBRE ARQUITETURA

	* Formato de software
	* Divisão de componentes
	* Comunicação entre componentes
	* Facilitar o processo de desenvolvimento

--------------------------------------------------------------------------------
> KEEP OPTIONS OPEN

	* Objetivo principal é dar suporte ao ciclo de desenvolvimento.
	
	* Uma boa arquitetura torna o sistema fácil de entender,
		desenvolver, manter e implantar.
	
	* Minimizar o custo de vida útil do sistema e 
		maximizar a produtividade do programador

--------------------------------------------------------------------------------
> REGRAS VS DETALHES

	* Regras de negócio trazem o real valor para software
	* Detalhes ajudam a suportar regras
	* Detalhes não devem impactar nas regras de negócio
	* Framewoks, bancos de dados, APIs, não devem impactar nas regras
````

<br>

---

## 1.3. Camadas

| CAMADA               | DESCRIÇÃO                 |
| :------------------- | :------------------------ |
| Entities             | Enterprise Business Rules |
| Use Cases            | Application Busines Rules |
| Adapters             | Controller                |
| Frameworks e Drivers | Web                       |

<br>

---

### 1.3.1. Camada de Entities

> :bulb: **OpenIA:** "Explique resumidamente Camada de Entities, da 'Clean Architecture'"
>
> Na arquitetura limpa, a camada de "Entidades" é uma das camadas mais importantes e fundamentais. Ela é responsável por definir os objetos que representam as entidades do domínio do sistema e suas regras de negócios, ou seja, a lógica central do negócio. Essa camada não deve depender de nenhuma outra camada ou framework, deve ser independente de tecnologia e pode ser reutilizada em diferentes projetos. As entidades devem ser mantidas o mais simples possível, contendo apenas atributos, identificadores e métodos que refletem as regras de negócios do domínio. A camada de entidades também deve ser protegida contra mudanças externas, para garantir a integridade dos dados do sistema.[^4]

<br>

---

### 1.3.2. Camada de Use Cases

- Intenção - Cada ação é uma intenção
- Clareza de cada comportamento
- Detalhes não devem impactar nas regras de negócio
- Framewoks, bancos de dados, APIs, não devem impactar nas regras

<br>

> Use Cases - SRP
> - "Reaproveitar" use cases?
> - Ex.: Alterar vs Inserir
> - SRP (Single Responsibility Principle) - Mudam por razões diferentes (alterar o código)

<br>

> :bulb: **OpenIA:** "Explique resumidamente Camada de Use Cases, da 'Clean Architecture'"
>
> Na arquitetura limpa, a camada de "Use Cases" é responsável por implementar a lógica de negócios da aplicação. Ela contém as regras de negócio específicas da aplicação e é responsável por coordenar as entidades e as interfaces do sistema. Os casos de uso são implementados como classes ou objetos que encapsulam a lógica de negócio do sistema e interagem com as entidades para realizar ações específicas. Essa camada depende da camada de entidades, mas não deve depender de nenhuma outra camada externa à aplicação. Além disso, essa camada deve ser testável e independente de tecnologia, para que os casos de uso possam ser reutilizados em diferentes interfaces do usuário ou sistemas. A camada de casos de uso é fundamental para manter a separação de interesses e garantir a manutenção e a evolução do sistema no longo prazo.[^5]

<br>

---

### 1.3.3. Camada de Adapters

> :bulb: **OpenIA:** "Explique resumidamente Camada de Adapters, da 'Clean Architecture'"
>
> Na arquitetura limpa, a camada de "Adapters" é responsável por adaptar as interfaces externas do sistema, como bancos de dados, UIs e frameworks, às interfaces internas do sistema, como casos de uso e entidades. Essa camada inclui classes que implementam as interfaces definidas na camada de casos de uso e classes que adaptam as interfaces externas às interfaces internas do sistema. As classes de adaptação permitem que as interfaces externas se comuniquem com a camada de casos de uso e as entidades sem conhecer sua implementação interna, promovendo a independência de tecnologia e a facilidade de manutenção do sistema. A camada de adaptadores é fundamental para a interoperabilidade do sistema e para a garantia de que as mudanças externas não afetem a lógica de negócio do sistema.[^6]

<br>

---

### 1.3.4. Camada de Frameworks e Drivers

> :bulb: **OpenIA:** "Explique resumidamente Camada de Frameworks e Drivers, da 'Clean Architecture'"
>
> Na arquitetura limpa, a camada de "Frameworks e Drivers" é a camada mais externa e é responsável por integrar o sistema com os frameworks e drivers externos, como bibliotecas de terceiros, bancos de dados, servidores web, entre outros. Essa camada é composta por classes que lidam com a entrada e a saída de dados do sistema, como controllers, gateways e repositories, e são responsáveis por traduzir as solicitações recebidas em chamadas para os casos de uso do sistema. Essa camada é a única que pode ser específica de tecnologia e é responsável por integrar as tecnologias externas ao sistema. A camada de frameworks e drivers deve ser mantida o mais fina possível, de forma a garantir a independência de tecnologia do sistema e facilitar sua manutenção e evolução.[^7]

## 1.4. Entendendo DTOs

- Data Transfer Object
- É um tipo de 'Envelope' de dados
- Ajuda a trafegar dados entre os limites arquiteturais
- Anêmico - sem comportamentos
- Contém dados - (Input e Output)

```
DTO em resumo:
- Sem regras
- Sem comportamento
- Não faz nada!
```

<br>

> ## **Fronteiras DTO vs Domain**
>	
> "Normalmente cada 'use case' possui o seu DTO de 'Input' e 'Output'"
>
> <br>
>
> :memo: **DICA:**: O objeto de 'domínio' não pode ultrapassar o 'Use case'.
> 
> - Todo 'Use case' receberá no 'InputDTO'
> - e devolverá no 'OutputDTO'.

<br>

---

## 1.5. Presenters

* Objetos de Transformação
* Adequa DTO de output no formato correto para entregar o resultado

REST Content Type:
- JSON
- XML
- Text
- GraphQL
- Protobuf

```java
	// EXEMPLO	
	CategoryController
		var input = new CategoryInputDTO("name");
		var output = CreateCategoryUseCase(input);
		var jsonResult = CategoryPresenter(output).toJson();
		var xmlResult = CategoryPresenter(output).toXML();
```

<br>

---

## 1.6. Entities vs DDD

- Entities Clean Arq. <> Entities DDD
- - Clean Arq -> Uma camada de regras de negócio
- - DDD				-> Tem um ID único (identificador)
- Se aplicam em qualquer situação
- Não há definição de como devem ser criadas
- Táticas DDD p/ criar entities no Clean Arq
- Entities = Agregados + Domain Service

<br>

---

## 1.7. Relação com 'Notification Pattern'

> :bulb: **OpenIA:** "Explique resumidamente a relação do 'Notification Pattern' com a 'Clean Architecture'"
>
> O padrão de arquitetura limpa pode ser utilizado em conjunto com o Notification Pattern, que é um padrão de projeto que permite gerenciar notificações de erro ou sucesso em uma aplicação.
> 
> A ideia é que as entidades e os casos de uso possam gerar notificações quando algo acontece, e a camada de "Adapters" fica responsável por apresentar essas notificações ao usuário ou gravá-las em um log. O Notification Pattern é uma forma de manter a responsabilidade única das classes e promover a separação de interesses na aplicação. Além disso, ele ajuda a reduzir o acoplamento e aumentar a coesão do sistema. Em resumo, a utilização do Notification Pattern em conjunto com a arquitetura limpa pode ajudar a manter a consistência e a qualidade da aplicação.[^8]



[^1]: Curso FullCycle - Clean Architecture<br>
  Consultado em: 20/01/2023<br>
  Disponível em: https://plataforma.fullcycle.com.br

[^2]: The Clean Architecture<br>
  Consultado em: 05/04/2023<br>
  Disponível em: https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html

[^3]: OpenIA -> "Explique resumidamente o que é 'Clean Architecture'"<br>
  Consultado em: 05/04/2023<br>
  Disponível em: https://chat.openai.com/chat

[^4]: OpenIA -> "Explique resumidamente Camada de Entities, da 'Clean Architecture'"<br>
  Consultado em: 05/04/2023<br>
  Disponível em: https://plataforma.fullcycle.com.br

[^5]: OpenIA -> "Explique resumidamente Camada de Use Cases, da 'Clean Architecture'"<br>
  Consultado em: 05/04/2023<br>
  Disponível em: https://plataforma.fullcycle.com.br

[^6]: OpenIA -> "Explique resumidamente Camada de Adapters, da 'Clean Architecture'"<br>
  Consultado em: 05/04/2023<br>
  Disponível em: https://plataforma.fullcycle.com.br

[^7]: OpenIA -> "Explique resumidamente Camada de Frameworks e Drivers, da 'Clean Architecture'"<br>
  Consultado em: 05/04/2023<br>
  Disponível em: https://plataforma.fullcycle.com.br

[^8]: OpenIA -> "Explique resumidamente a relação do 'Notification Pattern' com a 'Clean Architecture"<br>
  Consultado em: 05/04/2023<br>
  Disponível em: https://plataforma.fullcycle.com.br