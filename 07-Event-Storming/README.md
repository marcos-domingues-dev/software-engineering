# 1. Event storming

- [1. Event storming](#1-event-storming)
  - [1.1. Eventos e comandos](#11-eventos-e-comandos)
  - [1.2. Atores](#12-atores)
  - [1.3. Pontos de decisão e policies](#13-pontos-de-decisão-e-policies)
  - [1.4. Origem dos eventos](#14-origem-dos-eventos)
  - [1.5. Entendendo o surgimento de Agregados](#15-entendendo-o-surgimento-de-agregados)
  - [1.6. Agregados, fluxos e bounded contexts](#16-agregados-fluxos-e-bounded-contexts)
  - [1.7. Contextos e Microsserviços](#17-contextos-e-microsserviços)

<br>

> :bulb: **OpenIA:** "Explique resumidamente o que é 'Event storming'"
> 
> Event Storming é uma técnica de modelagem colaborativa de domínio que envolve a colaboração de pessoas de diferentes áreas de conhecimento, incluindo especialistas de domínio, desenvolvedores, designers e outras partes interessadas no projeto. Durante uma sessão de Event Storming, cada participante é atribuído a um papel específico que é crucial para o processo de modelagem. Esses papéis são:
> - Facilitador: responsável por conduzir a sessão e garantir que a discussão flua sem problemas.
> - Especialista de domínio: uma pessoa com profundo conhecimento sobre o domínio que está sendo modelado e é responsável por explicar os conceitos complexos.
> - Participante ativo: qualquer pessoa que esteja participando da sessão e contribuindo com ideias.
> - Observador: um participante que não está diretamente envolvido na discussão, mas está observando e fazendo anotações.
>
> Os papéis são projetados para ajudar a manter a discussão focada e garantir que todas as perspectivas sejam consideradas durante o processo de modelagem. A colaboração de pessoas com diferentes conhecimentos e perspectivas é fundamental para a criação de um modelo de domínio preciso e completo.[^1]

<br>

---

## 1.1. Eventos e comandos

> :bulb: **OpenIA:** "Explique resumidamente o que são 'Eventos e comandos', em Event storming"
> 
> No Event Storming, eventos e comandos são duas partes importantes do fluxo de informações no domínio. Os eventos representam as ocorrências importantes que acontecem no domínio, enquanto os comandos representam as ações que o sistema pode executar em resposta a esses eventos.
> 
> Os eventos são representados por cartões coloridos e organizados em uma linha do tempo. Cada evento representa uma mudança de estado em uma entidade, agregado ou serviço do domínio. Por outro lado, os comandos são as ações que podem ser executadas no domínio para causar eventos. Eles podem ser representados por cartões brancos e organizados em uma outra linha do tempo.
> 
> Ao identificar eventos e comandos, os participantes podem entender melhor o fluxo de informações no domínio e as relações causais entre os eventos e comandos. Eles também podem identificar as entidades, agregados e serviços do domínio que são afetados pelos comandos e eventos. A técnica de Event Storming pode ser usada para modelar e visualizar a arquitetura de um sistema baseado em eventos, o que pode ajudar na tomada de decisões de design e implementação..[^2]

<br> 

Mapear e entender através de EVENTOS gerados pelo sistema.

```
	------------------------------
	EVENTO:
		
		[Orange Card]
		Event "Item added to cart"
		
		- Past Tense (Acontece no Passado)
		- Sinaliza o fim de uma etapa
	
	------------------------------
	COMANDO:
		[Blue Card]
		Command ...: FinalizarCompraCommand
		Event .....: CompraFinalizadaEvent
```

Outros exemplos:

```
	------------------------------
	Eventos (No passado)
	- Vídeo criado
	- Categoria criada
	- Plano de assinatura criado
	- Assinatura aprovada
	- Upload do vídeo realizado
	- Genero Criado
	- Cliente criado
	- Assinatura rejeitada
	- Vídoe publicado
	- Vídeo assistido
	
	------------------------------
	Comandos
	- Criar vídeo
	- Fazer uploado
	- Publicar vídeo
	- Criar cast member
	- Criar gênero
	
	------------------------------
```

<br>

---

## 1.2. Atores

<br>

> :bulb: **OpenIA:** "Explique resumidamente o que são 'Atores', em Event storming"
> 
> No Event Storming, os atores são as pessoas, sistemas ou dispositivos que interagem com o domínio. Eles são representados por cartões de cor laranja e colocados em uma linha horizontal acima dos eventos e comandos.
> 
> Os atores podem ser usuários finais do sistema, outros sistemas externos, dispositivos físicos ou qualquer outra coisa que interaja com o domínio. Identificar e mapear os atores é importante para entender como o sistema se encaixa no contexto mais amplo em que está sendo usado.
> 
> Ao modelar os atores em um Event Storming, os participantes podem entender melhor como diferentes partes do sistema se comunicam e interagem com os usuários finais e outros sistemas. Isso pode ajudar a identificar oportunidades para melhorar a usabilidade do sistema e integrá-lo mais efetivamente com outros sistemas no ambiente em que está sendo usado.[^3]

<br>

---

## 1.3. Pontos de decisão e policies
	
[Green Card] Read Model - Dados para tomada de decisão
	
[Rocho Card] Whenever - Policy
- "Quando algo acontecer, faça isso. (Ex E-mail)"

```
POLICY
	Assinatura iniciada	Event ->	Envia dados de pagto para Gateway
		Assinatura Aprovada Event
		Assinatura Rejeitada Event 
```

<br>

---

## 1.4. Origem dos eventos

De onde os eventos podem surgir ?

- Através de um commando executado por um cliente
- Através de um sistema externo ( Gateway de pagto - Paypal )
- Através de agendamento ( envio de e-mail )
- Através de uma Policy ( após concluir, aciona um evento )

<br>

---

## 1.5. Entendendo o surgimento de Agregados

- Sempre entre um 'Comando' e um 'Evento' tem um AGREGADO
- Regras de Negócio	
- - Quem é responsável por este comando?
- - Aggregados: Categoria, Genero, Cliente, Plano de Assinatura

<br>

---

## 1.6. Agregados, fluxos e bounded contexts

```
Actor > Command > External System	    > EventA	> Policy
                > Aggregate Busin Rule > EventA   > Query Model
```

```
	--(Delimitador de Contexto)--
	
	[User] Administrador de Vídeos
		[Command] Fazer Upload de vídeo
			[Aggregado] Video
				[Event] Upload de vídeo realizado
			
	--(Delimitador de Contexto)--

	[Policy] Conversão de vídeo
		[Aggregado] JobVideo
			[Event] Vídeo convertido
				[Model] Status do vídeo

	--(Delimitador de Contexto)--
```

<br>

---
## 1.7. Contextos e Microsserviços

| Contextos          | Tipo                                          |
| :----------------- | :-------------------------------------------- |
| Adm videos         | Auxilio                                       |
| Catálogo de videos | Domínio principal                             |
| Pagamento          | Auxilio                                       |
| Gateway            | Genérico (de prateleira, permite troca facil) |


[^1]: OpenIA -> "Explique resumidamente o que é 'Event storming'"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 04/04/2023

[^2]: OpenIA -> "Explique resumidamente o que são 'Eventos e comandos', em Event storming"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 04/04/2023

[^3]: OpenIA -> "Explique resumidamente o que são 'Atores', em Event storming"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 04/04/2023
