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
============================================================

 ANÁLISE ENERGÉTICA
	Capacidade Total     : 500.0 kWh
	Carga Atual          : 460.0 kWh
	Consumo Real Total   : 129.6 kWh
	Autonomia Pós-Dec.   : 330.4 kWh  Suficiente

 ANÁLISE DE IA
	Classificações:
		• Temperatura interna: NOMINAL
		• Energia: ADEQUADA
	Anomalias:
		⚠ Nenhuma anomalia detectada

 DECISÃO FINAL: PRONTO PARA DECOLAR
============================================================
```

### Print 2 — Cenário abortado

```text
============================================================
 RELATORIO DE VERIFICAÇÃO
============================================================

 ALERTAS
	[ALERTA] Temperatura externa fora do limite
	[ALERTA] Nível de energia insuficiente
	[CRÍTICO] Pressão tanque oxidante fora do limite

 ANÁLISE ENERGÉTICA
	Autonomia Pós-Dec.   : -9.6 kWh  Insuficiente

 ANÁLISE DE IA
	Anomalias:
		⚠ Nível de energia abaixo do mínimo recomendado
		⚠ Pressão em tanques próxima ao limite inferior

 DECISÃO FINAL: DECOLAGEM ABORTADA
============================================================
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
