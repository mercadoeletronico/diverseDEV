<img src="me.svg" width="200" alt="ME">

# DiverseDEV

Bem-vindo(a) ao nosso desafio de conclusão !!!. :grin:

Essa etapa do curso será muito importante para que vocês dominem todos os conceitos de desenvolvimento adquiridos até aqui! Por isso, separamos dois casos de uso que fazem parte do nosso dia a dia e que os desafiarão a trabalharem em equipe.

---
## :zap: Desafio 1 - Inteligência Artificial
No cenário empresarial, uma das tarefas que mais causam contratempos é o processo de lançamento de notas fiscais e cupons para reembolso. Muitas pessoas encontram dificuldades em preencher de forma correta, resultando em uma série de problemas, tanto para os colaboradores quanto para a equipe financeira da empresa, consumindo um tempo valioso de todos.

### :clipboard: Detalhe técnico
Para resolver esse desafio, gostaríamos de utilizar o processamento de imagem para preenchermos os dados da despesa a partir do comprovante.

Para extrairmos essas informações da despesa através de uma imagem, iremos utilizar a API de Imagem do ChatGPT-4 que será disponibilizada para vocês.

### :rocket: Proposta de solução

* Criar uma API de OCR para o lançamento de despesas através de uma imagem de comprovante.

* Essa API deverá enviar a imagem para o ChatGPT-4 e realizar alguns prompts para extrair as informações necessárias para o preenchimento.

* O primeiro passo seria validar o comprovante
    ``prompt: essa imagem e algum comprovante de comprovante fiscal? responda com SIM ou NAO``
  Caso o comprovante seja inválido, devemos retornar a seguinte informação:
  
  ```
  HTTP/1.1 400 Bad Request
  {
    "message": "Comprovante Inválido"
  }
  ```
* Em seguida, poderíamos extrair as informações da despesa.
  * Categoria da despesa
    ``prompt: que categoria de despesa é essa, entre: hospedagem, transporte, viagem, alimentação ou Outros.``   
  * Valor total da despesa
    ``prompt: qual o valor dessa despesa``
  * Descricao da despesa
    ``prompt: descreva sobre a despesa``

* Após extrair todas as informações, devemos gravar em um banco de dados qualquer a despesa na seguinte estrutura de exemplo:
  ```
  {
    "Total": 99.00
    "Categoria": "HOSPEDAGEM",
    "Descricao": "Descricao do comprovante",
    "Status": "SUBMETIDO"
  }
  ```
* Criar endpoint de consulta de despesas para que o Financeiro consiga visualizar todas as notas com status em SUBMETIDO.
* Criar endpoint para que o financeiro consiga mudar o status da despesa para PAGA.

---

## :zap: Desafio 2 - Motor de Aprovação
Seguindo no contexto de reembolso, outra parte crucial do controle de pagamento de reembolsos é o seu processo de aprovação.
Essa etapa muitas vezes se revela trabalhosa, pois demanda que o departamento financeiro envie manualmente esse documento para o gestor, que em muitos casos essa informação não está clara e pode impactar negativamente na eficiência operacional.

### :clipboard: Detalhe técnico
Para resolvermos esse problema, precisamos criar um motor de aprovação.
A ideia geral é que, ao criarmos o documento de reembolso, descrito no desafio anterior, seja executada uma rotina que determine se devemos APROVAR ou RECUSAR automaticamente.

Com isso, podemos aplicar regras que agilizariam muito o nosso processo.

Caso nenhuma regra seja atendida, o status deverá ser alterado para "EM APROVAÇÃO". 
Com isso, o financeiro deverá manualmente APROVAR ou RECUSAR essa despesa.

### :rocket: Proposta de solução
* Criar a API para criação do documento de Reembolso.
  * Quando o documento for criado, devemos executar o motor de aprovação.
  Esse processo deverá seguir uma tabela de decisão semelhante a essa.

   | Valor do Reembolso| Categoria            | Acao    |
   |-|-|-|
   | Até R$100	       | Todas as categorias   | Aprovar
   | 101 - 500	       | Alimentação           | Aprovar | 
   | 101 - 500		     | Transporte            | Aprovar |
   | Acima de R$1.000	 | Todas as categorias	 | Recusar |
  
  Vale lembrar que essas regras podem variar, e esperamos que essa estrutura esteja mantida em um banco de dados.

* Criar endpoint para que o financeiro possa listar os documentos por STATUS
* Criar endpoint para APROVAR o documento.
* Criar endpoint para RECUSAR o documento.

---

### Enjoy!
