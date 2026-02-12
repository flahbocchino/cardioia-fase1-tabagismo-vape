# CardioIA – Fase 1 (Batimentos de Dados)  
## Tabagismo & Vapes como eixo de risco cardiovascular (18–40 anos)

🔗 **Link único com TODOS os dados (numéricos + textos + imagens):**  
https://fiapcom-my.sharepoint.com/:f:/g/personal/rm564213_fiap_com_br/IgBZcAPFC54ITZfvrtXZUAE3ASfGhsPkH7MRghijTd40ok8?e=I9bdxF

---

## Identificação (atividade individual)
- **Nome:** Flávia Bocchino  
- **RM:** 564213  
- **E-mail:** RM564213@fiap.com.br  

---

## Visão do projeto 
O CardioIA é pensado como um sistema de apoio inteligente que, no futuro, vai conseguir **cruzar dados clínicos, histórico de exposição à nicotina (tabagismo/vape), textos de referência e exames** para ajudar na **triagem e no apoio ao raciocínio clínico**.

Nesta **Fase 1**, o foco não é “dar diagnóstico”. É construir a base do projeto: **dados bem organizados**, rastreáveis e prontos para alimentar modelos e análises nas fases seguintes.

A escolha do recorte (tabagismo e vapes) é intencional: trata-se de um fator de risco atual, com impacto real em saúde pública, que se conecta bem com marcadores cardiológicos clássicos e com sinais que podem aparecer precocemente — especialmente na faixa de **18 a 40 anos**.

---

## Estrutura do repositório
- `data/`  
  Dataset numérico (CSV) + arquivos auxiliares (resumos, recortes e materiais de apoio).

- `docs/textos/`  
  Textos fonte em PDF (referências usadas como base).

- `textos_txt/`  
  Textos convertidos para `.txt` (prontos para NLP).

- `*.ipynb`  
  Notebooks do Colab usados para gerar/organizar dados (Fase 1).

---

# Parte 1 — Dados Numéricos (IoT / Dataset tabular)

## O que foi construído
Foi preparado um dataset tabular com **300 registros**, focado em perfis de pacientes jovens-adultos e variáveis relevantes para risco cardiovascular, incluindo exposição a tabaco e/ou vape.

Os arquivos principais ficam em:
- `data/`  
E também estão no OneDrive (link no topo), dentro da pasta correspondente aos dados numéricos.

## Origem dos dados
Os dados desta fase são **simulados/estruturados para fins acadêmicos**, com variáveis realistas de triagem e risco cardiovascular. A simulação existe para permitir experimentação controlada, testes de pipeline e desenvolvimento gradual do CardioIA sem depender, neste momento, de bases sensíveis.

## Variáveis clinicamente mais relevantes (e por quê)
Algumas variáveis são “coluna vertebral” do projeto por carregarem significado clínico forte:

- **Idade**: estratifica risco e muda interpretação de marcadores.
- **Pressão arterial**: indicador crítico para desfechos cardiovasculares.
- **Perfil lipídico**: associado a aterosclerose e risco cardiometabólico.
- **Frequência cardíaca**: pode refletir estresse cardiovascular e alterações.
- **Sintomas**: aproximam o dataset de um cenário real de triagem (dor torácica, dispneia, palpitações etc.).
- **Exposição a nicotina (tabagismo/vape)**: eixo do tema; conecta comportamento e risco.
- **Comorbidades / histórico familiar**: aumentam poder preditivo e realismo da base.

## Como isso vira IA depois
Esse dataset pode alimentar:
- **modelos preditivos** (estratificação de risco),
- **priorização de triagem** (quem precisa de atenção primeiro),
- **análises de correlação e importância de variáveis**,
- **checagens de viés** (como sexo/idade influenciam resultados).

---

# Parte 2 — Dados Textuais (NLP)

## O que foi preparado
Foram reunidos textos relacionados a saúde pública, risco cardiovascular, prevenção e tabagismo, e eles foram organizados em dois formatos:

- PDFs (fontes): `docs/textos/`
- TXT (prontos para NLP): `textos_txt/`

O mesmo conjunto está disponível no OneDrive (link no topo).

## Como eu imagino usar isso no CardioIA (na prática)
A ideia do CardioIA, do jeito que eu estou construindo, é funcionar como um **apoio inteligente de triagem**: o usuário (ou profissional) entra com informações básicas e o sistema cruza tudo para devolver uma leitura coerente do risco e do que merece atenção primeiro.

Um fluxo realista seria assim:

1) **Dados do paciente**
- idade
- sexo (quando aplicável)
- histórico familiar e comorbidades (quando houver)

2) **Queixa e sintomas**
- quais sintomas estão presentes (ex.: dor torácica, falta de ar, palpitações, tontura)
- há quanto tempo começaram
- intensidade e frequência (quando possível)

3) **Exposição a nicotina**
- se fuma ou usa vape
- **há quanto tempo** (anos/meses)
- frequência/intensidade (todos os dias, socialmente, “picos” no fim de semana)
- tentativas de parar e sinais de abstinência (quando relevante)

4) **Exames e sinais objetivos**
- variáveis clínicas (pressão arterial, colesterol, IMC, frequência cardíaca, SpO₂)
- imagens de exames (ECG, RX, eco, angiografia)

Com isso, o CardioIA não “dá um diagnóstico fechado”, mas entrega algo que é útil e responsável:
- **estratificação de risco** (baixo/médio/alto, com justificativa)
- **alertas de combinação perigosa** (ex.: sintomas + exposição + marcadores alterados)
- **sugestão de prioridade** (o que é mais urgente investigar primeiro)
- **explicabilidade**: quais fatores pesaram mais na análise (para não virar caixa-preta)

Os textos entram como base para o sistema “entender” linguagem de saúde e padronizar termos: por exemplo, reconhecer sinônimos, mapear sintomas descritos em linguagem comum para categorias clínicas e conectar recomendações gerais (prevenção, cessação, rastreio) com o perfil apresentado.

## Por que isso importa para IA em saúde
Em saúde, muita informação relevante não está em tabela — está em documento. NLP permite transformar texto em sinal útil: organizar conhecimento, extrair termos clínicos, melhorar consistência e apoiar sistemas inteligentes que precisem lidar com linguagem natural (protocolos, cartilhas, literatura, orientações).

---

# Parte 3 — Dados Visuais (Visão Computacional)

## O que foi preparado
Foi reunido um conjunto com **100 imagens** divididas em quatro tipos de exames (25 por categoria), em formato `.png`:

- **ECG**
- **Angiografia**
- **Raio-X de tórax**
- **Ecocardiograma**

As imagens estão organizadas por pastas no OneDrive (link no topo).

## Como essas imagens podem ser analisadas por Visão Computacional
Exemplos de uso em VC que fazem sentido para o CardioIA:

- **detecção de padrões** em traçados e estruturas (por exemplo, no ECG)
- **segmentação e detecção de bordas** para localizar regiões de interesse
- **classificação** (normal vs. suspeito, ou categorias de achados) como etapa de triagem
- **detecção de anomalias** para destacar exames fora do padrão para revisão humana

## Importância para IA aplicada à saúde
Visão Computacional é parte central do ecossistema de cardiologia moderna porque transforma exames em sinal analisável. Na prática, ela ajuda a priorizar casos, reduzir tempo de triagem e apoiar decisões com consistência — especialmente quando combinada com dados numéricos e contexto clínico.

---



