# ⚖️ TJDF - Análise de Processos Judiciais

Programa em C para leitura, processamento e análise de dados de processos judiciais do TJDFT (Tribunal de Justiça do Distrito Federal e dos Territórios), a partir de um arquivo CSV. O projeto extrai estatísticas relevantes, identifica processos com temas sensíveis (violência doméstica, feminicídio, meio ambiente, comunidades quilombolas, povos indígenas e infância/juventude) e calcula o cumprimento da **Meta 01** do CNJ.

## 📖 Sobre o projeto

O programa lê um arquivo CSV contendo processos judiciais (`TJDFT_filtrado.csv`), carrega os dados em memória e disponibiliza um conjunto de funções para:

- Buscar informações de um processo específico a partir do seu ID.
- Encontrar o processo mais antigo com base na data de recebimento.
- Calcular a diferença de dias entre o recebimento e a resolução de um processo.
- Contabilizar processos marcados com flags temáticas específicas.
- Calcular o percentual de cumprimento da Meta 01 (relação entre processos julgados e o total de processos distribuídos, descontados suspensos e dessarquivados).
- Gerar um novo arquivo CSV (`filtrado.csv`) contendo apenas os processos já julgados na Meta 01.

## ✨ Funcionalidades

- **Carregamento de CSV**: parser próprio para arquivos CSV separados por `;`, com tratamento de campos vazios e alocação dinâmica de memória.
- **Busca por ID**: retorna o último órgão julgador (OJ) de um processo.
- **Processo mais antigo**: percorre a lista e retorna a data de recebimento mais antiga.
- **Cálculo de datas**: conversão de datas para número de dias corridos (considerando anos bissextos), usada para calcular o intervalo entre recebimento e resolução.
- **Contadores de flags**: violência doméstica, feminicídio, matéria ambiental, comunidades quilombolas, povos indígenas e ECA (infância e juventude).
- **Meta 01**: cálculo do percentual de cumprimento conforme fórmula do CNJ.
- **Exportação**: geração de um novo CSV apenas com os processos julgados na Meta 01.

## 🛠️ Tecnologias utilizadas

- **Linguagem C** (padrão C99/C11)
- Bibliotecas padrão: `stdio.h`, `stdlib.h`, `string.h`

## 📁 Estrutura do projeto

```
TJDF-master/
├── main.c        # Ponto de entrada do programa, exemplos de uso das funções
├── TJDF.c        # Implementação das funções de carregamento e análise dos processos
├── TJDF.h        # Definição da struct Processo e assinaturas das funções
└── teste.exe     # Executável de exemplo (Windows)
```

## 📄 Formato de entrada esperado

O programa espera um arquivo `TJDFT_filtrado.csv` na raiz do projeto, com 27 colunas separadas por `;`, incluindo campos como `id_processo`, `dt_recebimento`, `dt_resolvido`, flags temáticas e dados numéricos usados no cálculo da Meta 01 (`cnm1`, `julgadom1`, `desm1`, `susm1`, entre outros).

## 🚀 Como compilar e executar

Certifique-se de ter um compilador C instalado (GCC, por exemplo) e o arquivo `TJDFT_filtrado.csv` na mesma pasta do executável.

```bash
gcc main.c TJDF.c -o tjdf
./tjdf
```

No Windows, também é possível gerar o executável com:

```bash
gcc main.c TJDF.c -o tjdf.exe
tjdf.exe
```

Ao final da execução, o programa exibe no terminal um resumo com a quantidade de processos carregados, os dados do processo de exemplo, as contagens por flag temática e o percentual de cumprimento da Meta 01, além de gerar o arquivo `filtrado.csv` com os processos já julgados.

## 📄 Licença

Projeto de caráter acadêmico/demonstrativo.
