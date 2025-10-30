🚀 Projeto de Monitoramento: PedidoService (Spring Boot + Prometheus/Grafana)
Este repositório contém a implementação completa de um sistema de monitoramento para a API PedidoService, conforme o estudo de caso, utilizando as seguintes tecnologias:

Aplicação: Spring Boot 3+

Geração de Métricas: Micrometer e Spring Boot Actuator

Coleta e Alertas: Prometheus

Visualização: Grafana

Orquestração: Docker Compose

O monitoramento abrange Métricas Técnicas (Uso de CPU, Threads, Tempo de Resposta) e Métricas de Negócio (Quantidade e Valor dos Pedidos).

📋 Pré-requisitos
Para executar o monitoramento completo (Visualização no Grafana), os seguintes requisitos são obrigatórios:

Java Development Kit (JDK) 17+

Docker Desktop (Instalado e em execução)

🛠️ Instruções de Execução (Guia para o Teste)
Siga estes 3 passos para iniciar a aplicação, o monitoramento e visualizar o dashboard.

Passo 1: Iniciar a Aplicação Spring Boot
Abra o Terminal na pasta raiz do projeto.

Bash

# Inicia a API REST na porta 8080.
./mvnw spring-boot:run
Detalhe: Deixe este terminal rodando. A aplicação está expondo as métricas em /actuator/prometheus.

Passo 2: Iniciar os Serviços de Monitoramento
Abra um SEGUNDO TERMINAL e navegue até a pasta raiz do projeto.

Bash

# Inicia o Prometheus (porta 9090) e o Grafana (porta 3000)
docker-compose up
Detalhe: O Prometheus usará o arquivo prometheus.yml para configurar a coleta e coletará os dados da aplicação no endereço host.docker.internal:8080.

Passo 3: Visualizar o Dashboard (Grafana)
Acesse o navegador: http://localhost:3000

Faça Login: admin / admin

Configuração e Visualização:

A Fonte de Dados (Prometheus) deve ser configurada:

No menu, vá em Configuration > Data Sources.

Adicione o Prometheus, usando o URL: http://prometheus:9090.

Para ver os gráficos, importe o dashboard:

No menu, vá em Dashboards > Import.

Use o ID pronto: 4701 (ou 6756).

O painel exibirá as métricas coletadas da sua aplicação PedidoService em tempo real.
