# Banco de dado Relacionais e nâo Relacionais
![imagem](https://flowti.com.br/storage/blog/1318532023022463f8b93d47e36.png)
___
## Banco de dados Relacional
- O Banco de dados relacional ou **SGBD Relacional (Sistema de gerenciamento de banco de dados relacional)** é um mecanismo que armazena e organiza pontos de dados, a fim de proporcionar acesso rápido, flexível e eficiente, sendo uma das formas de armazenamento mais comuns atualmente, sendo usado principalmente em cenários que exigem uma estrutura organizada e consistente. O mecanismo funciona como uma coletânea de dados, que são armazenados em uma tabela que possui **colunas e linhas**, lembrando muito uma estrutura de tabela de Excel. Cada tabela representa uma **entidade ou relação do mundo real**. As linhas representam registros individuais nessa entidade, e as colunas representam os atributos ou características dos registros. A principal característica do banco relacional é a capacidade de estabelecer relacionamentos entre tabelas por meio de chaves primárias e estrangeiras. Isso permite que os dados fiquem associados e que, futuramente, **sejam consultados de maneira eficiente, garantindo a integridade relacional.**
  
### Exemplo:

- As empresas de comércio eletrônico usam bancos de dados relacionais para gerenciar e **armazenar informações sobre seu catálogo de produtos** (por exemplo, nome do produto, descrição, imagens, preço e estoque disponível). Manter os dados do catálogo precisos e atualizados é fundamental para garantir que os clientes tenham acesso às ofertas de produtos mais recentes e manter os níveis de estoque. Os bancos de dados relacionais permitem gerenciar diversos atributos, categorias e níveis de estoque de produtos, ao mesmo tempo que permitem a **recuperação eficiente de informações do produto durante a navegação do cliente.**
 
 ![Imagem](https://ascenty.com/wp-content/uploads/2024/12/3721407_Ascenty_Artigo_12_Blog-_1_-_1_-1920x1000-c-default.webp)
____
## Banco de dados Não Relacional 

- O banco de dados não relacional é um banco de dados que **possibilita a flexibilidade na hora de armazenar os dados**, já que não se limita a tabelas com linhas e colunas, como o banco de dados relacional. Esse tipo de banco de dados usa um modelo de armazenamento otimizado, que é adaptável para o requisito específico de cada dado, por exemplo: possibilita que os dados sejam armazenados como **chave/valor simples**; documento no formato **JSON (JavaScript Object Notation)** ou até mesmo em forma de gráfico, composto de bordas e vértices. Esse modelo, também conhecido como **NoSQL**, surgiu como uma solução para casos em que há uma quantidade elevada de dados para armazenar, fator que torna complexa a estruturação em tabelas. E também permite maior flexibilidade, escalabilidade e velocidade ao armazenar e acessar dados não estruturados, já que não tem necessidade de que as databases sejam parecidas entre si. 

### Exemplo: 

- Um exemplo de uso de banco de dados não relacional é em redes sociais como o Instagram. Essas plataformas lidam com grandes volumes de dados variados, como postagens com **textos, imagens, vídeos, curtidas e comentários**. Como essas informações têm estruturas flexíveis e mudam com frequência, bancos não relacionais como o MongoDB são mais adequados do que os relacionais. Eles permitem armazenar tudo em um único documento, oferecendo **rapidez, flexibilidade e alta escalabilidade**, o que garante desempenho mesmo com milhões de usuários acessando ao mesmo tempo.

![Imagem](https://4linux.com.br/wp-content/uploads/2021/07/o-que-e-banco-de-dados-nosql-100.jpg)

___
## O que é Normalização? 

- A normalização de banco de dados refere-se à **organização de dados em tabelas para facilitar a navegação e garantir que os dados permaneçam precisos e consistentes.** Por meio desse processo, administradores de banco de dados , engenheiros de dados e arquitetos de dados podem modelar e projetar uma estrutura para armazenar os dados de um aplicativo de forma que a camada de banco de dados do aplicativo funcione com a **máxima eficiência.**
  
### Qual seu objetivo? 

#### A normalização de banco de dados tem como principais objetivos:

- Eliminar a redundância de dados **(evitar a repetição de informações)**
- Garantir a integridade referencial **(garantir que as informações relacionadas sejam consistentes e válidas)**
- Facilitar a manutenção e consulta do banco de dados, pois um banco de dados normalizado é mais fácil de manter, já que as alterações em um local não afetam outras partes do sistema, além de facilitar a adição de **novas funcionalidades ou a correção de erros.**
- Permitir que o sistema encontre informações de forma mais eficiente, especialmente quando o banco de dados cresce e se torna mais complexo. 
- Criar uma estrutura de dados **lógica e consistente.**
  
 ![imagem](https://blog.ebaconline.com.br/blog/wp-content/uploads/2023/05/image3-11.jpg)

## Exemplo de Tabela Não Normalizada

| Pedido_ID | Cliente_Nome | Cliente_Endereço     | Produto_ID | Produto_Nome | Quantidade | Preço_Total |
|-----------|---------------|-----------------------|-------------|----------------|-------------|--------------|
| 1         | Carol         | Rua Francisco, 123    | 10          | Borracha       | 2           | 4,00         |
| 2         | Murilo        | Rua Parque, 321       | 11          | Apontador      | 2           | 10,00        |


## 1ª Forma Normal(1FN)

A 1ª Forma Normal tem como principal objetivo **garantir que todos os dados estejam organizados em campos atômicos, ou seja, cada campo deve conter apenas um valor por vez, sem listas, repetições ou agrupamentos.** 

## 2ª Forma Normal (2FN)
Na 2ª Forma devemos eliminar **dependências parciais**, ou seja, casos em que **os campos não dependem da chave primária composta completa**, mas apenas de parte dela. Por exemplo, o nome e endereço do cliente dependem apenas do **Cliente_ID, ou do Pedido_ID**, que está ligado ao cliente), e o nome do produto depende só do **Produto_ID.** Para arrumar isso, dividi a tabela original em três tabelas separadas: **uma para os clientes, uma para os produtos e uma para os pedidos, contendo apenas as informações necessárias.**

## Resultado: 

### Tabela do Cliente:

| ID do Cliente | Nome   | Endereço          |
|---------------|--------|----------------------|
| 1             | Carol  | Rua Francisco, 123   |
| 2             | Murilo | Rua Parque, 321      |

### Tabela do Produto

| Produto_ID | Nome do Produto | Preço Unitário |
|------------|------------------|----------------|
| 10         | Borracha         | 2,00           |
| 11         | Apontador        | 5,00           |

### Tabela dos Pedidos

| Pedido_ID | ID do Cliente | Produto_ID | Quantidade |
|-----------|----------------|------------|------------|
| 1         | 1              | 10         | 2          |
| 2         | 2              | 11         | 2          |

### 3ª Forma Normal
- A 3ª Forma Normal tem como foco remover **dependências transitivas**, que ocorrem quando um campo depende de outro campo que não é a chave primária, mas sim de **outro campo que também depende da chave**. Por exemplo, o campo **Preço Total** depende de **Quantidade e de Preço Unitário**, que depende do Produto_ID. Então, **Preço_Total** é uma dependência transitiva e deve ser eliminado da tabela, já que pode ser calculado a partir das outras informações que já estão expostas. Além disso, na tabela de clientes, dividi o endereço em duas partes: **Rua e Número.**

## Resultado:
  
### - Tabela do Cliente
| ID do Cliente | Nome   | Endereço         | Número de Endereço |
|---------------|--------|------------------|---------------------|
| 1             | Carol  | Rua Francisco    | 123                 |
| 2             | Murilo | Rua Parque 321   | 321                 |

### - Tabela do Produto
| Produto_ID | Nome do Produto | Preço Unitário |
|------------|------------------|----------------|
| 10         | Borracha         | 2,00           |
| 11         | Apontador        | 5,00           |

### - Tabela dos Pedidos

| Pedido_ID | ID do Cliente | Produto_ID | Quantidade |
|-----------|----------------|-------------|-------------|
| 1         | 1              | 10          | 2           |
| 2         | 2              | 11          | 2           |

___

# Estrutura não relacional;
```
[
  {
    "cliente_id": 1,
    "nome": "Carol",
    "endereco": {
      "rua": "Rua Francisco",
      "numero": 123
    },
    "pedidos": [
      {
        "pedido_id": 1,
        "produto": {
          "produto_id": 10,
          "nome": "Borracha",
          "preco_unitario": 2.00
        },
        "quantidade": 2
      }
    ]
  },
  {
    "cliente_id": 2,
    "nome": "Murilo",
    "endereco": {
      "rua": "Rua Parque 321",
      "numero": 321
    },
    "pedidos": [
      {
        "pedido_id": 2,
        "produto": {
          "produto_id": 11,
          "nome": "Apontador",
          "preco_unitario": 5.00
        },
        "quantidade": 2
      }
    ]
  }
]
```
## Explicação;
No modelo não relacional, como o **JSON**, os dados são organizados de forma mais flexível e próxima da realidade da aplicação, agrupando informações relacionadas em um único documento. Isso faz com que não haja necessidade de **normalização**, pois **não é preciso dividir os dados em várias tabelas para evitar repetições**. Em vez disso, por exemplo, os pedidos de um cliente podem ser armazenados diretamente dentro do próprio documento do cliente. Isso reduz a dificuldade na hora de consultar os dados, já que tudo o que se precisa está em um só lugar, sem precisar fazer junções entre tabelas. Essa estrutura se adequa melhor a aplicações que priorizam **velocidade de leitura e flexibilidade,** como sistemas da web ou redes sociais, onde os dados mudam com frequência e a estrutura pode variar bastante.

