

# Fatores acadêmicos e de empregabilidade que influenciam a colocação.

Este projeto foi desenvolvido utilizando os conhecimentos adquiridos no Curso de Engenharia de Dados da Koru.

O objetivo é analisar a base de dados real para identificar e compreender quais variáveis estão mais associados à empregabilidade e quais fatores influenciam a colocação profissional dos alunos considerando aspetos como:

- Área com maior empregabilidade: Quais áreas de formação apresentam maior taxa de colocação no mercado de trabalho?

- Experiência prévia: pessoas com experiência conseguem emprego mais rápido?

- Gênero: Existem diferenças salariais entre gêneros dentro de uma mesma área de atuação?

- Graduação: Qual graduação está associada aos maiores salários?

- Área de formação (Tipo_Graduação) : O tipo de graduação (Sci&Tech, Commerce, Arts etc.) influencia nas oportunidades e salários?

- Notas escolares vs. empregabilidade: O desempenho escolar influencia diretamente na empregabilidade?

- Fatores determinantes:  Quais fatores realmente têm mais peso na empregabilidade: notas, graduação, experiência ou gênero?


> A empregabilidade não é só sobre conseguir um emprego. É sobre oportunidade!
O sucesso profissional não depende de um único fator, mas da combinação entre área de formação, experiência prática e contexto social.

## Base de Dados

A base de dados escolhida foi: "Fatores acadêmicos e de empregabilidade que influenciam a colocação".

A mesma se encontra na Plataforma da Kaggle. A seguir link da Plataforma. [Plataforma do Kaggle](https://www.kaggle.com/datasets/benroshan/factors-affecting-campus-placement)

### Ferramentas utilizadas no projeto

- Python para manipulação e análise de dados
- Pandas e SQL para tratamento de dados
- Looker para apresentar os insights
- Git/GitHub para versionar e compartilhar o Projeto

### Metodologia

- Coleta e compreensão da base de dados
- Limpeza e tratamento dos dados
- Análise exploratória
- Geração de insights
- Visualização dos resultados


### Estrutura do projeto

1.   📦 data/         → Bases originais e tratadas
2.   📓 notebooks/    → Análises exploratórias e insights
3. 🧪 src/          → Scripts de limpeza e transformação
4. 📊 reports/      → Dashboards e relatórios finais
5. 📄 README.md     → Você está aqui!


### Análises de Dados
1.   Experiência prévia: pessoas com experiência conseguem emprego mais rápido?
Consulta Aqui. [Consulta Aqui](https://console.cloud.google.com/bigquery?inv=1&invt=Ab4KKQ&project=t1engenhariadados&ws=!1m12!1m3!8m2!1s1026184274595!2sd5a463e1c7024e26811f77142b3efad2!1m3!8m2!1s1026184274595!2s7db49a29917744b09d77d840bdce6d77!1m3!8m2!1s1026184274595!2s94a9ac2928be440c90e5584754b8e4a8)

2.   Gênero: Existem diferenças salariais entre gêneros dentro de uma mesma área de atuação? [Consulta Aqui.](https://console.cloud.google.com/bigquery?ws=!1m5!1m4!4m3!1st1engenhariadados!2sGrupo_3_9_ProjetoFinal!3sPergunta2)


3. Graduação: Qual graduação está associada aos maiores salários? [Consulta Aqui.](https://console.cloud.google.com/bigquery?ws=!1m7!1m6!12m5!1m3!1st1engenhariadados!2sus-central1!3se43b0604-4d7e-41a0-8cef-ac2217cec3dc!2e1)


4. Área de formação (Tipo_Graduação) : O tipo de graduação (Sci&Tech, Commerce, Arts etc.) influencia nas oportunidades e salários? [Consulta Aqui.](https://console.cloud.google.com/bigquery?ws=!1m7!1m6!12m5!1m3!1st1engenhariadados!2sus-central1!3se43b0604-4d7e-41a0-8cef-ac2217cec3dc!2e1)

5. Fatores determinantes:  Quais fatores realmente têm mais peso na empregabilidade: notas, graduação, experiência ou gênero? [Consulta Aqui](https://https://console.cloud.google.com/bigquery?ws=!1m5!1m4!4m3!1st1engenhariadados!2sGrupo_3_9_ProjetoFinal!3sPergunta7)


6. Notas escolares vs. empregabilidade: O desempenho escolar influencia diretamente na empregabilidade?


> Código SQL -- 5. Notas Escolares vs. Empregabilidade



```
# -- Calcula a média de todas as notas, agrupando por status de colocação.
SELECT
    Status_colocação,
    AVG(NotaEns_Fundamental) AS Media_Ens_Fundamental,
    AVG(NotaEns_Medio) AS Media_Ens_Medio,
    AVG(Nota_Graduacao) AS Media_Graduacao,
    AVG(Nota_Test_Empregabilidade) AS Media_Teste_Empregabilidade,
    AVG(`Nota_Especialização`) AS Media_Especializacao
FROM
   `t1engenhariadados.Grupo_3_9_ProjetoFinal.Placement_Data_Full_Class`
GROUP BY
    Status_colocação;

```

### Análise de Hipotese

Em termos simples, nós criamos duas afirmações opostas:
- Hipótese Nula (H₀): A afirmação padrão, de que "não há efeito" ou "não há diferença". Por exemplo: "Não há diferença no salário médio entre homens e mulheres".

- Hipótese Alternativa (H₁): A afirmação que queremos provar. Por exemplo: "Existe uma diferença no salário médio entre homens e mulheres".
O teste estatístico nos dará um p-valor.
p-valor: É a probabilidade de observarmos os dados que temos (ou dados ainda mais extremos) se a Hipótese Nula (H₀) for verdadeira.
Regra de decisão: Se o p-valor for muito baixo (geralmente < 0.05), consideramos o resultado "estatisticamente significativo". Isso nos dá forte evidência para rejeitar a Hipótese Nula (H₀) em favor da Hipótese Alternativa (H₁).
Vamos definir nosso nível de significância (alfa) como α = 0.05.

- **Hipótese 1: Gênero e Salário**
Nossa análise descritiva mostrou que homens têm um salário médio maior. Mas essa diferença é estatisticamente significativa?
Hipótese Nula (H₀): O salário médio de homens colocados é igual ao salário médio de mulheres colocadas.
Hipótese Alternativa (H₁): O salário médio de homens colocados é diferente do salário médio de mulheres colocadas.
Teste a ser usado: Teste T de duas amostras independentes (ideal para comparar as médias de dois grupos).
- **Codigo Python**



```
from scipy.stats import ttest_ind
import pandas as pd

df = pd.read_csv('Tratado_Placement_Data_Full_Class.csv')

# Filtrar apenas alunos colocados
df_placed = df[df['Status_colocação'] == 'Placed']

# Separar os salários por gênero
salario_homens = df_placed[df_placed['Genero'] == 'M']['salario']
salario_mulheres = df_placed[df_placed['Genero'] == 'F']['salario']

# Realizar o teste T
t_stat, p_valor = ttest_ind(salario_homens, salario_mulheres, nan_policy='omit')

print(f"P-valor do teste T para gênero e salário: {p_valor}")

if p_valor < 0.05:
    print("Resultado: Rejeitamos a Hipótese Nula.")
else:
    print("Resultado: Não podemos rejeitar a Hipótese Nula.")

#

```
**Resultado e Interpretação:** Ao executar o código, o p-valor obtido é aproximadamente 0.209.
P-valor do teste T para gênero e salário: 0.209...
Resultado: Não podemos rejeitar a Hipótese Nula.
Conclusão Estatística: Apesar de a análise descritiva mostrar uma diferença nos salários médios, o p-valor (0.21) é maior que nosso nível de significância (0.05). Isso significa que a diferença observada nos salários entre homens e mulheres nesta amostra de dados não é estatisticamente significativa. Em outras palavras, com estes dados, não temos evidências fortes o suficiente para afirmar que existe uma diferença salarial real entre os gêneros na população de onde a amostra foi retirada; a diferença que vemos pode ser devida ao acaso.

### Visualização do Dado Looker Studio 
[Visualizar Aqui](https://lookerstudio.google.com/reporting/882a22bd-2543-4119-82e4-34097e77e421)

### 🎓 Sobre nós!

Somos o gruoo 3_9, formado por:

- Carolina Soares
- Diennifer Novaes
- Eloísa Caratéu
- Juliana Almeida
- Marcelo Maia
- Yuki Vidal

