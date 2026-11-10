# TID-KMeans — Clusterização dinâmica em fluxos de dados

Códigos associados ao Trabalho de Conclusão de Curso **Clusterização Dinâmica em Fluxos de Dados**, de **Isabela Borges Farina**, sob orientação de **Daiane Aparecida Zuanetti**, Departamento de Estatística — Universidade Federal de São Carlos (UFSCar), 2026.

## Organização

| Arquivo | Conteúdo |
|---|---|
| `01_simulacoes.ipynb` | Duas situações simuladas, busca em grade, avaliações por lote, 30 replicações e verificação online/offline. |
| `02_occupancy_experimentos.ipynb` | Pipeline completo de dados reais, calibração, comparação TID-KMeans/DenStream/k-means, testes e diagnósticos online/offline. |
| `03_occupancy_analise_exploratoria.ipynb` | Análise descritiva independente da base real, incluindo correlação calculada somente na base inicial. |
| `requirements.txt` | Principais dependências Python. |

Os notebooks preservam a lógica do arquivo original. Foram retiradas as saídas antigas das células e o código foi redistribuído para facilitar a navegação; **não foram refeitos nem validados numericamente todos os experimentos**.

## Como executar

1. Instale as dependências: `pip install -r requirements.txt`.
2. Abra o notebook desejado no Jupyter Notebook, JupyterLab ou Google Colab.
3. Execute as células em ordem. `01_simulacoes.ipynb` não exige arquivos externos.
4. Para os dois notebooks da Occupancy, obtenha a base **Occupancy Detection** de sua fonte original e disponibilize estes três arquivos no diretório de execução:
   - `datatest.txt` (inicialização)
   - `datatraining.txt` (calibração)
   - `datatest2.txt` (teste)

   Se estiver no Colab, envie os três arquivos para o ambiente ou adapte os caminhos `ARQ_X0`, `ARQ_CAL` e `ARQ_TESTE`.
5. `02_occupancy_experimentos.ipynb` deve ser executado integralmente; a seção online/offline usa resultados de células anteriores.

## Cuidados metodológicos

- Simulações: a padronização é ajustada às 300 observações iniciais de cada situação e aplicada aos lotes posteriores.
- Occupancy: o ajuste do padronizador usa apenas os dados iniciais. A seleção dos hiperparâmetros utiliza a calibração; a avaliação final utiliza o teste.
- O notebook original inclui uma função auxiliar `config_den()` que transforma uma grade auxiliar em valores de `decaying_factor` do River. Os valores efetivos aplicados ao DenStream devem ser consultados no código ou na saída da configuração antes de reportá-los no texto do TCC.
- No DenStream, o número de grupos observados ao longo do teste não é necessariamente igual ao número de micro-clusters potenciais ativos no último lote.

## Repositório

Este pacote está pronto para ser carregado em um repositório GitHub. Recomenda-se manter o link do repositório atualizado no texto do TCC e verificar se os dados podem ser redistribuídos antes de adicioná-los ao GitHub.
