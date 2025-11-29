# Sistema de Monitoramento de Derramamento de Óleo

Este projeto apresenta um sistema de monitoramento e detecção de derramamento de óleo utilizando análise de imagens de satélite. O sistema processa patches de imagens capturadas por satélites para identificar áreas potencialmente afetadas por vazamentos de petróleo no oceano.

## Descrição do Projeto

O projeto utiliza técnicas de processamento de imagens e análise de dados para detectar derramamentos de óleo em ambientes marinhos. As imagens de satélite são divididas em pequenos segmentos (patches) que são processados individualmente para identificar anomalias que possam indicar a presença de óleo.

### Metodologia

O processo de análise envolve várias etapas:

1. Captura de imagens através de sensores de satélite que detectam reflexões de luz e radiações eletromagnéticas da superfície terrestre e marinha.

2. Divisão das imagens em patches menores de 100x100 pixels para facilitar o processamento. Por exemplo, uma imagem de 4000x4000 pixels resulta em 1600 patches (40x40).

3. Correção radiométrica para ajustar os valores de brilho e contraste das imagens, normalizando os valores entre o mínimo e máximo detectados.

4. Correção geométrica para alinhar corretamente as imagens à superfície terrestre usando transformações geométricas.

5. Realce de características importantes através de filtros de detecção de bordas, como o filtro de Sobel, para destacar áreas suspeitas.

## Estrutura do Projeto

O repositório contém os seguintes arquivos:

- `Atobá.ipynb` - Jupyter Notebook principal com o código de processamento e análise
- `oil_spill.csv` - Conjunto de dados com 49 características extraídas de patches de imagens e uma coluna target indicando presença (1) ou ausência (0) de óleo

## Dataset

O arquivo `oil_spill.csv` contém 939 registros com 50 colunas, onde:

- As colunas `f_1` a `f_49` representam características extraídas dos patches de imagem
- A coluna `target` indica se o patch contém derramamento de óleo (1) ou não (0)

As características incluem informações sobre área, perímetro, brilho, contraste, índices espectrais e outras propriedades relevantes para a detecção.

## Requisitos

O projeto utiliza as seguintes bibliotecas Python:

- NumPy - processamento numérico
- scikit-image - processamento de imagens
- Pandas - manipulação de dados

## Como Usar

1. Clone este repositório
2. Abra o notebook `Atobá.ipynb` no Jupyter Notebook ou Google Colab
3. Execute as células sequencialmente para processar as imagens e treinar o modelo de detecção
4. Os resultados da análise serão apresentados ao final do notebook

## Aplicações

Este sistema pode ser utilizado para:

- Monitoramento ambiental de áreas oceânicas
- Detecção precoce de vazamentos de petróleo
- Auxílio em operações de resposta a emergências ambientais
- Estudos de impacto ambiental em regiões costeiras

## Referências

O projeto utiliza técnicas consolidadas de processamento digital de imagens e aprendizado de máquina aplicadas ao monitoramento ambiental por sensoriamento remoto.

## Licença

Este projeto está disponível para fins educacionais e de pesquisa.
