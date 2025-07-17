# Grafana Stack

Para iniciar a stack, utilize:

```bash
docker compose up
```

> [!IMPORTANT]
> No Linux, talvez seja necessário alterar as permissões das pastas geradas pelas binds do Docker

## Grafana

Ferramenta utilizada para ver os dados em gráficos, organizados em dashboards. Você pode utilizar um dashboard pronto, impotando os arquivos correspondentes da pasta `/dashboards.

### Dashboards Pré Feitos

- Spring Boot Application: `/dashboards/spring-application-dashboard.json`

### Diretórios

- `/grafana-plugins` - Contém os plugins instalados no Grafana
- `/grafana` - Contém os dados do Grafana

### Endereço de Acesso

- [[http://localhost:3000]]

## Alloy

O Grafana Alloy reúne os pontos fortes dos principais coletores em um só lugar. Seja observando aplicações, infraestrutura ou ambos, o Grafana Alloy pode coletar, processar e exportar sinais de telemetria para escalar e preparar sua abordagem de observabilidade para o futuro.

- Arquivo de configuração: `/shared/config.alloy`

### Portas

|Porta Externa|Porta Interna|Descrição      |
|-------------|-------------|---------------|
| 4317        | 4317        | Otlp grpc     |
| 4318        | 4318        | Otlp http     |

## Tempo

Backend de tracing que possibilita a busca por traces, gerar traces de spans e linkar dados de traces com métricas e logs.

- Arquivo de configuração: `/shared/tempo.yaml`

### Portas

|Porta Externa|Porta Interna|Descrição      |
|-------------|-------------|---------------|
| 14268       | 14268       | Jaeger ingest |
| 3200        | 3200        | Tempo         |
| 9095        | 9095        | Tempo grpc    |
| 4327        | 4317        | Otlp grpc     |
| 4328        | 4318        | Otlp http     |
| 9411        | 9411        | Zipkin        |

## Prometheus

Toolkit de monitoramento de sistemas que coleta e armazena suas métricas como time series data.

- Arquivo de configuração: `/shared/prometheus.yaml`
- Porta: 9090

## Loki

Conjunto de componentes que podem ser compostos em uma stack de logging completamente funcional.

- Arquivo de configuração: `/shared/loki-config.yaml`
- Porta: 3100

## Pyroscope

Software de agregação de profiling contínuo. é um sinal de observabilidade que permite que você entenda o uso de recursos da sua carga de trabalho até o número da linha do código-fonte

Baixe o plugin do Pyroscope para o Grafana, e cloque na pasta `grafana-plugins/`.

- [Download Plugin](https://grafana.com/api/plugins/grafana-pyroscope-app/versions/1.5.0/download)

> [!IMPORTANT]
> Sem o plugin do Pyroscope, o Grafana não irá funcionar.

### Diretórios

- Arquivo de configuração: `/shared/pyroscope.yaml`
- Dados do Pyroscope: `/pyroscope-data`