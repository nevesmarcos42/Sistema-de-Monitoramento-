# Sistema de Monitoramento de Derramamento de Óleo - Atobá

<div align="center">

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![NumPy](https://img.shields.io/badge/NumPy-Latest-013243?style=for-the-badge&logo=numpy)
![Pandas](https://img.shields.io/badge/Pandas-Latest-150458?style=for-the-badge&logo=pandas)
![scikit-image](https://img.shields.io/badge/scikit--image-Latest-F7931E?style=for-the-badge&logo=scikit-learn)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=for-the-badge&logo=jupyter)

Sistema de monitoramento e detecção de derramamento de óleo utilizando análise de imagens de satélite e machine learning. Processamento de patches de imagens capturadas por satélites para identificar áreas afetadas por vazamentos de petróleo no oceano.

[Funcionalidades](#funcionalidades) • [Tecnologias](#tecnologias) • [Dataset](#dataset) • [Instalação](#instalação) • [Uso](#uso) • [Metodologia](#metodologia) • [Aplicações](#aplicações)

</div>

---

## Índice

- [Sobre o Projeto](#sobre-o-projeto)
- [Funcionalidades](#funcionalidades)
- [Tecnologias](#tecnologias)
- [Dataset](#dataset)
- [Metodologia](#metodologia)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Instalação](#instalação)
- [Uso](#uso)
- [Aplicações](#aplicações)
- [Contribuindo](#contribuindo)
- [Licença](#licença)

---

## Sobre o Projeto

O **Sistema de Monitoramento Atobá** é uma solução de detecção de derramamento de óleo em ambientes marinhos utilizando análise de imagens de satélite. O projeto aplica técnicas avançadas de processamento de imagens e machine learning para identificar anomalias que possam indicar a presença de óleo no oceano, auxiliando em ações de monitoramento ambiental e resposta rápida a emergências.

### Principais Características

- **Processamento de Imagens de Satélite** - Análise automatizada de imagens capturadas por sensores remotos
- **Detecção Inteligente** - Algoritmos de machine learning para identificação de derramamento de óleo
- **Análise de Patches** - Divisão estratégica de imagens em segmentos de 100x100 pixels para processamento otimizado
- **Correção Radiométrica e Geométrica** - Normalização e ajuste de imagens para maior precisão
- **Extração de Características** - 49 features extraídas incluindo área, perímetro, brilho, contraste e índices espectrais
- **Filtros Avançados** - Aplicação de filtros de detecção de bordas (Sobel) para realce de áreas suspeitas
- **Dataset Rico** - Base de dados com 939 registros para treinamento e validação de modelos

---

## Funcionalidades

### Processamento de Imagens

- **Captura via Satélite** - Processamento de imagens de sensores que detectam reflexões de luz e radiações eletromagnéticas
- **Divisão em Patches** - Segmentação automática de imagens grandes (ex: 4000x4000 pixels → 1600 patches de 100x100)
- **Correção Radiométrica** - Ajuste de brilho e contraste com normalização entre valores mínimos e máximos
- **Correção Geométrica** - Alinhamento preciso das imagens à superfície terrestre usando transformações geométricas
- **Detecção de Bordas** - Aplicação de filtros Sobel para destacar áreas com características suspeitas

### Análise e Machine Learning

- **Extração de Features** - 49 características extraídas automaticamente de cada patch
- **Classificação Binária** - Modelo para identificar presença (1) ou ausência (0) de óleo
- **Análise de Índices Espectrais** - Avaliação de propriedades espectrais específicas de derramamentos
- **Validação de Resultados** - Métricas de desempenho para garantir precisão do modelo

---

## Tecnologias

### Python & Bibliotecas

| Tecnologia       | Versão | Descrição                              |
| ---------------- | ------ | -------------------------------------- |
| **Python**       | 3.x    | Linguagem de programação               |
| **NumPy**        | Latest | Processamento numérico e arrays        |
| **Pandas**       | Latest | Manipulação e análise de dados         |
| **scikit-image** | Latest | Processamento de imagens               |
| **Jupyter**      | Latest | Ambiente interativo de desenvolvimento |

### Ferramentas de Análise

- **Filtros de Sobel** - Detecção de bordas e realce de características
- **Normalização Radiométrica** - Ajuste de valores de pixel
- **Transformações Geométricas** - Correção de distorções espaciais
- **Machine Learning** - Algoritmos de classificação para detecção

---

## Dataset

O arquivo `oil_spill.csv` contém **939 registros** com **50 colunas**:

### Estrutura dos Dados

- **Colunas `f_1` a `f_49`** - 49 características extraídas dos patches de imagem, incluindo:
  - Área e perímetro
  - Brilho médio e contraste
  - Índices espectrais
  - Propriedades de textura
  - Informações de gradiente
  - Métricas de forma e distribuição
- **Coluna `target`** - Classificação binária:
  - `1` - Presença de derramamento de óleo
  - `0` - Ausência de derramamento de óleo

### Características do Dataset

- Total de registros: **939**
- Features por registro: **49**
- Balanceamento: Distribuição entre classes positiva e negativa
- Formato: CSV (Comma-Separated Values)

---

## Metodologia

O processo de análise e detecção segue um pipeline estruturado:

### 1. Captura de Imagens

- Sensores de satélite detectam reflexões de luz e radiações eletromagnéticas
- Imagens da superfície terrestre e marinha são capturadas em alta resolução

### 2. Pré-processamento

- **Divisão em Patches**: Imagens grandes são divididas em segmentos menores (100x100 pixels)
  - Exemplo: Imagem 4000x4000 → 1600 patches (40x40 grid)
- **Correção Radiométrica**: Normalização de valores de brilho e contraste
- **Correção Geométrica**: Alinhamento espacial usando transformações geométricas

### 3. Extração de Características

- Aplicação de filtros de detecção de bordas (Sobel)
- Cálculo de 49 features por patch:
  - Propriedades espaciais (área, perímetro)
  - Propriedades espectrais (índices, reflectância)
  - Propriedades de textura (contraste, homogeneidade)

### 4. Classificação

- Modelo de machine learning treinado com dataset rotulado
- Predição binária: presença ou ausência de óleo
- Validação e ajuste de hiperparâmetros

---

## Estrutura do Projeto

```
Sistema-de-Monitoramento/
├── Atobá.ipynb          # Notebook principal com pipeline completo
├── oil_spill.csv        # Dataset com 939 registros e 49 features
├── README.md            # Documentação do projeto
└── Atobá_               # Diretório adicional de recursos
```

### Componentes Principais

- **Atobá.ipynb** - Jupyter Notebook contendo:
  - Carregamento e exploração de dados
  - Pré-processamento de imagens
  - Extração de características
  - Treinamento de modelos
  - Análise de resultados
- **oil_spill.csv** - Dataset estruturado com:
  - Features extraídas de patches de imagens de satélite
  - Labels de classificação (presença/ausência de óleo)

---

## Instalação

### Pré-requisitos

- **Python** 3.x - [Download](https://www.python.org/downloads/)
- **Jupyter Notebook** - Incluído no Anaconda ou instalável via pip

### Instalação Local

#### 1. Clone o repositório

```bash
git clone https://github.com/nevesmarcos42/Sistema-de-Monitoramento-.git
cd Sistema-de-Monitoramento-
```

#### 2. Crie um ambiente virtual (recomendado)

```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Linux/Mac
python3 -m venv venv
source venv/bin/activate
```

#### 3. Instale as dependências

```bash
pip install numpy pandas scikit-image jupyter matplotlib seaborn scikit-learn
```

#### 4. Inicie o Jupyter Notebook

```bash
jupyter notebook
```

#### 5. Abra o notebook

- Navegue até `Atobá.ipynb` no navegador
- Execute as células sequencialmente

### Instalação via Google Colab (Alternativa)

1. Acesse [Google Colab](https://colab.research.google.com/)
2. Faça upload do arquivo `Atobá.ipynb`
3. Faça upload do arquivo `oil_spill.csv`
4. Execute as células diretamente no navegador

---

## Uso

### Executando o Pipeline Completo

1. **Inicie o Jupyter Notebook**

   ```bash
   jupyter notebook Atobá.ipynb
   ```

2. **Execute as Células Sequencialmente**:

   - Importação de bibliotecas
   - Carregamento do dataset `oil_spill.csv`
   - Exploração e visualização de dados
   - Pré-processamento e normalização
   - Treinamento do modelo de classificação
   - Avaliação de métricas (acurácia, precisão, recall, F1-score)
   - Visualização de resultados

3. **Análise de Resultados**:
   - Matriz de confusão
   - Curvas ROC
   - Importância de features
   - Exemplos de predições

### Processando Novas Imagens

Para processar novas imagens de satélite:

1. Divida a imagem em patches de 100x100 pixels
2. Aplique correções radiométrica e geométrica
3. Extraia as 49 características definidas no pipeline
4. Use o modelo treinado para classificação
5. Visualize áreas identificadas com derramamento

---

## Aplicações

Este sistema pode ser utilizado para:

### Monitoramento Ambiental

- **Vigilância Contínua** - Monitoramento de áreas oceânicas em tempo real
- **Zonas Costeiras** - Proteção de ecossistemas marinhos sensíveis
- **Rotas Marítimas** - Acompanhamento de áreas com alto tráfego de navios

### Resposta a Emergências

- **Detecção Precoce** - Identificação rápida de vazamentos de petróleo
- **Mapeamento de Extensão** - Delimitação precisa de áreas afetadas
- **Planejamento de Ações** - Suporte à tomada de decisão em operações de contenção

### Estudos Ambientais

- **Impacto Ambiental** - Avaliação de danos em regiões costeiras
- **Pesquisa Científica** - Análise de padrões de dispersão de óleo
- **Validação de Modelos** - Comparação com simulações de dispersão

---

## Contribuindo

Contribuições são bem-vindas! Siga os passos:

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/MinhaFeature`)
3. Commit suas mudanças (`git commit -m 'Adiciona MinhaFeature'`)
4. Push para a branch (`git push origin feature/MinhaFeature`)
5. Abra um Pull Request

### Padrões de Código

- Seguir convenções de código Python (PEP 8)
- Documentar funções e classes com docstrings
- Adicionar comentários explicativos em análises complexas
- Testar código antes de submeter Pull Request

---

## Licença

Este projeto está disponível para fins educacionais e de pesquisa.

---

**Desenvolvido como projeto de monitoramento ambiental e sensoriamento remoto**

---

**Versão**: 1.0.0

**Última Atualização**: Novembro 2025
