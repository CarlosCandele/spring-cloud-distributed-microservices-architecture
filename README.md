# 🚀 Microservices Architecture with Spring Cloud

# Microsserviços - Projeto de Exemplo

Este repositório contém um conjunto de microserviços Java (Spring Boot) organizados como projetos separados:

- `service-main`
- `service-tasks`
- `service.notification`
- `config-server`
- `docker-compose.yml` para orquestração local

Este README fornece instruções rápidas para rodar, construir e depurar a aplicação localmente e com Docker.

## Visão geral

Cada pasta no repositório representa um serviço independente com seu próprio `Dockerfile` e configuração Maven. O `config-server` expõe propriedades de configuração (arquivos `.properties` já incluídos em `config-server/`). O `docker-compose.yml` facilita executar todos os serviços juntos para desenvolvimento ou demonstração.

## Estrutura do repositório

- `service-main/` — serviço principal (API / frontend relacionado)
- `service-tasks/` — serviço de tarefas
- `service.notification/` — serviço de notificações
- `config-server/` — arquivos de configuração para cada serviço
- `docker-compose.yml` — orquestração local

## Pré-requisitos

- Java 11+ (ou a versão requerida pelo projeto)
- Maven (ou use o wrapper `./mvnw` incluído)
- Docker & Docker Compose (opcional, para containerização)

## Executando localmente (com Maven)

1. Navegue até o serviço desejado, por exemplo `service-main`:

```bash
cd service-main
./mvnw clean package
```

2. Execute o JAR gerado (substitua pela versão correta caso mude):

```bash
java -jar target/service-main-0.0.1-SNAPSHOT.jar
```

Repita para `service-tasks` e `service.notification` se quiser executar os serviços individualmente.

## Executando com Docker Compose

Para subir todos os serviços juntos (recomendado para desenvolvimento integrado):

```bash
docker-compose up --build
# ou em background
docker-compose up -d --build
```

O `docker-compose.yml` irá construir as imagens a partir dos `Dockerfile` em cada serviço e iniciar os containers.

## Build das imagens individualmente

Exemplo para `service-main`:

```bash
cd service-main
docker build -t service-main:local .
```

Repita para os outros serviços conforme necessário.

## Configuração

O repositório inclui `config-server/service-notification.properties` e `config-server/service-tasks.properties`. O `config-server` (quando usado) serve essas propriedades para os serviços via Spring Cloud Config. Ajuste os arquivos de propriedades conforme o ambiente.

## Logs e troubleshooting

- Verifique os logs no console do Maven (`./mvnw spring-boot:run`) ou nos logs do container Docker (`docker-compose logs -f`).
- Se um serviço não iniciar, confira:
	- Portas em uso (conflitos de porta)
	- Configurações no `config-server`
	- Variáveis de ambiente necessárias nos `Dockerfile`/`docker-compose.yml`

## Desenvolvimento e contribuição

- Faça fork do repositório e abra PRs com mudanças claras.
- Mantenha testes (quando aplicável) e atualize a documentação se alterar endpoints ou contratos.

## Comandos úteis

- Build e testar um serviço:

```bash
cd service-main
./mvnw clean package
```

- Executar todos com Docker Compose:

```bash
docker-compose up --build
```

- Ver logs de um serviço (ex.: `service-main`):

```bash
docker-compose logs -f service-main
```

## Observações finais

Este README é um guia inicial. Se você quiser, posso:

- Adicionar exemplos de endpoints e contratos de API
- Incluir instruções de testes automatizados
- Gerar arquivos de exemplo para variáveis de ambiente

Informe o que prefere que eu adicione a seguir.

---
Arquivo atualizado automaticamente.

Projeto desenvolvido com foco em arquitetura de microserviços utilizando o ecossistema Spring Cloud, aplicando boas práticas de sistemas distribuídos e containerização com Docker.

---

## 📌 Sobre o Projeto

Esta aplicação foi construída com o objetivo de aplicar na prática os principais conceitos de arquitetura de microserviços, desde a base teórica até a implementação de um sistema totalmente distribuído e dockerizado.

A solução contempla:

- Arquitetura 100% distribuída
- Configuração centralizada
- Service Discovery
- Comunicação entre serviços
- Containerização completa
- Orquestração com Docker Compose

---

## 🏗️ Arquitetura Aplicada

A aplicação é composta pelos seguintes componentes:

- 🔧 **Config Server** – Centralização de configurações
- 🧭 **Service Discovery (Eureka Server)** – Registro e descoberta de serviços
- 🌐 **API Gateway** – Ponto único de entrada
- 🔗 **Microservices independentes**
- 🐳 **Docker & Docker Compose** – Orquestração dos containers

Fluxo arquitetural:

Client → API Gateway → Microservices → Config Server / Eureka

---

## 🧠 Conceitos Aplicados

Durante o desenvolvimento foram aplicados conceitos importantes como:

- Diferença entre Monólitos e Microserviços
- Vantagens e Desvantagens da Arquitetura Distribuída
- Princípios de desacoplamento
- Externalização de configurações
- Comunicação síncrona entre serviços
- Healthcheck e gerenciamento de containers
- Orquestração com Docker Compose

---

## 🛠️ Tecnologias Utilizadas

- Java 17+
- Spring Boot
- Spring Cloud
- Spring Cloud Config
- Eureka Server
- OpenFeign
- RestTemplate
- Docker
- Docker Compose
- Maven

---

## 🔄 Comunicação entre Microserviços

A comunicação foi implementada utilizando:

- **OpenFeign** (client declarativo)
- **RestTemplate** (abordagem tradicional HTTP)

Permitindo comparação entre estratégias de comunicação síncrona.

---

## 🐳 Containerização

Todos os serviços foram:

- Dockerizados individualmente
- Configurados com Healthcheck
- Orquestrados com Docker Compose
- Executados em rede compartilhada

Para subir o ambiente completo:

```bash
docker-compose up --build

---
```
---

## 👨‍💻 Autor

Projeto desenvolvido por Carlos Jorge.


