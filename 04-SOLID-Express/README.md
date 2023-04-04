# SOLID

| #    | SIGLA | DESCRIÇÃO                       |
| :--- | :---- | :------------------------------ |
| S    | SRP   | Single Responsability Principle |
| O    | OCP   | Open-Closed Principle           |
| L    | LSP   | Liskov Substituition Principle  |
| I    | ISP   | Interface Segregation Principle |
| D    | DIP   | Dependency Inversion Principle  |

<br> [^1]
---

## SRP - Single Responsability Principle

Uma classe deve ter apenas uma responsabilidade.

> "A classe deve ter apenas um motivo para ser alterada."

---

## OCP - Open-Closed Principle

> Aberta para extensão, fechada para alterações.
	
	class Video
		class Movie extends Video
		class TVShow extends Video

---

## LSP - Liskov Substituition Principle

Bárbara Liskov
	
> Subclasses podem ser substituídas pela classe pai.

---

## ISP - Interface Segregation Principle

> "Uma classe não é obrigada a implementar uma interface que ela não utilizará"

---

## DIP - Dependency Inversion Principle

> Não criar instâncias ( new MyClass ) dentro de classes,	passar parâmetro, no construtor.

---

<br>

> :bulb: **OpenIA:** "Me explique resumidamente o que é SOLID"
> 
> SOLID é um acrônimo que representa cinco princípios fundamentais da programação orientada a objetos que foram estabelecidos por Robert C. Martin. Eles são amplamente utilizados na Engenharia de Software para criar sistemas flexíveis, fáceis de manter e escaláveis.
> Os cinco princípios do SOLID são:
> 
> 1. Princípio da Responsabilidade Única (Single Responsibility Principle - SRP): cada classe deve ter uma única responsabilidade.
> 2. Princípio do Aberto/Fechado (Open/Closed Principle - OCP): as classes devem ser abertas para extensão e fechadas para modificação.
> 3. Princípio da Substituição de Liskov (Liskov Substitution Principle - LSP): as classes derivadas devem ser substituíveis pelas classes base.
> 4. Princípio da Segregação de Interfaces (Interface Segregation Principle - ISP): as interfaces devem ser segregadas para que as classes não implementem funcionalidades desnecessárias.
> 5. Princípio da Inversão de Dependência (Dependency Inversion Principle - DIP): as classes de nível superior não devem depender das classes de nível inferior, mas sim de abstrações.
> 
> Em resumo, o SOLID é um conjunto de cinco princípios da programação orientada a objetos que são amplamente utilizados na Engenharia de Software para criar sistemas flexíveis, fáceis de manter e escaláveis. Eles são a Responsabilidade Única, Aberto/Fechado, Substituição de Liskov, Segregação de Interfaces e Inversão de Dependência. Cada princípio ajuda a manter um código bem organizado e de fácil manutenção.[^2]

<br>

[^1]: Curso FullCycle - Arquitetura de Software<br>
  Consultado em: 06/01/2023<br>
  Disponível em: https://plataforma.fullcycle.com.br

[^2]: OpenIA -> "Apresente resumidamente o que é SOLID"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 01/04/2023