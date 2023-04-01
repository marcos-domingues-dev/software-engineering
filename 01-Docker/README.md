# Docker

## O que é Docker?

O Docker é uma plataforma de software open source que possibilita o empacotamento de uma aplicação dentro de um container (1).
  
Com o Docker é possível criar, implantar e executar aplicativos em contêiners. Esses contêiners fornecem um ambiente isolado para os aplicativos e suas dependências, tornando-os portáveis e fáceis de implantar em diferentes plataformas e ambientes (2).

## Recursos oferecidos pelo Docker

1. Isolamento de aplicativos em contêiners: cada contêiner tem seu próprio ambiente isolado para executar o aplicativo e suas dependências, o que ajuda a garantir a compatibilidade e a segurança.

2. Portabilidade de aplicativos: os contêiners são portáteis e podem ser executados em qualquer sistema operacional ou infraestrutura de nuvem compatével com Docker.

3. Gerenciamento de recursos: o Docker ajuda a gerenciar os recursos do sistema, incluindo CPU, memória e armazenamento, para garantir que os aplicativos executem de forma eficiente.

4. Escalonamento horizontal: o Docker permite dimensionar facilmente aplicativos com vários contêiners em diferentes hosts para lidar com cargas de trabalho crescentes.

5. Implantação de aplicativos: os contêiners podem ser facilmente implantados em diferentes ambientes, incluindo nuvem pública, nuvem privada, data center local ou laptop.

6. Integração contínua e implantação contínua (CI/CD): o Docker pode ser integrado a ferramentas de CI/CD para automatizar o processo de construção, teste e implantação de aplicativos e contêiners.

Esses recursos tornam o Docker uma das plataformas de contêiners mais populares e amplamente usadas no mundo do desenvolvimento de software e da computação em nuvem (2).

## Como começar com o Docker?

### o que é um contêiner?

Simplificando, um contêiner é um processo empacotado em sua máquina que é isolado de todos os outros processos na máquina host. Este isolamento aproveita o namespaces do kernel e cgroups, funcionalidades que estão no Linux há muito tempo. O Docker trabalhou para tornar esses recursos acessíveis e fáceis de usar (3).

Para resumir um contêiner:
- É uma instência executável de uma imagem. Você pode criar, iniciar, parar, mover ou deletar um contêiner usando o Docker API ou CLI.
- Pode ser executado em máquinas locais, máquinas virtuais ou implantado na Cloud
- É portável (pode ser executado em qualquer OS)
- É isolado de outros contêiners e roda seu próprio software, binários e configurações

> Namespace (Espaço de nomes): Um espaço de nomes é um delimitador abstrato que fornece um contexto para os itens que ele armazena, o que permite uma desambiguação para itens que possuem o mesmo nome mas que residem em espaços de nomes diferentes (4).

## REFERÊNCIAS

(1) Curso FullCycle - Docker
Consultado em: 18/09/2022
Disponível em: 

(2) OpenIA -> "Apresente um resumo breve dos recursos oferecidos pelo Docker"
Disponível em: https://chat.openai.com/chat
Consultado em: 01/04/2023

(3) Docker overview
Disponível em: https://docs.docker.com/get-started/
Consultado em: 01/04/2023

(4) Namespace
Disponível em: https://pt.wikipedia.org/wiki/Espa%C3%A7o_de_nomes
Consultado em: 01/04/2023
