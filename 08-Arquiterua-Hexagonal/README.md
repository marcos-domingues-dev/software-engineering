# 1. Arquitetura hexagonal

> "Ports and Adapter"

<br>

---

- [1. Arquitetura hexagonal](#1-arquitetura-hexagonal)
  - [1.1. Ciclo de um projeto](#11-ciclo-de-um-projeto)
  - [1.2. Ciclo de muitos projetos](#12-ciclo-de-muitos-projetos)
  - [1.3. Reflexões importantes](#13-reflexões-importantes)
  - [1.4. Arquitetura vs Design de software](#14-arquitetura-vs-design-de-software)
  - [1.5. Camadas da arquitetura Hexagonal](#15-camadas-da-arquitetura-hexagonal)
  - [1.6. Dependency Inversion Principle](#16-dependency-inversion-principle)


<br>

---

<br>

> :bulb: **OpenIA:** "Explique resumidamente o que é 'Arquitetura hexagonal'"
> 
> A Arquitetura Hexagonal é um padrão de arquitetura de software que tem como objetivo separar a lógica de negócios do código relacionado à infraestrutura do sistema. Ela é composta por três camadas principais: a camada de aplicação, a camada de domínio e a camada de infraestrutura.
> 
> - A camada de domínio contém as regras de negócios e é independente de qualquer outra camada do sistema.
> - A camada de aplicação é responsável por orquestrar a lógica de negócios e é a única camada que tem conhecimento das outras duas camadas. 
> - A camada de infraestrutura é responsável por lidar com a comunicação externa, como a comunicação com bancos de dados e serviços externos.
> 
> A Arquitetura Hexagonal tem como benefícios principais a facilidade de testabilidade, manutenção e escalabilidade do sistema. Ela também torna o sistema mais flexível e adaptável a mudanças no ambiente em que está sendo utilizado.[^1]


<br>

---

## 1.1. Ciclo de um projeto

* Cresimento sustentável
* Software precisa se pagar ao longo do tempo
* Software deve ser desenhado por você e não pelo seu framework
* Peças precisam se encaixar e eventualmente serem substituídas

"Arquitetura diz respeito com o futuro do software."[^2]

---

<br>

## 1.2. Ciclo de muitos projetos
		
```
## FASE 1
- Banco de dados
- Cadastros
- Validações
- Servidor web
- Controllers
- Views
- Autenticação

## FASE 2
- Regras de negócio
- Criação de APIs
- Consumo de APIs
- Autorização
- Relatórios
- Logs

## FASE 3
- Mais acessos
- Upgrades de hardware
- Cache
- API parceiros
- Regras parceiros
- Relatórios

## Fase 4
- Mais acessos
- Upgrade de hardware
- DB Relatórios
- Comandos/Batch
- V2 da API

## FASE 5
- Escalar horizontal
- Sessões				-> Banco cache/Redis
- Uploads				-> várias máquinas, enviar p/ nuvem
- Refatoração
- Autoscaling
- CI/CD

## FASE 6
- GraphQL
- Bugs constantes
- Logs? Ops...
- Integração CRM
- Migração React

## FASE 7
- Inconsistência CRM
- Containers
- CI/CD
- Memória
- Logs
- Se livrar do legado

## FASE 8
- Microserviços
- DB Compartilhado
- Problemas com tracing
- Lentidão ( dupla latência )
- Custo elevado

## FASE 9
- Kubernetes
- CI/CD
- Mensageria
- Perda de mensagens
- Consultorias

## FASE 10
- Use a imaginação!
		
------------------------------
```

---

<br> 

## 1.3. Reflexões importantes

	* Principais Problemas
		- Visão de futuro
		- Limites bem definidos
		- Troca a adição de componentes
		- Escala horizontal
		- Otimizações frequentes ( débito técnico )
		- Mudanças - Camada anti corrupção (ACL) - CRM, Gateway, SW Terceiros, etc
	
	REFLEXÕES
	* Está sendo doloroso?
	* Poderia ter sido evitado?
	* O software está se pagando?
	* Será que a relação com o cliente está legal?	
	* O cliente terá prejuízo com a mudança brusca?
	* Em qual momento tudo se perdeu?
	* Se fosse novo na equipe, você julgaria os devs que fizeram tudo?

---

<br>

## 1.4. Arquitetura vs Design de software
	
> "Atividades relacionadas  a arquiteutura de software são sempre de design.
> Entretanto, nem todas atividades de design são sobre arquitetura.
> 
> O objetivo primário da arquitetura é garantir que 
> - os atributos de qualidade, 
> - as restrições de alto nível e
> - os objetivos de negócio
> sejam atendidos pelo sistema.
> 
> Qualquer decisão de design que não tenha relação com este objetivo não é arquitetural.
> 
> Todas as decisões de design para um componente que não sejam "visíveis" fora dele, geralmente, também não são."
> 	 
> Fonte: Elemar Jr.

---

<br>

## 1.5. Camadas da arquitetura Hexagonal

> 'Hexagonal' sides

| **[Left]** -> | **[Core]**      -> | **[Right]** |
| :-------- | :------------- | :------ |
| Client -> | Application -> | Infra   |

---

<br>

## 1.6. Dependency Inversion Principle

* Modulos de alto nivel não devem depender de módulos de baixo nível.Ambos devem depender de abstrações.

* Abstrações não devem depender de detalhes. Detalhes devem depender de abstrações.



[^1]: OpenIA -> "Explique resumidamente o que é 'Arquitetura hexagonal'"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 04/04/2023

[^2]: Curso FullCycle - Arquitetura hexagonal<br>
  Consultado em: 11/01/2023<br>
  Disponível em: https://plataforma.fullcycle.com.br