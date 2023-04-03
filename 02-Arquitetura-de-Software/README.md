# 1. Arquitetura de Software

- [1. Arquitetura de Software](#1-arquitetura-de-software)
  - [1.1. Tipos de Arquitetura](#11-tipos-de-arquitetura)
    - [1.1.1. Arquitetura corporativa](#111-arquitetura-corporativa)
    - [1.1.2. Arquitetura de solução](#112-arquitetura-de-solução)
    - [1.1.3. Arquitetura tecnológica](#113-arquitetura-tecnológica)
    - [1.1.4. Arquitetura de software](#114-arquitetura-de-software)
  - [1.2. Papel do Arquiteto de Software](#12-papel-do-arquiteto-de-software)
  - [1.3. Por que Arquiteto de Software](#13-por-que-arquiteto-de-software)
  - [1.4. Arquitetura vs Design](#14-arquitetura-vs-design)
  - [1.5. Sustentabilidade no dia zero](#15-sustentabilidade-no-dia-zero)
  - [1.6. Pilares da arquitetura de software](#16-pilares-da-arquitetura-de-software)
  - [1.7. Requisitos arquiteturais - (RAs)](#17-requisitos-arquiteturais---ras)

<br>

---

## 1.1. Tipos de Arquitetura

As organizações normalmente separam as funções de arquitetura em:
- Arquitetura corporativa
- Arquitetura de solução
- Arquitetura tecnológica
- Arquitetura de software

<br>

---

### 1.1.1. Arquitetura corporativa

A arquitetura corporativa é a prática de aplicar um método compreensivo e rigoroso, para descrever uma estrutura para um processo organizacional, presente ou futuro; ou Sistemas de Informação. [^1]

Ela tem a função de avaliar estrategicamente a organização como um todo. [^2]

Principais atribuições da arquitetura corporativa de sistemas de informação:
- Avaliação de custos
- Avaliação de novas tecnologias
- Padronização de tecnologia
- Planejamento de grandes implantações
- Sistemas core
- Migrações

<br>

> :bulb: **OpenIA:** "Apresente resumidamente o que é arquitetura corporativa"
> 
> A arquitetura corporativa é um conjunto de práticas e padrões utilizados pelas empresas para gerenciar e alinhar seus processos de negócios, sistemas de informação e tecnologia. Ela visa garantir que todos os sistemas, dados e processos de negócios estejam alinhados com a estratégia geral da organização, sejam eficientes e eficazes, e que a empresa possa tomar decisões informadas sobre investimentos em tecnologia. A arquitetura corporativa geralmente inclui várias camadas, como a camada de negócios, camada de aplicativos, camada de dados e camada de tecnologia.[^3]

[^1]: A arquitetura arquitetura corporativa<br>
  Disponível em: https://pt.wikipedia.org/wiki/Arquitetura_empresarial<br>
  Consultado em: 01/04/2023

[^2]: Curso FullCycle - Arquitetura de Software<br>
  Consultado em: 01/10/2022<br>
  Disponível em: https://plataforma.fullcycle.com.br

[^3]: OpenIA -> "Apresente resumidamente o que é arquitetura corporativa"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 01/04/2023

<br>

---

### 1.1.2. Arquitetura de solução
	
Arquitetura de solução fica entre a área técnica e área de negócios e busca	transformar requisitos de negócio em soluções de software. Realiza desenhos arquiteturais da solução utilizando tecnologias como C4, UML, BPMN, etc.
Também analisa os impactos comerciais de escolha tecnológica, faz reuniões com comercial em pré-venda, análise de custos, acompanhamento de implantação, ,igração, etc. [^2]

<br>

> :bulb: **OpenIA:** "Apresente resumidamente o que é arquitetura de solução"
> 
> A arquitetura de solução é uma abordagem para projetar sistemas de software que atendam aos requisitos específicos de um problema ou necessidade. Ela inclui a definição de componentes de software, suas interações e o ambiente em que o software será executado. A arquitetura de solução é geralmente aplicada em um contexto de projeto específico e é criada a partir de uma arquitetura de referência. Ela é projetada para fornecer uma estrutura para a implementação e manutenção de soluções de software escaláveis e flexíveis.[^4]

[^4]: OpenIA -> "Apresente resumidamente o que é arquitetura de solução"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 01/04/2023

<br>

---

### 1.1.3. Arquitetura tecnológica

Dentro das empresas, a arquitetura tecnológica é a especialidade em tecnologias específicas de mercado.
Exemplos de especialidades tecnológicas:
		- Arquiteto Elastic
		- Arquiteto Java
		- Arquiteto Oracle	
As certificações são uma forma de garantir a especialização de uma tecnologia por parte de um profissional [^2].

<br>

> :bulb: **OpenIA:** "Apresente resumidamente o que é arquitetura tecnológica"
> 
> A arquitetura tecnológica em Engenharia de Software é um conceito fundamental para o desenvolvimento de sistemas complexos. Ela se refere à estruturação dos componentes tecnológicos de um sistema, como hardware, software, redes e bancos de dados, para que possam trabalhar juntos de forma eficiente e eficaz. A arquitetura tecnológica também está relacionada à escolha das ferramentas e tecnologias adequadas para implementar um sistema. É importante que a arquitetura tecnológica seja planejada cuidadosamente para garantir que o sistema seja escalável, seguro e confiável. Um dos principais objetivos da arquitetura tecnológica é garantir que o sistema seja facilmente mantido e atualizado ao longo do tempo.

<br>

---

### 1.1.4. Arquitetura de software

A arquitetura de software é uma disciplina da engenharia de software, ligada ao desenvolvimento de aplicações que é impactada pela estrutura organizacional. Em grandes empresas, é comum a formação de times específicos para tratar da estrutura de componentes de software.[^2]

<br>

> :memo: **Arquiteura é sempre design. Design nem sempre é arquitetura.** 
> 
> O objetivo da prática de arquitetura de software é maximizar as entregas reduzindo o esforço para atingir essas entregas.
>
> `Produtividade = Desempenho / Empenho`
> 
> Ela busca garantir que os objetivos do negócio, os atributos de qualidade e as restrições de alto nível sejam atendidos durante o processo de desenvolvimento.
> 
> As decisões de design de arquitetura de software são aquelas que buscam garantir que objetivos do negócio, os atributos de qualidade e as restrições de alto nível sejam atendidos.[^5]
> 
> <p style="text-align:right">Elemar Junior - Canal EximiaCo</p>

<br>

> :bulb: **OpenIA:** "Apresente resumidamente o que é arquitetura de software"
> 
> Arquitetura de software é a estruturação dos componentes de um sistema de software e suas interações, que determina suas propriedades e comportamentos. É responsável por definir a organização dos módulos, as interfaces entre eles, as decisões de design e as restrições do sistema. O objetivo da arquitetura de software é garantir que o sistema seja confiável, escalável, seguro, eficiente e fácil de manter. Ela também ajuda a mitigar riscos e a tomar decisões fundamentadas em relação ao desenvolvimento e evolução do sistema ao longo do tempo.[^6]

[^5]: Canal EximiaCo: O que é Arquitetura de Software?<br>
  Disponível em: https://www.youtube.com/watch?v=jUH5lKfpWE0&t=300s<br>
  Consultado em: 01/04/2023

[^6]: OpenIA -> "Apresente resumidamente o que é arquitetura de software<br>
  Disponível em: https://www.youtube.com/watch?v=jUH5lKfpWE0&t=300s<br>
  Consultado em: 01/04/2023

<br>

---

## 1.2. Papel do Arquiteto de Software

- Transformar requisitos em padrões arquiteturais
- Orquestrar pessoas desenvodres e experts de domínio
- Entender de forma profunda conceitos e modelos arquiteturais
- Auxilia na tomada de decisão nos momentos de crise
- Reforça boas práticas de desenvolvimento
- Solid, Teste, Eventos, Clean Arquitecture, etc
- Code Reviews
- Identifica Pontos críticos

<br>

---

## 1.3. Por que Arquiteto de Software

- Navegar do macro para micro
- Entender opções e escolher a melhor
- Pensar no longo prazo
- Escolher tecnologias, não por ser 'hype'
- Padrões de Projetos e Boas Práticas
- Clareza do IMPACTO POSITIVO
  "que o software possui na organização como um todo".
  "Sentimento de Valor".
  "Pertencimento".
  "Resultado".
- Falta de Segurança pode 'congelar a carreira'
- Aprender arquitetura proporciona CONFIANÇA

<br>

---

## 1.4. Arquitetura vs Design

	- Arquitetura ...: Escopo Global ou alto nível
	- Design ........: Escopo Local
	
	Arquitetura: objetivo primário
		Atributos de qualidade
		Restrições de alto nível
		Objetivos de negócio

	É "Visível de fora" ? Arquitetura
	NÃO é "Visível de fora" ? Design

<br>

---

## 1.5. Sustentabilidade no dia zero

- Software é caro
- Software resolve uma "dor"
- Software precisa se pagar ao longo do tempo
- Acompanhar evolução
- Longevidade

"'Breakeven' significa o momento de equilíbrio da sua empresa,
ou seja, quando custos e despesas operacionais se igualam à receita."

<br>

---

## 1.6. Pilares da arquitetura de software

- Estrutura
- Componentização
- Relacionamento
- Governança - (padrões, regras, documentação, onboarding, etc)

<br>

---

## 1.7. Requisitos arquiteturais - (RAs)

- Performance
- - 500ms por requisição
- - 50 Transações por segundo
- Armazenamento de Dados
- Escalabilidade
- Segurança
- Legal
- Auditoria