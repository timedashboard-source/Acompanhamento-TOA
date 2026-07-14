# 📊 Acompanhamento de Quebra - TOA

Dashboard operacional interativo para análise de **Quebras de Agenda** .
100% client-side (HTML + JavaScript), funciona direto no navegador — **sem servidor, sem instalação**.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![Chart.js](https://img.shields.io/badge/Chart.js-FF6384?style=flat&logo=chartdotjs&logoColor=white)
![Offline](https://img.shields.io/badge/100%25-Offline-2fa84f?style=flat)

---

## 🎯 Sobre o projeto

Este dashboard analisa dados operacionais de **quebras de agenda**, calculando indicadores como
**Break Rate** (taxa de falha), evolução temporal, ranking de motivos (Pareto) e ofensores por login.

Basta fazer o **upload** de uma planilha `.xlsx` ou `.csv` — todo o processamento acontece
**localmente no seu navegador**. Nenhum dado é enviado para nenhum servidor. 🔒

---

## ✨ Funcionalidades

### 🔎 6 Filtros dinâmicos
- **Categorias da Capacidade** (Categorias da Capacidade)
- **UN** (Recurso Pai)
- **Mês / Ano** (MM/AAAA)
- **Data** (DD/MM/AAAA)
- **Quebras** (Cód de Baixa 1)
- **Tipo de Atividade**

> Todos com **busca**, atalhos **"Marcar todos" / "Desmarcar todos"**, chips removíveis e limpar individual.

### 📑 6 Abas de análise
| Aba | Conteúdo |
|-----|----------|
| **Visão Executiva** | Cód Baixa (Top 20 %), UN (%), KPIs de validação, Pontos Percentuais |
| **Quebra Agenda Janela** | Distribuição por janela de serviço (08-12 / 12-15 / 15-18) |
| **Pareto** | Top 6 motivos + linha de % acumulado |
| **Evolutivo** | Evolução diária das 15 principais quebras |
| **Evolutivo Quebras** | Tabela pivô + linha semanal + barras mensal/diária + Volume Diário (%) |
| **Login Ofensor** | Ranking de técnicos por quebra (estilo funil) |

### ⚙️ Regras de negócio automáticas
- Exclui as Classes **4, 5, 6, 7, 8, 9, 10, 12, 14**
- Mantém o código **409 (Serviço Concluído)** apenas para o cálculo do **Break Rate**
- **Deduplicação** por `Contrato + Data`
- Remove registros "Sem Informação"

### 🧮 Break Rate (Taxa de Quebra)
```
% Quebras do Dia = Quebras ÷ (Quebras + Executados 409) × 100
```

### 📤 Exportação
- **Baixar CSV filtrado** — exporta somente os dados após todos os filtros aplicados

### 🚀 Leitor Excel nativo integrado
- Interpreta arquivos `.xlsx` **sem bibliotecas externas** (usa `DecompressionStream` + `DOMParser`)
- Funciona **100% offline** após o primeiro carregamento
- Fallback automático de CDN para o Chart.js (jsDelivr → unpkg → cdnjs)

---

## 🖥️ Como usar

1. Abra o `index.html` no navegador (**Chrome / Edge 80+** ou **Firefox 113+**)
2. Clique em **⬆ Upload** e selecione sua planilha `.xlsx` ou `.csv`
3. Explore as abas e aplique os filtros
4. Use **Baixar CSV filtrado** para exportar o recorte analisado

> 💡 A barra de status mostra em tempo real: linhas brutas, após regras e após filtros.

---

## 🌐 Como publicar no GitHub Pages

1. Crie um repositório novo (ex.: `dashboard-toa-salvador`)
2. Faça upload do arquivo **`index.html`** (e opcionalmente o `README.md`)
3. Vá em **Settings → Pages**
4. Em **Source**, escolha a branch `main` e a pasta `/ (root)`
5. Clique em **Save**
6. Aguarde ~1 minuto e acesse a URL gerada:
   `https://SEU-USUARIO.github.io/dashboard-toa-salvador/`

✅ Pronto! O dashboard estará no ar.

---

## 🔒 Privacidade dos dados

> **Importante:** este dashboard é **100% client-side**.
> Os dados da sua planilha **nunca saem do seu computador** — não há backend, banco de dados
> nem envio para servidores. Todo o processamento ocorre na memória do navegador.

⚠️ **Nunca faça commit de planilhas com dados sensíveis** no repositório.
O arquivo `.gitignore` já bloqueia `.xlsx` e `.csv` por segurança.

---

## 🛠️ Stack técnica

- **HTML5 + CSS3** (layout responsivo, tema claro, cor principal `#d71920`)
- **JavaScript puro (ES2020+)** — sem frameworks
- **[Chart.js 4](https://www.chartjs.org/)** + plugin datalabels (via CDN com fallback)
- **Parser XLSX nativo** (ZIP + DecompressionStream + DOMParser)

---

## 📄 Licença

Distribuído sob a licença **MIT**. Veja o arquivo [`LICENSE`](LICENSE) para mais detalhes.

---

<div align="center">
Feito com ❤️ para a operação <b>TOA Salvador</b>
</div>
