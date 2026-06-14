# 🏭 Projeto: Análise Preditiva de Dados - AllConect

## 🎯 Objetivo Principal
Desenvolver modelos de análise e interpretação de dados operacionais de máquinas CNC para predição de falhas e monitoramento de performance. O escopo foca exclusivamente na ciência de dados e engenharia de confiabilidade, utilizando dados que já são extraídos e enviados para a nuvem pela equipe de infraestrutura.

---

## 🗺️ Plano de Ação e Fases do Projeto

### 🕵️‍♂️ Fase 1: Imersão e Aquisição da Linha de Base (Baseline)
O primeiro passo é entender a natureza física do problema antes de escrever qualquer código. Da mesma forma que se valida os parâmetros físicos antes de uma simulação complexa, precisamos conhecer a "cara" do dado real.
* **Solicitar Amostra de Dados:** Pedir à equipe parceira um arquivo estático (CSV, JSON ou XML) com pelo menos uma hora de operação contínua da máquina.
* **Mapeamento do Dicionário de Dados:** Criar uma tabela documentando o que cada coluna significa (ex: `M_SSEC_EXST_RAPID_OVERRIDE` = Override de avanço rápido em %).
* **Identificação de Variáveis Físicas:** Isolar quais dados representam temperatura, corrente do servo, posição dos eixos e códigos de alarme.

### ☁️ Fase 2: Pesquisa de Plataformas em Nuvem (Cloud Analytics)
Como a extração já está coberta, precisamos definir onde os nossos scripts de análise vão "morar" para consumir esses dados em tempo real no futuro.
* **Avaliar AWS (Amazon Web Services):**
  * Estudar o AWS SageMaker (para rodar os notebooks Python na nuvem).
  * Entender o funcionamento básico do Amazon S3 (onde os arquivos estáticos ficam salvos).
* **Avaliar Google Cloud Platform (GCP):**
  * Pesquisar sobre o Google Colab Enterprise ou Vertex AI.
  * Analisar o uso do BigQuery para ler dados com SQL de forma fácil.
* **Avaliar Microsoft Azure:**
  * Dar uma olhada no Azure Machine Learning (muito usado na indústria por ter boa integração corporativa).
* **Entrega da Fase:** Um breve relatório comparativo (pode ser uma tabela no próprio GitHub) escolhendo o ambiente mais amigável para o perfil de engenharia/análise.

### 🧪 Fase 3: O "Laboratório" Local (Limpeza e Tratamento)
Aqui é onde a mão na massa começa no seu próprio computador, sem se preocupar com a nuvem ainda. O foco é tratar a sujeira dos dados reais.
* **Configuração do Ambiente:** Instalar Python, Jupyter Notebook e as bibliotecas essenciais (`pandas`, `numpy`, `matplotlib`).
* **Tratamento de Nulos e Ruídos:** Criar rotinas para limpar valores em branco ou erros de leitura dos sensores.
* **Alinhamento Temporal:** Garantir que todas as variáveis estejam sincronizadas na mesma linha do tempo (TimeStamp).
* **Entrega da Fase:** Um script Python limpo que entra um CSV "sujo" e sai um DataFrame pronto para análise matemática.

### ⚙️ Fase 4: Engenharia de Features (Dando Significado)
O núcleo do trabalho de engenharia. Transformar os dados brutos de máquina em indicadores de integridade.
* **Criação de Variáveis Derivadas:** Calcular a variação brusca de corrente dos motores (pode indicar esforço mecânico ou ferramenta cega).
* **Cruzamento de Estados:** Correlacionar alarmes (ex: `melGetAlarmMessage`) com a carga do spindle segundos antes do evento crítico.
* **Definição de Limites (Thresholds):** Estabelecer, baseado em regras físicas, quando um comportamento sai da normalidade.

### 🧠 Fase 5: Análise Exploratória e Modelagem Inicial
A aplicação da matemática para encontrar padrões que o olho humano não veria na planilha.
* **Análise Visual:** Plotar gráficos comparativos para entender a "assinatura" de uma usinagem perfeita versus uma que gerou defeito.
* **Modelos Simples:** Aplicar árvores de decisão simples (via Scikit-Learn) para classificar o estado da máquina.

---

## 💻 Como usar este repositório (Guia Rápido)
* **`notebooks/`**: Pasta onde salvaremos nossos arquivos `.ipynb` (Jupyter) com as análises e lógicas em Python.
* **`docs/`**: Manuais da máquina, tabelas de parâmetros e relatórios de pesquisa (como o da Fase 2).
* **`data/`**: (Apenas local, não suba dados pesados pro GitHub!) Pasta para guardar as amostras de CSV/XML.
* A cada avanço em uma fase, usaremos os comandos básicos `git add`, `git commit -m "mensagem"` e `git push` para salvar o progresso.
