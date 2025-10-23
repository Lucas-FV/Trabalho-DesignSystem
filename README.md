# Trabalho-DesignSystem

## Apresentação

A comunicação global sempre enfrentou uma barreira fundamental: o idioma. Segundo relatório da EF English Proficiency Index (2024), apenas cerca de 17% da população mundial fala inglês com fluência, e este ainda é considerado o idioma mais utilizado em interações internacionais. Além disso, estima-se que existam mais de 7.000 línguas vivas no mundo, das quais aproximadamente 23 concentram a comunicação de mais da metade da população global. Esse cenário torna evidente a dificuldade de estabelecer interações naturais entre pessoas de diferentes culturas, limitando a colaboração, a troca de conhecimento e as relações pessoais.

Nesse contexto, surge a proposta de um aplicativo de rede social que possibilita conversas bilíngues ou multilíngues em tempo real, eliminando barreiras linguísticas e proporcionando um ambiente inclusivo e universal para interação.

## Problema

O problema identificado é a barreira linguística existente nas interações digitais. Mesmo em um mundo globalizado, a comunicação entre pessoas de diferentes nacionalidades ainda depende de intermediários, tradutores externos ou de um idioma comum (como o inglês), que nem sempre garante precisão ou naturalidade na conversa.

Assim, existe uma necessidade clara de uma solução que permita tradução instantânea, contínua e transparente, garantindo que cada participante da conversa possa se expressar no seu idioma nativo sem prejuízo da compreensão.

## Produto

Nosso produto consiste em uma aplicação WEB e Mobile, de um chat de conversas entre pessoas onde todas as mensagens serão traduzidas simultanêamente para o respectivo idioma escolhido do usuário. Além disso teremos funções de tradução de fotos onde a pessoa pode mandar uma foto para algum contato e este contato reberá a tradução de algum texto presente na imagem.

## Arquitetura 


### Estilo Arquitetural
Durante nosso projeto usamos o estilo de micro-serviços para a implementação. Onde tivemos serviços de :
  * Serviço de Tradução
  * Serviço de Mensagens
  * Serviço de Notificação
  * Serviço de Contatos
  * Serviço de Imagens

### Padrão Arquitetural
Para a implementação do nosso projeto usamos o padrão MVC, onde temos:
  * View
    * Temos as telas tanto de WEB quanto Mobile
    * Temos os serviços de autenticação
  * Model
    * Temos as estruturas de atributos das tabelas de, Usuario, Contatos, Mensagens...
  * Controller
    *  Temos as lógicas de négocio
    *  Integrações com as API's
    *  Integração com os serviços de mensageria do RabbitMQ
    
