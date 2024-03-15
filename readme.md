# Extração tabelas IPVA

Uma das minhas paixões são os carros, para quem gosta, assim como eu, passar horas em sites de classificados buscando o próximo modelo dos sonhos é um passatempo prazeroso. 

Mas antes de fechar o negócio, não se pode esquecer a razão e ir apenas pela emoção. Avaliar os custos além do valor de compra do veículo é muito importante.

E para ajudar nessa etapa veio a ideia de montar esse projeto de extração dos valores do IPVA, facilitando a consulta por modelo e ano de fabricação. 

## IPVA Minas Gerais

A cobrança do IPVA (Imposto sobre a Propriedade de Veículos Automotores) é realizada de forma diferente em cada estado, variando as regras e alíquotas. Inicialmente fiz a extração dos dados para o estado de Minas. 

As tabelas anuais são disponibilizadas em PDF no [Diário Eletrônico da Secretaria de Estado da Fazenda](http://diarioeletronico.fazenda.mg.gov.br/opendiariogeral/opencms/resultados-ipva/index.html). 

O código e o resultado da extração estão disponíveis no diretório `/MG`, o projeto foi desenvolvido na linguagem Python em um Notebook.

### Resultados
Foram considerados no código o IPVA dos anos de 2022, 2023 e 2024. Os dados extraídos foram exportados em dois arquivos CSV.

Para realizar análises os arquivos podem ser carregados por exemplo no Power BI. 

#### Modelos (modelos.csv)
É uma dimensão, com a união de todos os modelos distintos de veículos, informações complementares sobre a categoria e fabricante.

* <b>CodIPVA</b>: chave única que identifica o modelo
* <b>CATEGORIA</b>: categoria que se enquadra o veículo
* <b>FABRICANTE</b>: nome da fabricante
* <b>MODELO/VERSÃO</b>: nome do modelo e versão do veículo

#### IPVA (ipva.csv)
É uma tabela fato, onde foram concatenados o custo do IPVA por veículo, ano de referência da taxa e ano de fabricação. Ele pode ser associado ao arquivo de modelos através do <b>CodIPVA</b>.

* <b>CodIPVA</b>: chave única que identifica o modelo
* <b>AnoIPVA</b>: ano de cobrança do imposto
* <b>AnoVeículo</b>: ano de fabricação do veículo
* <b>AnoVeículo</b>: valor do IPVA

