# Portfolio_Analise_dados_Infra_TI
Ambientes críticos de TI exigem alta disponibilidade e performance. Muitas vezes os incidentes de indisponibilidade ou lentidão estão relacionados a gargalos de recursos (ex.: CPU sobrecarregada, memória insuficiente, saturação de rede). Antecipar esses problemas é vital para manter o negócio em operação sem interrupções.

# Pergunta principal
Quais padrões de consumo de recursos (CPU, memória e rede) podem antecipar gargalos em nossa infraestrutura?

# Hipótese inicial
CPU: cargas elevadas em horários de pico ou picos de processos em batch podem antecipar incidentes.
Memória: crescimento constante no consumo sem liberação pode indicar risco de “memory leak”.
Rede: saturação em horários críticos pode estar ligada a aplicações específicas ou backups.

#Dados necessários
Métricas de performance extraídas de ferramentas de monitoramento (Zabbix, Grafana, Prometheus, CloudWatch etc.):
Uso de CPU (% por servidor/cluster).
Consumo de memória (MB/GB alocados x disponíveis).
Tráfego de rede (Mbps, pacotes enviados/recebidos).
Logs de incidentes (para correlacionar com os picos).
Horários e calendário (ex.: fins de mês, horários de fechamento de sistema, rotinas batch).

# Metodologia de análise
Coleta
Extrair séries temporais de CPU, memória e rede por servidor (últimos 12 meses).
Tratamento
Limpeza dos dados (remover outliers não representativos, normalizar valores).
Análise exploratória
Gráficos de linha para visualizar consumo ao longo do tempo.
Histogramas para identificar distribuição de uso (picos x média).
Heatmaps para visualizar padrões por horário/dia da semana.
Correlação com incidentes
Comparar picos de utilização com datas de falhas reportadas no ITSM.
Modelagem preditiva (opcional)
Aplicar análise de tendências (ARIMA ou regressão) para prever quando a infraestrutura atingirá limites críticos.

#Métricas de Sucesso
Identificar padrões horários e semanais de consumo.
Criar alertas proativos quando o consumo se aproxima de limites críticos.
Reduzir em pelo menos 20% o número de incidentes não planejados por gargalos de recursos.

#resultados esperados
Mapa claro de horários críticos (ex.: segunda-feira às 9h, fechamento de mês).
Identificação de servidores mais sensíveis a sobrecarga.
Insights para decisões de capacity planning (upgrade de hardware, balanceamento de carga, escalabilidade em cloud).
Implantação de KPIs de monitoramento preditivo: CPU acima de 85%, memória acima de 90%, rede acima de 80% → disparar alerta antes do incidente.

#Visualizações recomendadas
Linha do tempo (time series): evolução do consumo de CPU, memória e rede.
Heatmap: consumo por hora/dia da semana.
Dashboard interativo: servidores críticos com status em tempo real.


