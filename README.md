# README: Simulação de Transmissão Digital de Áudio em Jupyter Notebook a partir da Pulse Code Modulation e Codificação de Linha

Este projeto simula um sistema completo de transmissão digital de áudio usando Python em um ambiente Jupyter Notebook.

## Pré-requisitos
- Python 3.6+
- Jupyter Notebook
- Bibliotecas Python: NumPy, SciPy, Matplotlib, PyGame

Instale as dependências:
```bash
pip install numpy scipy matplotlib pygame notebook
```

## Como Executar
1. Inicie o Jupyter Notebook:
```bash
jupyter notebook
```
2. Abra o notebook `Simulacao_Transmissao_Digital.ipynb`
3. Execute as células sequencialmente:
   - Todas as células: Kernel > Restart & Run All
   - Células individuais: Shift+Enter

## Estrutura do Notebook

### 1. Configuração Inicial
- Importação de bibliotecas
- Parâmetros globais (bits por amostra, faixa de SNR)

### 2. Processamento de Áudio
- Leitura de arquivo WAV
- Normalização e quantização PCM
- Codificação para binário (8 bits/amostra)

### 3. Codificações de Linha
- Implementação de três esquemas:
  - On-Off (1 → 1V, 0 → 0V)
  - Polar (1 → +1V, 0 → -1V)
  - Manchester (1 → [+1,-1], 0 → [-1,+1])

### 4. Simulação de Canal
- Adição de ruído AWGN
- Detecção por limiar
- Cálculo de BER (Bit Error Rate)

### 5. Análise de Resultados
- Gráfico comparativo BER vs SNR
- Visualização de formas de onda
- Estatísticas de desempenho

## Saídas Esperadas
1. **Gráfico BER vs SNR**: Comparação do desempenho das três codificações
2. **Visualizações de Sinais**:
   - Forma de onda original
   - Sinal quantizado
   - Sinais codificados
   - Sinais com ruído
3. **Estatísticas**:
   - Taxa de erro para cada codificação
   - Potência do sinal e ruído
   - Número de bits transmitidos

## Recomendações
1. Usar arquivos WAV curtos para simulação rápida
2. Para melhor qualidade de áudio, aumente `BITS_POR_AMOSTRA`
3. Ajuste a faixa de SNR para observar diferentes cenários de ruído


## Personalização
Ajuste estes parâmetros na segunda célula:
```python
ARQUIVO_AUDIO = "seu_audio.wav"  # Arquivo de entrada
BITS_POR_AMOSTRA = 8             # Resolução de quantização
SNR_dB = np.arange(SNR_MIN , SNR_MAX + PASSO_SNR , PASSO_SNR) #dB              
```

## Resultados Esperados
- **Melhor desempenho**: Codificação Polar
- **Pior desempenho**: Codificação On-Off
- **Manchester**: Intermediário, com vantagem de sincronismo

