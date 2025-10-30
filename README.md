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
  * Serviço de Grupos

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

### Desenho da Arquitetura

<img width="1580" height="887" alt="Diagrama em branco" src="https://github.com/user-attachments/assets/ad999af9-bf63-47b9-99a5-38d6cf8bbb42" />

### Fluxo do Projeto (Fluxograma)

<img width="1792" height="1040" alt="Fluxograma Fluid" src="https://github.com/user-attachments/assets/f5965ca9-c95c-48d8-a01e-0be460c18dbe" />

## Fundamentos Visuais, Tipografia e Wireframes

### Wireframes

<a name="wireframes"></a>

> Um wireframe web é uma ilustração semelhante ao
> layout de elementos fundamentais na interface.
Eles não apenas definem a estrutura e a arquitetura da informação de cada tela, mas também servem como a primeira validação de como os nossos componentes e padrões do Design System como botões, campos de input e layouts serão organizados para criar uma experiência de usuário coesa e intuitiva.

#### Landing Page

<img width="1920" height="1080" alt="LandingPage" src="https://github.com/user-attachments/assets/d9f75491-d4e7-4a7c-b203-36b7f615ab94" />


#### SignIn Page

<img width="1920" height="1080" alt="SignInPage" src="https://github.com/user-attachments/assets/418bb25c-6dff-4ebf-8297-60043e057e29" />


#### Perfil Page

<img width="1920" height="1080" alt="PerfilPage" src="https://github.com/user-attachments/assets/709ed9dc-52e8-4fa5-8268-a10a40b3dd31" />


#### Chat Page

<img width="1920" height="1081" alt="ChatPage" src="https://github.com/user-attachments/assets/6cd0d41f-f1a2-426b-b99b-67ec1cd25ee5" />


#### Contacto Page

<img width="1920" height="1081" alt="ContactsPage-1" src="https://github.com/user-attachments/assets/53d56aa3-d240-427a-bf3b-532c92065409" />


## Padrões de Comunicação

### RabbitMQ

### LibreTranslate

### Tesseract

## Persistência e Banco de Dados
Usamos o MongoDB, para armazenamento e persistência dos dados da aplicação como : 
  * Dados do Usário
    * Nome
    * Email
    * Senha
    * Telefone

## Escalabilidade
### Microsserviços independentes em Node.js
→ Permitem que cada função (mensagens, tradução, grupos) cresça de forma isolada, sem afetar o restante do sistema.

### Mensageria com Apache Kafka
→ Garante processamento assíncrono e distribuição equilibrada da carga em picos de uso.

### Banco PostgreSQL com replicação e particionamento
→ Mantém alta performance e integridade mesmo com grandes volumes de dados e acessos simultâneos.

### Infraestrutura com containers e CI/CD
→ Facilita o aumento automático de capacidade (auto-scaling) e atualizações contínuas sem interrupções.

### OpenTelemetry e monitoramento distribuído
→ Acompanha métricas e gargalos em tempo real, permitindo ajustes imediatos para manter estabilidade.

### Design modular e expansível
→ Suporte fácil a novos idiomas, recursos de tradução e acessibilidade, sem reescrever o sistema.
   
 ## Monitoramento e Observabilidade
 ### Logs
 * Console logging com console.log e console.error
 * Logs de operações críticas: WebSocket, mensagens, erros de autenticação
 * Rastreamento de fluxo: Entrada/saída de mensagens, estados de conexão
 * Logs de debug para traduções e comunicação em tempo real

 ### Saúde da Aplicação
 * Verificação via middleware de autenticação JWT
 * Validação de banco através de operações nos models User e Message
 * Monitoramento de conexões WebSocket ativas
 * Status de serviços RabbitMQ e MongoDB via uso operacional

 ### Métricas Existentes
 * Contagem de mensagens não lidas por conversa
 * Status de usuários online/offline
 * Contagem de conexões WebSocket ativas
 * Métricas de tradução (sucessos/falhas)

 ## Manutenibilidade
 ### Estrutura
 * Separação em camadas: Routes → Controllers → Services → Models
 * Módulos especializados: usuários, mensagens, conversas, tradução
 * Injeção de dependências via módulos CommonJS

### Organização
* Controllers: Orquestração de requests/responses HTTP
* Services: Lógica de negócio centralizada
* Models: Abstração de dados MongoDB
* Middleware: Autenticação e validação

### Testabilidade Estrutural
* Serviços independentes com responsabilidades únicas
* Funções puras em serviços de tradução e utilitários
* Baixo acoplamento entre domínios diferentes

### Manutenção Prática
* Error handling consistente em todos os controllers
* Validação centralizada em middleware dedicado
* Separação clara entre lógica WebSocket e REST API
* Reuso de serviços entre diferentes rotas e funcionalidades
