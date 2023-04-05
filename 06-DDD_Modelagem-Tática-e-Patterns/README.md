# 1. DDD: Modelagem Tática e Patterns

---

- [1. DDD: Modelagem Tática e Patterns](#1-ddd-modelagem-tática-e-patterns)
  - [1.1. Elementos táticos](#11-elementos-táticos)
    - [1.1.1. Entities](#111-entities)
    - [1.1.2. Value objects](#112-value-objects)
    - [1.1.3. Agregates](#113-agregates)
    - [1.1.4. Domain services](#114-domain-services)
    - [1.1.5. Repositories](#115-repositories)
    - [1.1.6. Domain events](#116-domain-events)
    - [1.1.7. Modules](#117-modules)
    - [1.1.8. Factories](#118-factories)


<br>

---

## 1.1. Elementos táticos

Os elementos táticos do Domain-driven design surgem quando precisamos olhar mais afundo um bounded context. Modelarmos componentes, comportamentos e individualidades	e suas relações.[^1]

<br>

---

### 1.1.1. Entities

Uma entidade é algo único que é capaz de ser alterado de forma contínua durante um longo período de tempo. Uma entidade é algo que possui uma continuidade em seu siclo de vida e pode ser distinguida independente de seus atributos.

`Entidade = IDENTIDADE`

DTO - Transferir dados de uma camada para outra

Modelagem ORM - Preso no 'ORM' -> Customer.ID

Entidade anêmica
- ID único
- Getters & Setters

Modelagem de domínio rico
- ID
- Valores que alteram durante o tempo
- Comportamento
- Regras de Negócio -> Mudar o Comportamento
- - Validações
- - Exceção
- - Fórmulas

Regras de negócio
- Quais comportamentos?
- O que muda na entidade?
- Qual o motivo de negócio?

Consistência constante em primeiro lugar
- Uma entidade deve representar SEMPRE o estado correto e atual do elemento.
- Os campos obrigatórios estão 100% preenchidos.
- Permite confiar que ao aplicar uma regra de negócio, a entidade está 100% consistente.

Princípio da autovalidação
- Uma entidade SEMPRE vai ter que se autovalidar.
- Não permitir alterar atributos via 'setter'.

<br>

> :bulb: **OpenIA:** "Explique resumidamente o que é uma Entity, em Domain-driven design"
> 
> Entity é um dos principais elementos do Domain-Driven Design (DDD). Ela é um objeto distintivo que possui uma identidade única e é reconhecido por suas características, não por seus atributos. Além disso, é capaz de mudar de estado ao longo do tempo e deve ser modelada para refletir as regras de negócio do domínio em que está inserida. As operações em uma entidade são normalmente realizadas por um repositório.[^2]

<br>

---

### 1.1.2. Value objects

- Quando vc se preocupa apenas com os atributos de um elemento (sem métodos).
- Trate um value object como imutável.

```
	Exemplo-01:
		Address
			Street
			City
			State
			ZipCode
```

		Pergunta:	"Existe possibilidade de trocar apenas o 'State',
		sem alterar outros atributos?"
		
		Resposta: "Não se muda de ZipCode, mas de 'Address'."

<br>

> :memo: **PONTOS DE VALUE OBJECTS:** 
> - Sempre coeso - se autovalidando
> - Não tem um ID
> - Imutável

<br>

> :bulb: **OpenIA:** "Explique resumidamente o que é um Value object, em Domain-driven design"
> 
> Value object é um objeto que representa um valor ou conjunto de valores e não possui identidade própria. Em outras palavras, ele é definido pelos seus atributos e não por uma chave única. Por isso, eles são imutáveis e podem ser compartilhados por várias entidades e agregados. O objetivo é modelar conceitos de negócio que não possuem uma identidade própria, mas são importantes para o domínio.[^3]

<br>

---

### 1.1.3. Agregates

O aggregate é um conjunto de objetos associados que tratamos como uma unidade para propósito de mudança de dados.

Agregados são conjuntos de Entidades, Objetos de Valor e outros...

- Faz sentido um Endereço sem Cliente?
- Faz sentido um ItemDeOrdem sem OrdemServico ?

<br>

> :bulb: **OpenIA:** "Explique resumidamente o que é um Agregate, em Domain-driven design"
> 
> Aggregate é um conjunto de objetos relacionados que são tratados como uma unidade coesa no Domain-Driven Design (DDD). Ele é composto por uma entidade raiz (Root Entity) e um ou mais objetos de valor e/ou entidades relacionadas. O objetivo é simplificar a modelagem de domínios complexos, garantir a consistência das operações realizadas no aggregate e reduzir a necessidade de acessar objetos relacionados de forma direta. O acesso aos objetos dentro de um aggregate é feito por meio da entidade raiz.[^4]

<br>

---

### 1.1.4. Domain services

Um serviço de domínio é uma operação sem estado que cumpre uma tarefa específica de um domínio. Muitas vezes, a melhor indicação de que você deve criar um Serviço no modelo de domínio é quando a operação que você precisa executar não se encaixar como um método em um Agregado ou um Objeto de Valor.

Quando um processo ou transformação significativa no domínio não for uma responsabilidade natural de uma ENTIDADE ou OBJETO DE VALOR, adicione uma operação ao modelo como uma interface autônoma declarada como um SERIÇO. Defina a interface em baseada na linguagem do modelo de domínio e certifique-se de que o nome da operação faça parte do UBIQUITOUS LANGUAGE. Torne o SERVIÇO sem estado.

- Como realizar uma operação em lote?
- Como calcular algo cuja as informações constam em mais de uma entidade?

<br>

> :memo: **Cuidados:** 	 
> * Quando houver muitos "Domain Services", TALVEZ, isso pode indicar que seus agregados estão anêmicos.
> * Domain services são 'Stateless' ( não deve possuir atributos )

<br>

> :bulb: **OpenIA:** "Explique resumidamente o que é um domain service, em Domain-driven design"
> 
> Domain Service é um elemento importante do Domain-Driven Design (DDD) que representa um serviço relacionado ao domínio. Ele é responsável por realizar operações complexas que não se encaixam em uma única entidade ou agregado. Essas operações normalmente envolvem múltiplas entidades ou agregados e, portanto, não podem ser realizadas por nenhum deles isoladamente. O Domain Service é uma forma de modelar essas operações dentro do domínio e garantir que a lógica de negócio seja implementada de forma adequada.[^5]

<br>

---

### 1.1.5. Repositories

- Crie um repositório para cada 'Agregado'
- Quando recuperar os dados do banco de dados eles devem estar no mesmo estado.

```typescript
	export default interface RepositoryInterface<T> {
		create(entity: T): Promise<void>;
		update(entity: T): Promise<void>;
		find(id: string): Promise<T>;
		findAll(): Promise<T[]>;
	}
```

Entendendo camada de Infra
```
src\domain\repository
src\infrastructure\db\sequelize\model
```

<br>

> :bulb: **OpenIA:** "Explique resumidamente o que é um Repository, em Domain-driven design"
> 
> Repository é um padrão de projeto comummente utilizado no Domain-Driven Design (DDD) para encapsular a lógica de acesso a dados em um único lugar. Ele representa uma camada de abstração entre a aplicação e a persistência de dados, permitindo que as entidades sejam tratadas independentemente da forma como estão armazenadas. O objetivo é simplificar o acesso a dados e desacoplar a lógica de negócio da implementação de persistência. O Repository é responsável por fornecer métodos para persistir, recuperar, atualizar e excluir entidades, permitindo que a aplicação trabalhe com objetos de domínio em vez de dados brutos.[^6]

<br>

---

### 1.1.6. Domain events

Use um evento de domínio para capturar uma ocorrência de algo que aconteceu no domínio.

Todo evento deve ser representado em uma 'ação realizada no passado'.

Exemplos:
- UserCreated
- OrderPlaced
- EmailSent

Deve ser utilizado quando queremos notificar outros Bounded Contexts de uma mudança de estado

Pattern:
- Event: possui os dados do evento
- Handler: executa o processamento quando o evento é chamado
- Event Dispatcher: responsável por armazenar e executar os handlers de um evento quando ele for chamado

<br>

> :bulb: **OpenIA:** "Explique resumidamente o que são 'Domain events', em Domain-driven design"
> 
> Domain Events são eventos que ocorrem dentro do domínio do problema, no contexto do Domain-Driven Design (DDD). Eles representam uma técnica para comunicar mudanças relevantes no estado das entidades do domínio para outros componentes do sistema. O objetivo é garantir que as mudanças relevantes do estado do domínio sejam propagadas para outras partes da aplicação sem que a lógica de negócio precise se preocupar com detalhes de implementação. O Domain Event é uma forma de desacoplar os componentes e promover uma arquitetura de sistemas distribuídos.[^7]

<br>

---

### 1.1.7. Modules

Servem como containers de classes altamente coesas entre si. Objetivo de ter baixo acoplamento entre classes de módulos diferentes.

> 'Bounded Context'	> Moules

- Respeitar linguagem Universal (Ubíqua). O módulo deve representar o 'Bounded Context'	
- Baixo acomplamento
- Um ou mais agregados devem estar junto somente se faz sentido
- Organizado pelo domínio/Subdomínio

<br>

> :bulb: **OpenIA:** "Explique resumidamente o que são 'Modules', em Domain-driven design"
> 
> Em Domain-Driven Design (DDD), módulos são uma forma de organizar o código da aplicação em partes coesas e independentes. Eles representam uma maneira de dividir o domínio em partes menores e mais gerenciáveis, cada uma com sua própria responsabilidade. O objetivo é reduzir a complexidade da aplicação e promover uma arquitetura modular que possa ser facilmente mantida e estendida. Cada módulo deve ter uma interface clara e bem definida, com suas próprias entidades, serviços e repositórios. Isso permite que cada módulo seja desenvolvido e testado independentemente, facilitando a integração e reduzindo os problemas de acoplamento.[^8]

<br>

---

### 1.1.8. Factories

A responsabilidade de criar instâncias de objetos complexos e AGREGADOS deve ser deslocada para uma classe, que não faz parte do modelo de dominio,  faz parte do design do domínio.
	
Crie AGREGADOS inteiros de uma única vez.

<br>

> :bulb: **OpenIA:** "Explique resumidamente o que são 'Factories', em Domain-driven design"
> 
> Em Domain-Driven Design (DDD), Factories são um padrão de projeto utilizado para criar objetos complexos. Eles são responsáveis por encapsular a lógica de criação de objetos e tornar essa tarefa mais simples e flexível. O objetivo é permitir que os objetos sejam criados de forma mais expressiva e declarativa, sem a necessidade de expor detalhes de implementação. As Factories são particularmente úteis para a criação de objetos que requerem informações adicionais ou validação antes de serem criados. Elas também podem ser utilizadas para abstrair a criação de objetos e reduzir o acoplamento entre diferentes partes do sistema.[^9]

[^1]: Curso FullCycle - DDD: Modelagem Tática e Patterns<br>
  Consultado em: 11/01/2023<br>
  Disponível em: https://plataforma.fullcycle.com.br

[^2]: OpenIA -> "Explique resumidamente o que é uma Entity, em Domain-driven design"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 04/04/2023

[^3]: OpenIA -> "Explique resumidamente o que é um Value object, em Domain-driven design"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 04/04/2023

[^4]: OpenIA -> "Explique resumidamente o que é um Agregate, em Domain-driven design"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 04/04/2023

[^5]: OpenIA -> "Explique resumidamente o que é um domain service, em Domain-driven design"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 04/04/2023

[^6]: OpenIA -> "Explique resumidamente o que é um Repository, em Domain-driven design"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 04/04/2023

[^7]: OpenIA -> "Explique resumidamente o que são 'Domain events', em Domain-driven design"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 04/04/2023

[^8]: OpenIA -> "Explique resumidamente o que são 'Modules', em Domain-driven design"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 04/04/2023

[^9]: OpenIA -> "Explique resumidamente o que são 'Factories', em Domain-driven design"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 04/04/2023