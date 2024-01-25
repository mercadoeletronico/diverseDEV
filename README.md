  <img src="me.svg" width="200" alt="ME">

# DiverseDEV

Bem-vindo(a) ao nosso desafio de conclusão !!!. :grin:

Essa etapa do curso será muito importante para que vocês dominem todos os conceitos de desenvolvimento adquiridos até aqui! Por isso, separamos dois casos de uso que fazem parte do nosso dia-a-dia e que os desafiarão a trabalharem em equipe.

---
## :zap: Desafio nº 1 - Inteligencia Artificial
No cenario empresarial, uma das tarefas que mais causam contratempos é o processo de lançamento de notas fiscais e cupons para reembolso. Muitas pessoas encontram dificuldades em preencher de forma correta resultando em uma série de problemas, tanto para os colaboradores quanto para a equipe financeira da empresa, consumindo um tempo valioso de todos.

### :clipboard: Detalhe técnico
Para resolver esse desafio gostariamos de utilizar o processamento de imagem para preenchermos os dados da despesa a partir do comprovante.

Para extrairmos essas informacao da despesa atraves de uma imagem iremos utilizar a API de Imagem do ChatGPT-4 que sera disponibilizada para voces.

### :rocket: Proposta de solução

* Criar uma API de OCR para o lancamento de despesas atraves de uma imagem de comprovante.
* Essa API devera enviar a imagem para o ChatGPT-4 e realizar alguns prompts para extrair as informacoes necessarias para o preenchimento.

* O primeiro passo seria validar o comprovante
    ``prompt: essa imagem e algum tipo de comprovante do tipo cupom fiscal ou nota fiscal? responda com SIM ou NAO``
  Caso a comprovante seja invalido devemos retornar a seguinte informacao.
  
  ```
  HTTP/1.1 400 Bad Request
  {
    "message": "Comprovante Invalido"
  }
  ```
* Em seguida vamos extrair as informacoes da despesa
  * Categoria da despesa
    ``prompt: que categoria de despesa é essa, entre: hospedagem, transporte, viagem, alimentação ou Outros.``   
  * Valor total da despesa
    ``prompt: qual o valor dessa despesa``
  * Descricao da despesa
    ``prompt: descreva sobre a despesa``

* Apos extrair todas as informacoes, devemos gravar em um banco de dados qualquer a despesa na seguinte estrutura de exemplo
  ```
  {
    "Total": 99.00
    "Categoria": "HOSPEDAGEM",
    "Descricao": "Descricao do comprovante",
    "Status": "SUBMETIDO"
  }
* Criar endpoint de consulta de despesas para que o Financeiro consiga visualizar todas as notas SUBMETIDO
* Criar endpoint para que o Financeiro consiga mudar o status da DESPESA para PAGA

---

## :zap: Desafio nº 2 - Motor de Aprovação
Seguindo no contexto de reembolso, uma outra parte crucial do controle de pagamento de reembolsos e o seu processo de aprovacao.
Essa etapa muitas vezes se revela trabalhosa pois demanda que o departamento financeiro envie manualmente esse documento para o gestor que em muitos casos essa informacao nao esta clara e pode impactar negativamente na eficiência operacional.

### :clipboard: Detalhe técnico
Para resolvermos esse problema precisamos criar um motor de aprovacao.
A ideia geral e que ao criarmos o documento de reembolso, descrito no desafio anterior seja executado uma rotina que determine se devemos APROVAR ou RECUSAR automaticamente.
Com isso podemos aplicar regras que agilizariam em muito o nosso processo.
Essa rotina devera alterar o status do documento para que esteja visivel para o departamento financeiro.

Caso nenhuma regra seja atendida, o financeiro devera manualmente APROVAR ou RECUSAR.
e o status devera ser "EM APROVACAO"

### :rocket: Proposta de solução
* Criar a API para criacao do documento de Reembolso.
  * Quando o documento for criado, devemos executar o motor de aprovacao.
  Segue abaixo a estrutura de tabela de Decisao. 

   | Valor do Reembolso| Categortia            | Acao    |
   |-|-|-|
   | Até R$100	       | Todas as categorias   | Aprovar
   | 101 - 500	       | Alimentação           | Aprovar | 
   | 101 - 500		     | Transporte            | Aprovar |
   | Acima de R$1.000	 | Todas as categorias	 | Recusar |
  
  Lembrando que ela pode sofrer alteracoes para adequacao do processo da empresa.
  Esperamos que essa estrutura deva ser mantida em um banco de dados

* Criar API para APROVAR o documento.
  * Para a aprovacao manual para ser utilizado pelo financeiro
* Criar API para RECUSAR o documento.
  * Para a recusa manual para ser utilizado pelo financeiro
* Criar API para que o financeiro possa listar os documentos por status
  * Sera util para que consigam verificar quais documentos necessitam de aprocacao manual.
---

### Enjoy!