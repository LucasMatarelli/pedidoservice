# 🚀 Projeto de Monitoramento: PedidoService (Spring Boot + Prometheus/Grafana)

[cite_start]Este repositório contém a implementação completa de um sistema de monitoramento para a API `PedidoService`[cite: 10], conforme o estudo de caso, utilizando as seguintes tecnologias:
* **Aplicação:** Spring Boot 3+
* [cite_start]**Geração de Métricas:** Micrometer e Spring Boot Actuator [cite: 38, 42, 106, 107]
* [cite_start]**Coleta e Alertas:** Prometheus [cite: 6, 66, 109]
* [cite_start]**Visualização:** Grafana [cite: 5, 72, 110]
* [cite_start]**Orquestração:** Docker Compose [cite: 8, 63, 112]

[cite_start]O monitoramento abrange Métricas Técnicas (como Uso de CPU e Tempo de Resposta) [cite: 17, 18] [cite_start]e Métricas de Negócio (como Quantidade e Valor dos Pedidos)[cite: 23, 24].

## 📋 Pré-requisitos
Para executar o monitoramento completo (Visualização no Grafana), os seguintes requisitos são obrigatórios:
1.  **Java Development Kit (JDK) 17+**
2.  **Docker Desktop** (Instalado e em execução)

## 🛠️ Instruções de Execução (Guia para o Teste)

Siga estes 3 passos para iniciar a aplicação, o monitoramento e visualizar o dashboard.

### Passo 1: Iniciar a Aplicação Spring Boot
Abra o Terminal na pasta raiz do projeto.
```bash
# Inicia a API REST na porta 8080.
./mvnw spring-boot:run
(Deixe este terminal rodando. A aplicação está expondo as métricas em /actuator/prometheus )

Passo 2: Iniciar os Serviços de Monitoramento
Abra um SEGUNDO TERMINAL e navegue até a pasta raiz do projeto.
# Inicia o Prometheus (porta 9090) e o Grafana (porta 3000)
docker-compose up
(O Prometheus usará o arquivo prometheus.yml para configurar a coleta a cada 5 segundos e coletará os dados da aplicação no endereço host.docker.internal:8080 )

Passo 3: Visualizar o Dashboard (Grafana)
Acesse o navegador: http://localhost:3000 
Faça Login: admin / admin 
Visualização: A Fonte de Dados (Prometheus) deve ser configurada:
No menu, vá em Configuration > Data Sources.
Adicione o Prometheus, usando o URL: http://prometheus:9090.
Para ver os gráficos, importe um dashboard:
No menu, vá em Dashboards > Import.
Use o ID pronto: 4701 (ou 6756).
O painel exibirá as métricas coletadas da sua aplicação PedidoService em tempo real.
