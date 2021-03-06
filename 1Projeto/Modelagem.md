# Modelagem de dados para programadores

É muito importante saber como modelar os dados de bancos de dados, para deixar seu aplicativo mais eficiente e seguro.

## Convenção de nomes:
Para compatibilizar para os grandes frameworks
- Bancos, tabelas e campos - tuto em minúsculas e palavras compostas separadas por sublinhado
- Tabelas - no plural
- campos relacionados - nome da tabela no singular mais id: group_id (sempre not null e do mesmo tipo que a PK da tabela primária)

## Modelagem
- Banco de dados
- Esquemas
- Tabelas normalizadas
- Campos
- Tipos de dados
- Tamanho dos campos
- Constraints:
    - PK
    - FK
    - unique
    - not null
    - null
    - enum

## Relacionamentos:
    - Um para vários
    - Um para um
    - Vários para vários

## Análise de requisitos
Essa fase é a que se procura entender a regra do negócio, ouvindo o cliente e os futuros usuários do sistema, para que se possa compreender quais são suas necessidades. 

