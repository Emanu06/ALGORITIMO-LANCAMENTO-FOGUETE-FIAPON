# Foguete PY — Verificação de Pré-Decolagem

## Explicação do projeto

Este projeto simula um checklist de pré-decolagem de foguete usando Python em notebook (`script.ipynb`).

O sistema:
- coleta dados operacionais (temperatura, integridade, energia, pressão e status de módulos);
- valida os dados com base em limites de segurança;
- executa uma análise energética para estimar autonomia pós-decolagem;
- realiza uma análise de risco (IA) com classificações, anomalias e sugestões;
- gera um relatório final no output e uma planilha `relatorio_do_foguete.xlsx`.

## Prints da execução

### Print 1 — Cenário aprovado

```text
============================================================
 RELATORIO DE VERIFICAÇÃO
  2026-03-30T10:20:01.655311
============================================================

 DADOS COLETADOS
  Temperatura Interna  : 30.0 °C
  Temperatura Externa  : 50.0 °C
  Integridade Estrut.  : OK (1)
  Nível de Energia     : 100.0 %
  Pressão Tanque Ox.   : 270.0 kPa
  Pressão Tanque Comb. : 200.0 kPa
  Módulos Críticos:
   Propulsao : OK (1)
   Navegacao : OK (1)
   Comunicacao : OK (1)
   Controle Termico : OK (1)
   Separacao Estagios : OK (1)

VERIFICAÇÕES DE SEGURANÇA
  Temp Interna : OK
  Temp Externa : OK
  Integridade Estrutural : OK
  Nivel Energia : OK
  Pressao Tanque Ox : OK
  Pressao Tanque Comb : OK
  Modulos Criticos : OK

 ANÁLISE ENERGÉTICA
  Capacidade Total     : 500.0 kWh
  Carga Atual          : 500.0 kWh
  Consumo Decolagem    : 120.0 kWh
  Perdas Estimadas     : 9.6 kWh
  Consumo Real Total   : 129.6 kWh
  Autonomia Pós-Dec.   : 370.4 kWh  Suficiente

 ANÁLISE DE IA
  Classificações:
    • Temperatura interna: NOMINAL
    • Energia: EXCELENTE
    • Todos os módulos críticos: OPERACIONAIS
  Anomalias:
    ⚠ Pressão em tanques próxima ao limite inferior — risco de falha de propulsão
  Sugestões de Risco:
    → Pressurizar tanques ao nível nominal (270–300 kPa)
    → Todos os parâmetros nominais — missão pode prosseguir conforme planejado

────────────────────────────────────────────────────────────
  DECISÃO FINAL: PRONTO PARA DECOLAR
────────────────────────────────────────────────────────────

```

### Print 2 — Cenário abortado

```text
============================================================
 RELATORIO DE VERIFICAÇÃO
  2026-03-30T16:54:28.032161
============================================================

 DADOS COLETADOS
  Temperatura Interna  : -13.0 °C
  Temperatura Externa  : 90.0 °C
  Integridade Estrut.  : FALHA (0)
  Nível de Energia     : 15.0 %
  Pressão Tanque Ox.   : 52.0 kPa
  Pressão Tanque Comb. : 12.0 kPa
  Módulos Críticos:
   Propulsao : FALHA (0)
   Navegacao : FALHA (0)
   Comunicacao : FALHA (0)
   Controle Termico : FALHA (0)
   Separacao Estagios : FALHA (0)

VERIFICAÇÕES DE SEGURANÇA
  Temp Interna : FALHA
  Temp Externa : FALHA
  Integridade Estrutural : FALHA
  Nivel Energia : FALHA
  Pressao Tanque Ox : FALHA
  Pressao Tanque Comb : FALHA
  Modulos Criticos : FALHA

 ALERTAS
  [ALERTA] Temperatura interna fora do limite: -13.0°C (esperado: -10 a 40°C)
  [ALERTA] Temperatura externa fora do limite: 90.0°C (esperado: -80 a 60°C)
  [CRÍTICO] Integridade estrutural comprometida! (valor=0)
  [ALERTA] Nível de energia insuficiente: 15.0% (mínimo: 85%)
  [CRÍTICO] Pressão tanque oxidante fora do limite: 52.0 kPa
  [CRÍTICO] Pressão tanque combustível fora do limite: 12.0 kPa
  [CRÍTICO] Módulos com falha: propulsao, navegacao, comunicacao, controle_termico, separacao_estagios

 ANÁLISE ENERGÉTICA
  Capacidade Total     : 500.0 kWh
  Carga Atual          : 75.0 kWh
  Consumo Decolagem    : 120.0 kWh
  Perdas Estimadas     : 9.6 kWh
  Consumo Real Total   : 129.6 kWh
  Autonomia Pós-Dec.   : -54.6 kWh  Insuficiente

 ANÁLISE DE IA
  Classificações:
    • Temperatura interna: FRIA (risco de condensação em circuitos)
    • Energia: INSUFICIENTE — risco operacional
  Anomalias:
    ⚠ Temperatura interna abaixo de zero — risco de falha em sensores
    ⚠ Nível de energia abaixo do mínimo recomendado
    ⚠ Pressão em tanques próxima ao limite inferior — risco de falha de propulsão
    ⚠ Módulo(s) crítico(s) com falha detectada: propulsao, navegacao, comunicacao, controle_termico, separacao_estagios
    ⚠ Integridade estrutural comprometida — possível dano físico à estrutura
  Sugestões de Risco:
    → Ativar sistema de aquecimento interno antes da decolagem
    → Recarregar bancos de energia antes da tentativa de decolagem
    → Pressurizar tanques ao nível nominal (270–300 kPa)
    → Executar diagnóstico completo e substituir módulo(s) defeituoso(s)
    → Inspeção visual e ultrassônica completa antes de qualquer nova tentativa
    → Missão deve ser adiada até resolução de todos os alertas críticos

────────────────────────────────────────────────────────────
  DECISÃO FINAL: DECOLAGEM ABORTADA
────────────────────────────────────────────────────────────

```

## Instruções de execução do código

### Requisitos

- Python 3.10+
- pip

### Instalação

```bash
pip install -r requirements.txt
```

### Execução

1. Abra o arquivo `script.ipynb` no VS Code/Jupyter.
2. Execute a célula 1.
3. Informe os valores solicitados no terminal interativo.
4. Confira o relatório exibido no output.
5. Verifique o arquivo gerado `relatorio_do_foguete.xlsx`.

### (Opcional) Subir para GitHub

```bash
git init
git add .
git commit -m "feat: estrutura inicial do projeto"
git branch -M main
git remote add origin <URL_DO_SEU_REPOSITORIO>
git push -u origin main
```
