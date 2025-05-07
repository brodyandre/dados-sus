## 📌 Análise de Dados do SUS (Sistema Único de Saúde)

Este projeto tem como objetivo realizar operações de manipulação de dados provenientes de um arquivo CSV do **Sistema Único de Saúde (SUS)**. A análise é realizada utilizando o Google Colab para execução dos códigos e o Google Drive para armazenamento e leitura dos dados.

---

## 🗂️ **Etapas do Projeto**

1. **Importação das Bibliotecas Necessárias**
   - `pandas` para manipulação de DataFrames.
   - `csv` para detecção de delimitadores.
   - `google.colab` para montar o Google Drive.

   ```python
   from google.colab import drive
   import pandas as pd
   import csv
   ```

2. **Montagem do Google Drive**
   - Permite o acesso aos arquivos do Drive diretamente no Google Colab.

   ```python
   drive.mount('/content/drive')
   ```

3. **Leitura do Arquivo CSV**
   - Leitura inicial do arquivo CSV com encoding específico e delimitador `;`.

   ```python
   df = pd.read_csv('/dados_sus.csv', encoding='ISO-8859-1', sep=';', on_bad_lines='skip')
   ```

4. **Detecção do Delimitador**
   - Para confirmar o delimitador do arquivo, foi usada uma amostra do conteúdo:

   ```python
   with open('/dados_sus.csv', 'r', encoding='ISO-8859-1') as f:
       sample = f.read(1024)
       dialect = csv.Sniffer().sniff(sample)
       print(f"O separador detectado é: '{dialect.delimiter}'")
   ```

5. **Leitura Ajustada do Dataset**
   - Remoção das três primeiras linhas do cabeçalho e uso do delimitador detectado.

   ```python
   df = pd.read_csv('/dados_sus.csv', encoding='ISO-8859-1', sep=dialect.delimiter, header=3)
   ```

6. **Remoção das Últimas Linhas Indesejadas**
   - Algumas linhas no rodapé do arquivo foram ignoradas.

   ```python
   df = pd.read_csv('/dados_sus.csv',
                    encoding='ISO-8859-1',
                    sep=';',
                    header=3,
                    skipfooter=9,
                    engine='python')
   ```

7. **Salvando o DataFrame no Google Drive**
   - O DataFrame processado foi salvo novamente como um arquivo CSV.

   ```python
   df.to_csv('/content/drive/My Drive/dataframe_dados_sus.csv', index=False)
   ```

---

## 📂 **Estrutura de Diretórios**
```plaintext
📦 Google Drive
 ┣ 📂 Colab Notebooks
 ┃ ┣ 📄 dados_sus.csv
 ┃ ┗ 📄 notebook_sus.ipynb
 ┣ 📂 Meu Drive
 ┃ ┗ 📄 dataframe_dados_sus.csv
```

---

## 🚀 **Como Executar o Projeto**
1. Abra o Google Colab: [Google Colab](https://colab.research.google.com/)
2. Monte seu Google Drive:
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```
3. Verifique o caminho do arquivo CSV e ajuste no código se necessário.
4. Execute as células sequencialmente.

---

## 📊 **Prévia dos Dados**
Os dados representam os investimentos realizados pelo SUS nas Unidades Federativas, segmentados por mês e ano.

```plaintext
  Unidade da Federação     2008/Jan     2008/Fev     2008/Mar     2008/Abr
0             Rondônia   1388528,39   2931283,42   1541682,52   1525314,96
1                 Acre    902416,00   1497206,26   1794028,48   1730469,42
2             Amazonas   4735529,42   7118990,57   8196635,49   8259378,42
```

---

## 🤝 **Como Contribuir**
1. Faça um fork do repositório.
2. Crie uma branch para sua feature:
   ```bash
   git checkout -b feature/nova-feature
   ```
3. Adicione suas alterações:
   ```bash
   git add .
   git commit -m 'Adicionando nova feature'
   ```
4. Envie um PR (Pull Request) para revisão.

---

## 📜 **Licença**
Projeto sob licença MIT - sinta-se livre para utilizar.

---

## ✉️ **Contato**
- **GitHub**: [brodyandre](https://github.com/brodyandre)
- **Email**: landresouza36@gmail.com
- **LinkedIn**: [Luiz André de Souza](https://www.linkedin.com/in/luiz-andre-de-souza/)
""
