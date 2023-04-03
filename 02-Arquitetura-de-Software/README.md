# 1. Arquitetura de Software

- [1. Arquitetura de Software](#1-arquitetura-de-software)
  - [1.1. Fundamentos](#11-fundamentos)
    - [1.1.1. Tipos de Arquitetura](#111-tipos-de-arquitetura)
      - [1.1.1.1. Arquitetura corporativa](#1111-arquitetura-corporativa)
      - [1.1.1.2. Arquitetura de solução](#1112-arquitetura-de-solução)
      - [1.1.1.3. Arquitetura tecnológica](#1113-arquitetura-tecnológica)
      - [1.1.1.4. Arquitetura de software](#1114-arquitetura-de-software)
    - [1.1.2. Papel do Arquiteto de Software](#112-papel-do-arquiteto-de-software)
    - [1.1.3. Por que Arquiteto de Software](#113-por-que-arquiteto-de-software)
    - [1.1.4. Arquitetura vs Design](#114-arquitetura-vs-design)
    - [1.1.5. Sustentabilidade no dia zero](#115-sustentabilidade-no-dia-zero)
    - [1.1.6. Pilares da arquitetura de software](#116-pilares-da-arquitetura-de-software)
    - [1.1.7. Requisitos arquiteturais - (RAs)](#117-requisitos-arquiteturais---ras)
  - [1.2. Características arquiteturais](#12-características-arquiteturais)
    - [1.2.1. Características: Operacionais - (Ops)](#121-características-operacionais---ops)
    - [1.2.2. Características: Estrutura arquitetural](#122-características-estrutura-arquitetural)
    - [1.2.3. Características: Cross-Cutting](#123-características-cross-cutting)
  - [1.3. Performance](#13-performance)
    - [1.3.1. Como melhorar?](#131-como-melhorar)
    - [1.3.2. Razões da baixa performance](#132-razões-da-baixa-performance)
    - [1.3.3. Formas para aumentar a performance](#133-formas-para-aumentar-a-performance)
    - [1.3.4. Caching](#134-caching)
    - [1.3.5. Edge computing - ( Computação de borda )](#135-edge-computing----computação-de-borda-)
  - [1.4. Escalabilidade](#14-escalabilidade)
    - [1.4.1. Descentralização](#141-descentralização)
    - [1.4.2. Banco de Dados](#142-banco-de-dados)
    - [1.4.3. Proxy reverso](#143-proxy-reverso)
  - [1.5. Resiliência](#15-resiliência)
    - [1.5.1. Helth Check](#151-helth-check)
    - [1.5.2. Rate limiting](#152-rate-limiting)
    - [1.5.3. Circuit breaker](#153-circuit-breaker)
    - [1.5.4. API Gateway](#154-api-gateway)
    - [1.5.5. Service Mesh - Malha de serviços](#155-service-mesh---malha-de-serviços)
    - [1.5.6. Trabalhar de forma assíncrona](#156-trabalhar-de-forma-assíncrona)
    - [1.5.7. Retry - Garantia de Entrega](#157-retry---garantia-de-entrega)
    - [1.5.8. Garantias de entrega com Kafka - (Broker)](#158-garantias-de-entrega-com-kafka---broker)
    - [1.5.9. Situações complexas e decisões de alto nível](#159-situações-complexas-e-decisões-de-alto-nível)

<br>

---

## 1.1. Fundamentos

### 1.1.1. Tipos de Arquitetura

As organizações normalmente separam as funções de arquitetura em:
- Arquitetura corporativa
- Arquitetura de solução
- Arquitetura tecnológica
- Arquitetura de software

<br>

---

#### 1.1.1.1. Arquitetura corporativa

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

#### 1.1.1.2. Arquitetura de solução
	
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

#### 1.1.1.3. Arquitetura tecnológica

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

#### 1.1.1.4. Arquitetura de software

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

### 1.1.2. Papel do Arquiteto de Software

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

### 1.1.3. Por que Arquiteto de Software

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

### 1.1.4. Arquitetura vs Design

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

### 1.1.5. Sustentabilidade no dia zero

- Software é caro
- Software resolve uma "dor"
- Software precisa se pagar ao longo do tempo
- Acompanhar evolução
- Longevidade

"'Breakeven' significa o momento de equilíbrio da sua empresa,
ou seja, quando custos e despesas operacionais se igualam à receita."

<br>

---

### 1.1.6. Pilares da arquitetura de software

- Estrutura
- Componentização
- Relacionamento
- Governança - (padrões, regras, documentação, onboarding, etc)

<br>

---

### 1.1.7. Requisitos arquiteturais - (RAs)

- Performance
- - 500ms por requisição
- - 50 Transações por segundo
- Armazenamento de Dados
- Escalabilidade
- Segurança
- Legal
- Auditoria

<br>

---

## 1.2. Características arquiteturais

As características arquiteturais estão classificadas em categorias:
- Operacionais
- Estruturais
- Cross-Cutting

### 1.2.1. Características: Operacionais - (Ops)

> Pensar:
> - Como vai ficar mais fácil de operar?
> - Como a aplicação vai crescer?

- Disponibilidade - SLA
- Recuperação de desastres
- Performance
- - Quantas requisições por segundo?
- Recuperação (backup)
- Confiabilidade e segurança
- Robustez
- Escalabilidade - na forma orizontal
- - Twelve Factors

### 1.2.2. Características: Estrutura arquitetural

> Pensar:
> - Pontos de atenção para funcionar mais flexível

**Configurável**
- Trocar de ambiente

**Extensibilidade**
- Plugar aplicações de terceiros (vendors)
- Camadas anti-corrupção
- Novos módulos

**Fácil instalação**
- Docker / Elasticsearch / RabbitMQ 

**Reuso de componentes**
- Monolítico ( sem latência, tudo no mesmo sistema)
- Distribuído ( microservices, soluções iguais para mesmo problema )

**Internacionalização**
- Rótulos: não ficam no backend, problemas de layout desalinhados
- Gateway de pagamento: converção?

**Fácil manutenção**
- SOLID
- Camadas de sistemas
- Ports & Adapters
- Legível

**Portabilidade**
- Bancos de Dados
- Observabilidade

**Fácil suporte**
- Logs, centralização de logs, padronização de logs
- Métricas
- Debugging

### 1.2.3. Características: Cross-Cutting

**Acessibilidade**
- Qual o público a aplicação (frontend)
- Tá fácil de outrsas pessoas consigam utilizar?

**Retenção e recuperação de dados**
- Quanto tempo os dados serão mantidos?
- Exemplo: Tópicos de Kafka, vcto 7 dias

**Autenticação e Autorização**
- Arquitetura distribuída - keyclock
- API Gateway

**Legal**
- Armazenamento de dados

**Privacidade**
- LGPD

**Seguraça**

**Usabilidade**
- Documentação da API
- Contratos (Swagger)
- Readme

<br>

---

## 1.3. Performance

É o desempenho que o software possui para completar um workload.

*Unidades de Avaliação:*
- Latência ou "response time"
- Throughput - mostra quantas requisições o software consegue aguentar

`Performance <> Escalabilidade`

### 1.3.1. Como melhorar?

**a) Diminuir latência**
* Milisegundos
* Processamento, Rede e chamadas externas

**b) Aumentar Throughput**
* Qtd requisições

### 1.3.2. Razões da baixa performance
	
- Processamento ineficiente
- Recursos computacionais limitados
- Trabalhar com requisições NÃO bloqueantes
- Acesso serial a recursos ( uma atrás da outra; múltiplas threads )

### 1.3.3. Formas para aumentar a performance
	
- Escala da capacidade computacional - (CPU, Disco/IO, Memória, Rede)
- Lógica - ( algoritmos, queries, overhead de frameworks )
- Concorrência e paralelismo
- Banco de Dados
- Caching

- Escala Vertical vs Escala Horizontal -> (Load Balancer)

> **Concorrência vs Paralelismo**
>
> - Concorrência: Lidar com muitas coisas ao mesmo tempo.
> 10ms -> 10ms -> 10ms -> 10ms -> 10ms ->	**TOTAL = 50ms**
> 
> - Paralelismo: Fazer muitas coisas ao mesmo tempo.<br>
> 10ms -><br>
> 10ms -><br>
> 10ms ->					**TOTAL = 10 ms**<br>
> 10ms -><br>
> 10ms -><br>

### 1.3.4. Caching
	
- Cache na borda / Edge computing
- Cache de dados estáticos
- Cache de páginas Web (Html).
- Cache de funções internas
- - Algoritmos
- - Acesso banco de dados
- Cache de objetos - Criação de instâncias a todo momento

> ------------------------------
> #### Tipos de Cache
> 
> **Exclusivo - ( na aplicação )**
> - Baixa latência
> - Duplicado entre nós
> - Problemas relacionados a sessões
>
> **Compartilhado - ( Servidor de cache )**
> - Maior latência
> - Não há duplicação
> - Sessões compartilhadas
> - Banco de dados externos
> - - MySql
> - - Redis - cache extremamente rápido ( maior mercado )
>
> ------------------------------

### 1.3.5. Edge computing - ( Computação de borda )
	
O processamento acontece no local físico (ou próximo) do usuário
- Cache próximo ao usuário
- Evita chegar até o Cloud Provider / Infra
- Arquivos estáticos
- CDN - Content Delivery Network - (rede de distribuição de conteúdo)
- Cloudflare workers
- Vercel - ( NextJS )
- Akamai

https://www.cloudflare.com/pt-br/
https://www.akamai.com/solutions/content-delivery-network
https://vercel.com/

<br>

---

## 1.4. Escalabilidade

É a capacidade de sistemas suportarem o aumento ou redução dos workloads incrementando ou reduuzindo o custo.
* Maior Poder Computacional
* Escala Vertical: Aumentar recurso computacional (CPU)
* Escala Horizontal: Aumentar Quantidade de Máquinas 
* Aumentar Throughput - mostra quantas requisições o software consegue aguentar
* Proxy Reverso / Load balancer

https://arquiteturadesoftware.online/

### 1.4.1. Descentralização
	
- Disco efêmero - ( s3 bucket aws - fotos, vídeos, documentos )
- Servidor aplicação vs Servidor de assets ( imagens, css, arquivo txt... )
- Cache centralizado
- Sessões centralizadas
- Upload / Gravação de arquivos

### 1.4.2. Banco de Dados
	
- Aumento de recursos computacionais
- Distribuir responsabilidade - ( escrita vs leitura )
- Shards de forma horizontal
- Serverless - ( sem servidor: Ex: Lambda functions )
Serverless é um modelo de desenvolvimento nativo em nuvem para
criação e execução de aplicações sem o gerenciamento de servidores

- Otimização de queries e índices
* Índices
* APM - Application Performance Monitoring
* Explain queries
* CQRS - ( Command Query Responsability Segregation )

### 1.4.3. Proxy reverso
	
- Proxy => Procurador, ou seja, fala em seu nome ( filtro na saída ).
- Proxy reverso => Me encaminha para o servidor ( filtro na entrada ).

MERCADO
* Nginx
* HAProxy ( HA= High Availability )
* Traefik

<br>

---

## 1.5. Resiliência

- Mecanismos de autopreservação

- Não ser egoísta - (com acesso aos serviços externos )
"Não adianta chutar cachorro  morto"

- Um sistema lento é muitas vezes pior que um sistema fora do ar
"Efeito dominó"

<br>

---

### 1.5.1. Helth Check
	
- Sem sinais vitais, não é possível verificar a saúde do sistemas

- Self-healing: Possui a chance de se recuperar, caso o tráfego para temporariamente

- Helth Check de Qualidade

<br>

---

### 1.5.2. Rate limiting
	
Proteger, baseado no que a aplicação foi projetado para suportar
- Teste de stress -> determinar os limites.
- Ex.: Máx 100 requisições p/ segundos.

Preferência programado por 'tipo de cliente' -- ( Origem? )
- Sistemas com maior ou menor criticidade

<br>

---

### 1.5.3. Circuit breaker
	
Protege o sistema fazendo com que as requisições sejam negadas:
- Circuito fechado - Requisições chegam normal
- Circuito aberto - Requisições NÃO chegam normal
- - 500 - Internal Server Error
- Meio aberto - Permite qtd limitada, p/ verificar se aplicação voltou a ter saúde

<br>

---

### 1.5.4. API Gateway
	
Garante que requisições "inapropriadas" chegem até o sistema.
	
https://docs.konghq.com/gateway/latest/
  Helth Check
  Rate limiting

<br>

---

### 1.5.5. Service Mesh - Malha de serviços
	
Controla o tráfego da rede - usando 'mini' proxy
  
Uma service mesh, assim como o projeto open source Istio, é uma maneira de controlar como diferentes componentes de uma aplicação compartilham dados entre si.
  
A service mesh is a dedicated infrastructure layer for facilitating service-to-service communications between services or microservices, using a proxy.
  
- Evita implementações de proteção pelo próprio sistema
- mTLS - ( Man in the midle )
- Circuit breaker, retry, timeout, fault injection, etc

<br>

---

### 1.5.6. Trabalhar de forma assíncrona
	
- Evita perda de dados
- Entender com profundidade message broker / sistema de stream

*** Kafka ***

<br>

---

### 1.5.7. Retry - Garantia de Entrega
	
Exponential backoff
- Retry exponencial
- EX: 1s, 2s, 4s, 8s, ...

Exponential backoff + Jitter -> Pequena alteração da chamada
- Retry exponencial c/ ruído
- EX: 1.2s, 2.5s, 4.6s, 8.7s, ...

<br>

---

### 1.5.8. Garantias de entrega com Kafka - (Broker)
	
Broker -> sistema q armazena mensagem para outro pegar depois

[ Ack 0 ]<br>
Fire and forget - ( envia msg e não precisa saber se foi )<br>

[ Ack 1 ]<br>
Retorna 'Ok, recebido'<br>

[ Ack -1 ALL ]<br>
Broker A, B e C - 'Ok, todos  recebidos'<br>

---

### 1.5.9. Situações complexas e decisões de alto nível
	
- O que acontece se o 'Message broker' cair ?
- O que acontece se o 'Rabbit MQ' cair ?
- Haverá perda de mensagem?
- O sistema ficará fora?

SPOF = Single point of failure - (Ponto único de falha)
Zonas de Disponibilidade AWS
Multicloud - resiliência e disponibilidade

CTO decide, de acordo com nível de risco de negócio.
"Quanto mais resiliência, mais caro é."
