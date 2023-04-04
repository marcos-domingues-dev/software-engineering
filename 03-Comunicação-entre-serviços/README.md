# 1. Comunicação entre serviços

> Tecnologias de comunicação:
> - REST
> - gRPC
> - GraphQL
> 	
> Tecnologias relacionadas: Service Discovery e Consul

<br>

> Tipos de comunicação:
> - Comunicaçao Síncrona
> - Comunicaçao Assíncrona
> 
> Tecnologias Assíncronas: RabbitMQ, Kafka, etc

<br>[^1]

---

- [1. Comunicação entre serviços](#1-comunicação-entre-serviços)
	- [1.1. REST](#11-rest)
		- [1.1.1. Níveis de maturidade](#111-níveis-de-maturidade)
			- [1.1.1.1. Richardson Maturity Model](#1111-richardson-maturity-model)
			- [1.1.1.2. "Verbos HTTP com representatividade"](#1112-verbos-http-com-representatividade)
			- [1.1.1.3. Utilização de "resources"](#1113-utilização-de-resources)
		- [1.1.2. Method e Content Negotiation](#112-method-e-content-negotiation)
			- [1.1.2.1. Uma boa API REST](#1121-uma-boa-api-rest)
			- [1.1.2.2. HAL, Collection+JSON e Siren](#1122-hal-collectionjson-e-siren)
			- [1.1.2.3. REST: HAL](#1123-rest-hal)
			- [1.1.2.4. REST: Http Method Negotiation](#1124-rest-http-method-negotiation)
			- [1.1.2.5. REST: Content Negotiation - Accept Negotiation](#1125-rest-content-negotiation---accept-negotiation)
			- [1.1.2.6. REST: Content Negotiation - Content Type Negotiation](#1126-rest-content-negotiation---content-type-negotiation)
	- [1.2. gRPC](#12-grpc)
		- [1.2.1. Características - Em quais casos podemos utilizar ?](#121-características---em-quais-casos-podemos-utilizar-)
		- [1.2.2. LINKS](#122-links)
		- [1.2.3. Linguagens](#123-linguagens)
		- [1.2.4. Protocol Buffers](#124-protocol-buffers)
		- [1.2.5. REST vs gRPC](#125-rest-vs-grpc)
	- [1.3. GraphQL](#13-graphql)
		- [1.3.1. Vantagens](#131-vantagens)
	- [1.4. Comunicaçao Síncrona](#14-comunicaçao-síncrona)
	- [1.5. Comunicaçao Assíncrona](#15-comunicaçao-assíncrona)
	- [1.6. Service Discovery](#16-service-discovery)
		- [1.6.1. Consul](#161-consul)
			- [1.6.1.1. Consul - Service registry](#1611-consul---service-registry)
			- [1.6.1.2. Consul - Health check Ativo](#1612-consul---health-check-ativo)
			- [1.6.1.3. Consul - Multicloud - ( multiregião )](#1613-consul---multicloud----multiregião-)
			- [1.6.1.4. Agent: Client \& Server](#1614-agent-client--server)
			- [1.6.1.5. Consul client](#1615-consul-client)
			- [1.6.1.6. Consul Server](#1616-consul-server)
			- [1.6.1.7. Consul - Dev Mode](#1617-consul---dev-mode)

---

## 1.1. REST

REST -> Representational State of Transfer
- Dissertação de Doutorado -> Roy Fielding
- Simplicidade com http
- Totalmente STATELESS
- Necessário passar um Token para cada requisição
- Cacheável
<br>[^1]

<br>

> :bulb: **OpenIA:** "Me explique resumidamente o que é REST"
> 
> REST (Representational State Transfer) é um estilo arquitetural para sistemas web, que consiste em um conjunto de restrições e propriedades. É amplamente utilizado para projetar APIs (Interfaces de Programação de Aplicativos) na Engenharia de Software. O estilo REST envolve uma arquitetura cliente-servidor, onde o cliente envia uma solicitação HTTP (Hypertext Transfer Protocol) para o servidor, que retorna uma resposta HTTP. Além disso, o REST usa recursos (como documentos, imagens ou vídeos) identificados por URLs (Uniform Resource Locators) para lidar com as solicitações.
>
> As restrições REST incluem a interface uniforme, a separação de preocupações, a escalabilidade, a visibilidade e a confiabilidade. A interface uniforme significa que as solicitações HTTP devem incluir informações suficientes para o servidor entender e processar a solicitação. A separação de preocupações implica que o cliente e o servidor são independentes um do outro, permitindo a evolução de cada um de forma independente. A escalabilidade envolve a capacidade de aumentar ou diminuir o número de servidores conforme necessário. A visibilidade implica que o cliente possa ver e entender a representação do recurso solicitado pelo servidor. Finalmente, a confiabilidade exige que o cliente possa confiar nas informações enviadas pelo servidor.
>
> Em suma, o REST é uma abordagem arquitetural para sistemas web que usa solicitações HTTP, recursos identificados por URLs e um conjunto de restrições para garantir a interoperabilidade entre diferentes sistemas. Ele é amplamente utilizado na Engenharia de Software para projetar APIs que sejam escaláveis, confiáveis e fáceis de evoluir.[^2]

<br>

---

### 1.1.1. Níveis de maturidade

#### 1.1.1.1. Richardson Maturity Model

- Nível 0: The Swamp if POX
- Nível 1: Resources
- Nível 2: Http Verbs
- Nível 3: HATEOAS
<br>[^3]

Transação sem padrão no lado do servidor<br>
Utilização de "resources"<br>
Verbos HTTP com representatividade<br>
HATEOAS ->  Hypermedia as Engine of Application State<br>

#### 1.1.1.2. "Verbos HTTP com representatividade"

| Verbo  | Utilização           |
| :----- | :------------------- |
| GET    | Recuperar informação |
| POST   | Inserir              |
| PUT    | Alterar              |
| DELETE | Remover              |

#### 1.1.1.3. Utilização de "resources"

| Verbo  | URI         | Operação |
| :----- | :---------- | -------- |
| GET    | /products/1 | Buscar   |
| POST   | /products   | Inserir  |
| PUT    | /products/1 | Alterar  |
| DELETE | /products/1 | Remover  |


### 1.1.2. Method e Content Negotiation

#### 1.1.2.1. Uma boa API REST

- URIs únicas
- Utiliza todos verbos para operações, incluindo caching
- Provê links relacionais para os recursos

#### 1.1.2.2. HAL, Collection+JSON e Siren

JSON não provê um padrão de hipermídia para linkagem<br>
HAL: Hipermídia Application Language<br>
Siren<br>

#### 1.1.2.3. REST: HAL
	
Media type = application/hal+json

"_links"<br>
  self -> trás o recurso atual q está acessando
  
"embbeded"<br>
  Recurso complementar

#### 1.1.2.4. REST: Http Method Negotiation
	
	Request:
		OPTIONS /api/product HTTP/1.1
		Host: fullcycle.com.br
    
	Response:
		HTTP/1.1 200 OK
		Allow: GET, POST

	Caso envie outro formato:
		HTTP/1.1 405 Not Allowed
		Allow: GET, POST

#### 1.1.2.5. REST: Content Negotiation - Accept Negotiation
	
	Request:
		GET/product
		Accept: application/json
	
	Response:
		HTTP/1.1 406 Not Acceptable

#### 1.1.2.6. REST: Content Negotiation - Content Type Negotiation
	
	Request tipo Content-Type Negotiation
		POST /product HTTP/1.1
		Accept: application/json
		Content-Type: application/json
		
	Caso não aceite:
		HTTP/1.1 415 Unsuported Media Type

<br>

---

## 1.2. gRPC

RPC: Remote Procedure Call

OBJETIVO: Facilitar o processo de comunicação entre sistemas de forma extremamente rápida. leve e independente de linguagem.[^1]

Um cliente chama uma função em um servidor<br>
`Cliente  -->  Server`

<br>

> :bulb: **OpenIA:** "Me explique resumidamente o que é gRPC"
> 
> gRPC é um framework de comunicação de software livre, criado pelo Google, que utiliza RPC (Remote Procedure Call) como mecanismo de comunicação entre diferentes sistemas. Ele é amplamente utilizado na Engenharia de Software para projetar APIs que sejam rápidas, eficientes e escaláveis. O gRPC é baseado em um protocolo chamado Protocol Buffers, que permite que os dados sejam serializados de forma eficiente e compacta.
>
> O gRPC utiliza o HTTP/2 como protocolo de transporte, o que permite a comunicação assíncrona e multiplexada, além de suportar a compressão de dados. Ele também oferece suporte a diferentes linguagens de programação, o que permite que os desenvolvedores usem suas linguagens de programação favoritas para escrever e consumir serviços gRPC.
> 
> Em resumo, o gRPC é um framework de comunicação de software livre que utiliza RPC e o protocolo HTTP/2 para criar APIs rápidas, eficientes e escaláveis. Ele é amplamente utilizado na Engenharia de Software para projetar serviços distribuídos que precisam de uma comunicação de baixa latência e alto desempenho.[^5]

### 1.2.1. Características - Em quais casos podemos utilizar ?

- Ideal para microserviços
- Mobile, Browsers e Backend
- Geração das bibliotecas de forma automática - (stubs - códigos prontos)
- Streaming bidirecional utilizando HTTP/2

### 1.2.2. LINKS

https://grpc.io

https://www.cncf.io/

https://developers.google.com/protocol-buffers

https://developers.google.com/protocol-buffers/docs/proto3

### 1.2.3. Linguagens

	- gRPC-GO
	- gRPC-Java
	- gRPC-C  -->  (C++ ,Phyton, Ruby, C#, PHP,Dart, Kotlin, etc)

### 1.2.4. Protocol Buffers

	- Linguagem neutra
	- Plataforma neutra
	- Extensivel p/ serializar estrutura de dados
	
		-> think XML, smaller, faster, and simpler
		
  "Protocol Buffers (também conhecido como protobuf) é um método de serialização de dados estruturados."[^4]

### 1.2.5. REST vs gRPC

- Browser			->		Servidor (NÃO RECOMENDADO)
- Sistemas		->		Sistema (Ok, RECOMENDADO)

| REST                  | gRPC                       |
| :-------------------- | :------------------------- |
| Texto / JSON          | Protocol Buffers           |
| Unidirecional         | Bidirecional e Assíncrono  |
| Alta latência         | Baixa Latência             |
| Sem contrato          | Contrato definido (.proto) |
| Sem streaming         | Suporte a streaming        |
| Design pré-definido   | Design livre               |
| Bibliotecas terceiros | Geração de código          |

<br>

---

## 1.3. GraphQL

GraphQL é uma linguagem de consulta de APIs<br>

	Mobile e Web
	-> Utilizando o mesmo Backend.
	-> Geralmente utilizam campos diferentes.

<br>

> :bulb: **OpenIA:** "Me explique resumidamente o que é GraphQL"
>
> GraphQL é uma linguagem de consulta para APIs (Interfaces de Programação de Aplicativos) criada pelo Facebook, que permite que o cliente especifique exatamente quais dados ele precisa e como deseja que esses dados sejam retornados pelo servidor. Ele é amplamente utilizado na Engenharia de Software para projetar APIs flexíveis e escaláveis.
> 
> O GraphQL permite que o cliente faça uma única solicitação para obter todos os dados necessários em vez de várias solicitações para diferentes endpoints. Ele também oferece suporte à tipagem, o que permite que o cliente especifique o tipo de dados que deseja receber. Isso aumenta a segurança e a confiabilidade da API.
> 
> O GraphQL é independente de linguagem e plataforma, o que significa que pode ser usado com qualquer linguagem de programação e em qualquer plataforma. Ele também oferece suporte a ferramentas de desenvolvimento, como o GraphiQL, que permite que os desenvolvedores testem suas consultas GraphQL e visualizem os resultados em tempo real.
> 
> Em resumo, o GraphQL é uma linguagem de consulta para APIs que permite que o cliente especifique exatamente quais dados ele precisa e como deseja que esses dados sejam retornados pelo servidor. Ele é amplamente utilizado na Engenharia de Software para projetar APIs flexíveis, escaláveis e seguras.[^6]

### 1.3.1. Vantagens

	- Único Endpoint
	- Única Requisição
	- O server apresenta recursos disponíveis
	- O client solicita a informação necessária
	- Permite alterações - mutations
	- Http
	- Json como response
	
<br>

---

## 1.4. Comunicaçao Síncrona

Acontece em tempo real
a) Request/Response

<br>

---

## 1.5. Comunicaçao Assíncrona

Não precisa ter a resposta na hora
a) Request/Reponse
b) Callback

Tecnologias conhecidas: RabbitMQ, Kafka, etc

## 1.6. Service Discovery

### 1.6.1. Consul

Consul - Entendendo-o-contexto
- Service Discovery
- Service Segmentation
- Load Balanecer na Borda (Layer 7)
- Key/Value Configuration
- Opensource / Enterprise
- Segurança - (TLS, Proxy)
	
https://www.hashicorp.com/products/consul

#### 1.6.1.1. Consul - Service registry
	
	Consul DNS Server
	- Registro de serviços registrados
	
	Consult Agend
	- Roda no cliente
	- Envia mensagens de saúde p/ o Server
	
	Gossip protocol

#### 1.6.1.2. Consul - Health check Ativo

	Server	<->		Server		<->		Server
		|               |                |
	Service	<->		Service		<->		Service

#### 1.6.1.3. Consul - Multicloud - ( multiregião )

	- Conceito de Datacenters
	
		( Cluster rodando em um lugar )
    
#### 1.6.1.4. Agent: Client & Server

	Agent é um processo (daemon) rodando em todos os nós do cluster
		Client mode
		Server mode

#### 1.6.1.5. Consul client

- Registra os serviços localmente
- Realiza o health cjeck
- Encaminha informações ao server

#### 1.6.1.6. Consul Server
	
- Mantém o estado do cluster
- Registra os serviços recebidos do Client
- Conceito de Membership ( quem é cliente e quem é server )
- Troca de informações entre datacenters

#### 1.6.1.7. Consul - Dev Mode

- Permite simular
- Não se utiliza em PRD
- Roda como Server
- Não escala
- Registra tudo em memória

---

[^1]: Curso FullCycle - Arquitetura de Software<br>
  Consultado em: 06/01/2023<br>
  Disponível em: https://plataforma.fullcycle.com.br

[^2]: OpenIA -> "Apresente resumidamente o que é REST"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 01/04/2023

[^3]: Richardson Maturity Model<br>
  Disponível em: https://martinfowler.com/articles/richardsonMaturityModel.html<br>
  Consultado em: 03/04/2023

[^4]: Protocol Buffers<br>
  Disponível em: https://pt.wikipedia.org/wiki/Protocol_Buffers<br>
  Consultado em: 03/04/2023

[^5]: OpenIA -> "Apresente resumidamente o que é gRPC"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 01/04/2023

[^6]: OpenIA -> "Apresente resumidamente o que é GraphQL"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 01/04/2023