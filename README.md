
# Olá, mundo!!
Olá! Eu sou Luciano do Valle, analista de processos, e estou em transição de carreira para a área de dados.

 Hoje já  desenvolvo pequenos projetos tm Pyhton e R, visando realizar o processo de ETL(Extraction, Transformation, Load) para alimentar painéis do Power BI e Tableau
<br>
<img align="right" src="https://github.com/lduvalle/imagens/blob/main/octocat-1696861909375.png?raw=true" width="300"/> 
<br>
Tenho como principais hobbies:
<br>

- Correr
- Comer, não sei se é um hobbie, mas faço por diversão
- Viajar
- Ir à Praia
- Jogar Baldur`s Gate
- E outras coisas mais...
<br><br><br>

---

Este repositório representa a entrega do projeto: Processando e Transformando Dados com Power BI
<br><br><br>

[<img align="center" src="https://github.com/lduvalle/dio-desafio-power-bi-azure/blob/main/01.%20Imagens/Screenshot_276.png?raw=true" width="800"/>](https://github.com/lduvalle/dio-desafio-power-bi-azure/blob/main/01.%20Imagens/Screenshot_276.png?raw=true)

<br><br><br>
O desafio consistia em:
1.	Criação de uma instância na Azure para MySQL
<br><br>
[<img align="center" src="https://github.com/lduvalle/dio-desafio-power-bi-azure/blob/main/01.%20Imagens/Screenshot_281.png?raw=true" width="400"/>](https://github.com/lduvalle/dio-desafio-power-bi-azure/blob/main/01.%20Imagens/Screenshot_281.png?raw=true)
<br><br>
2.	Criar o Banco de dados com base disponível no github
<br><br>
[<img align="center" src="https://github.com/lduvalle/dio-desafio-power-bi-azure/blob/main/01.%20Imagens/Screenshot_282.png?raw=true" width="400"/>](https://github.com/lduvalle/dio-desafio-power-bi-azure/blob/main/01.%20Imagens/Screenshot_282.png?raw=true)
<br><br>
3.	Integração do Power BI com MySQL no Azure 
<br><br>
[<img align="center" src="https://github.com/lduvalle/dio-desafio-power-bi-azure/blob/main/01.%20Imagens/Screenshot_283.png?raw=true" width="400"/>](https://github.com/lduvalle/dio-desafio-power-bi-azure/blob/main/01.%20Imagens/Screenshot_283.png?raw=true)
<br><br>
4.	Verificar problemas na base a fim de realizar a transformação dos dados



<br>
<br>
Diretrizes para transformação dos dados

1.	Verifique os cabeçalhos e tipos de dados

        	Campo Essn da tabela works_on modificado para tipo numérico.

2.	Modifique os valores monetários para o tipo double preciso

        	Modificado para valor monetário. O Power BI não possui tipo double preciso.

3.	Verifique a existência dos nulos e analise a remoção

        	Não houve necessidade de exclusão de nulos

4.	Os employees com nulos em Super_ssn podem ser os gerentes. Verifique se há algum colaborador sem gerente

        	James Borg é o único colaborador que não possui gerente

5.	Verifique se há algum departamento sem gerente

        	Não há departamentos sem gerentes

6.	Se houver departamento sem gerente, suponha que você possui os dados e preencha as lacunas

        	Não há departamentos sem gerentes. 
        	333445555 é gerente do Research. 
        	987654321 é gerente do Administration. 
        	888665555 é gerente do Headquarters

7.	Verifique o número de horas dos projetos

        	Há uma coluna de horas no tipo decimal.

8.	Separar colunas complexas

        	Coluna Adress da tabela Employee separada em: Number, Street, City e State

9.	Mesclar consultas employee e departament para criar uma tabela employee com o nome dos departamentos associados aos colaboradores. A mescla terá como base a tabela employee. Fique atento, essa informação influencia no tipo de junção

        	Mescla realizada no Power Query adicionando a consulta “azure_company employee X Departament
10.	Neste processo elimine as colunas desnecessárias. 

        	Não há informações sobre o que é necessário ou não. 
            Não há delimitação de escopo. Para atender à solicitação da questão 9, 
            apenas importei o nome do departamento, reduzindo a quantidade de etapas aplicadas no Power BI.

11.	Realize a junção dos colaboradores e respectivos nomes dos gerentes . Isso pode ser feito com consulta SQL ou pela mescla de tabelas com Power BI. Caso utilize SQL, especifique no README a query utilizada no processo.

        	Consultas mescladas no Power Query gerando a 
            “azure_company Employee X Manager Name”.
         O nome do gerente foi adicionado ao lado da coluna Super_ssn

12.	Mescle as colunas de Nome e Sobrenome para ter apenas uma coluna definindo os nomes dos colaboradores

        	Realizado na consulta “azure_company Employee X Manager Name”, 
            tanto com o nome do funcionário, quanto com o nome do gerente.

13.	Mescle os nomes de departamentos e localização. Isso fará que cada combinação departamento-local seja único. Isso irá auxiliar na criação do modelo estrela em um módulo futuro.

        	Realizado na consulta “azure_company departament”. 
            Existe um erro nesta etapa, pois a tabela consta 3 localidades para o mesmo setor.

14.	Explique por que, neste caso supracitado, podemos apenas utilizar o mesclar e não o atribuir. 

        	A mescla dos setores funciona como um Inner Join, 
            utilizando o campo Dnumber como chaves. 
            É a única maneira de responder a questão supracitada (13).

15.	Agrupe os dados a fim de saber quantos colaboradores existem por gerente

        	Realizado na consulta “azure_company Employee X Manager Name count”

16.	Elimine as colunas desnecessárias, que não serão usadas no relatório, de cada tabela

        	Esta é uma etapa com escopo indefinido. Não foi passado o tipo de análise que será executado.
            Eliminar colunas cria etapas aplicadas no Power Query, 
            caso seja necessário utilizar novamente estes dados, 
            e houver uma ação posterior, algumas métricas e relacionamentos 
            efetuados após a exclusão podem ficar comprometidas. 
            Para eliminar as colunas, é necessária a definição do *ESCOPO DE PROJETO*. 
            Foi realizada a ocultação de campos e tabelas desnecessárias.



<br>
<br>
<br>
Os arquivos utilizados na resolução do desafio está no repositório. Publiquei o relatório, que pode ser acessado no link abaixo
<br> <br>

[![PowerBI](https://img.shields.io/badge/PowerBI-Desafio_DIO-%23F2C811?style=for-the-badge&logo=PowerBI&logoColor=white)](https://app.powerbi.com/view?r=eyJrIjoiZDlkMGFiMjktY2JlNy00YzFmLTgwNTMtODg0ZDc2ZDcxZjA5IiwidCI6ImMwZmQwMGVhLThmNzQtNDBhZC04ZjMyLWJlZjAyYzk4M2IwNyJ9)

<br>
<br>

---

## Ferramentas e Habilidades
### Dataviz
![PowerBI](https://img.shields.io/badge/PowerBI-%23F2C811?style=for-the-badge&logo=PowerBI&logoColor=black)
![Tableau](https://img.shields.io/badge/Tableau-E97627?style=for-the-badge&logo=tableau&logoColor=white)<br>
### Linguangens de Programação
![R](https://img.shields.io/badge/R-276DC3?style=for-the-badge&logo=R&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)

### Bancos de Dados
![SQL Lite](https://img.shields.io/badge/sqlite-003B57?style=for-the-badge&logo=sqlite)
![MySQL](https://img.shields.io/badge/mysql-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![MySQL](https://img.shields.io/badge/microsoftsqlserver-CC2927?style=for-the-badge&logo=microsoftsqlserver&logoColor=white)
![Mongo](https://img.shields.io/badge/mongodb-47A248?style=for-the-badge&logo=mongodb&logoColor=white)



# Contatos
Entre em contato em uma das redes sociais abaixo

[![Mongo](https://img.shields.io/badge/behance-1769FF?style=for-the-badge&logo=behance&logoColor=white)](https://www.behance.net/dovallebarbosa)
[![LinkedIn](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/luciano-do-valle-barbosa-33799b263/)
[![Instagram](https://img.shields.io/badge/instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://www.instagram.com/ldovalle/)
[![Spotify](https://img.shields.io/badge/spotify-1DB954?style=for-the-badge&logo=spotify&logoColor=white)](https://open.spotify.com/user/22rxsto4zfjdqqyfdhx27v3jq)