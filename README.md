# Trilha A: Plataforma Multicloud com IA - Análise de Instâncias AWS EC2

Este projeto faz parte da **Trilha A** do programa de capacitação em ambientes multicloud com foco em **eficiência financeira** e uso de **Inteligência Artificial**. O objetivo principal foi realizar uma **análise exploratória e estatística** dos preços das instâncias EC2 da AWS, considerando diferentes regiões, categorias, sistemas operacionais e configurações de hardware.

---

## Objetivos

- Coletar dados da API pública da AWS Pricing.
- Analisar variações de custo por região e sistema operacional.
- Identificar instâncias com melhor **custo-benefício**.
- Avaliar o impacto do uso de **GPU** no preço final.
- Aplicar **testes estatísticos** para validar hipóteses.

---

## Tecnologias Utilizadas

- **Python**
- **Pandas / NumPy**
- **Matplotlib / Seaborn / Plotly**
- **Boto3** (AWS SDK para Python)
- **SciPy / scikit-posthocs** (testes estatísticos)

---

## Coleta de Dados

Os dados foram coletados diretamente da **API de preços da AWS (AWS Pricing API)** utilizando o boto3 com autenticação via chaves temporárias. Foram consideradas instâncias das seguintes categorias:

- **Uso Geral**
- **Computação Acelerada**
- **Memória**
- **Armazenamento**

Regiões analisadas:

- US East (N. Virginia)
- US West (Oregon)
- Europe (Ireland)
- South America (São Paulo)
- Asia Pacific (Tokyo)

---

## Principais Resultados

### Regiões
- O **Brasil** apresentou os **maiores preços médios** para instâncias com GPU.
- Em categorias como **Uso Geral**, os preços são competitivos regionalmente.

### Sistemas Operacionais
- **Linux** possui o **menor custo médio** na maioria das categorias.
- **Windows**, surpreendentemente, teve o menor custo em **Computação Acelerada**.
- Diferenças estatísticas significativas foram encontradas entre:
  - Linux x RHEL (Uso Geral)
  - Linux x SUSE (Memória)

### Custo-Benefício
- Instância `t3.nano` apresentou o **melhor índice de custo-benefício** globalmente.
- Instâncias com GPU, como `p4d.24xlarge`, devem ser utilizadas com critério devido ao custo elevado.

---

## Metodologia

1. **Coleta automática** dos preços com filtros por instância, região, SO e tenancy.
2. **Criação de métricas** como índice de custo-benefício:  
   \[
   \text{Índice} = \frac{\text{vCPU} + \text{RAM}}{\text{Preço}}
   \]
3. Aplicação de **testes de normalidade** (Shapiro-Wilk) e **Kruskal-Wallis** para verificar diferenças estatísticas entre grupos.
4. Testes **post-hoc de Dunn** para comparar pares de sistemas operacionais.

---

## Conclusão

A análise evidenciou que é possível tomar decisões mais eficientes ao escolher instâncias com base em dados. Instâncias como `t3.nano` se destacam pelo ótimo custo-benefício, enquanto o uso de SOs como RHEL ou instâncias com GPU pode elevar significativamente o custo total.

Este projeto reforça o papel da ciência de dados na **otimização de infraestrutura em nuvem**, contribuindo para **estratégias multicloud mais inteligentes e econômicas**.

---

## Próximos Passos

- Estender a análise para outros provedores (Azure, GCP).
- Incorporar dados reais de consumo para medir desempenho vs. custo.
- Criar um dashboard interativo com **Streamlit** ou **Plotly Dash**.

---

## Estrutura do Projeto
```
TRILHA_A_DADOS_IA/
├── notebooks/               # Pasta com os notebooks Jupyter
│   └── trilhaA/             # Notebooks específicos da Trilha A
│       └── notebook.ipynb   # Notebook principal com a análise
├── .gitattributes           # Configurações do Git
├── README.md                # Documentação do projeto
└── requirements.txt         # Dependências do projeto
```

## Instalação e Configuração

### Pré-requisitos
- Python 3.8 ou superior
- Gerenciador de pacotes `pip`
- Ambiente virtual (recomendado)

### Passos para Configuração

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/mh-pedro/TRILHA_A_DADOS_IA.git
   cd TRILHA_A_DADOS_IA

2. **Crie e ative um ambiente virtual (opcional):**

   ```bash
    python -m venv venv
    source venv/bin/activate    # Linux/Mac
    venv\Scripts\activate       # Windows
   ```
3. **Instale as dependências:**
   ```bash
   pip install -r requirements.txt
   ```
4. **Configure as credenciais AWS:**
    AWS_ACCESS_KEY_ID=seu_access_key
    AWS_SECRET_ACCESS_KEY=seu_secret_key
    AWS_REGION=us-east-1

    OBS.: Foram usadas as credenciais de uma conta de teste.

5. **Execute o notebook:**
   ```bash
   jupyter notebook notebooks/trilhaA/notebook.ipynb
   ```

---
## Autor

Pedro Henrique Morais  
[LinkedIn](https://www.linkedin.com/in/mhpedro/) | [GitHub](https://github.com/mh-pedro)  
