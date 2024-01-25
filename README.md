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
  * Tipo da despesa
    ``prompt: que tipo de despesa é essa, entre: hospedagem, transporte, viagem, alimentação ou Outros.``   
  * Valor total da despesa
    ``prompt: qual o valor dessa despesa``
  * Descricao da despesa
    ``prompt: descreva sobre a despesa``

* Apos extrair todas as informacoes, devemos gravar em um banco de dados qualquer a despesa na seguinte estrutura de exemplo
  ```
  {
    "Total": 99.00
    "Tipo": "HOSPEDAGEM",
    "Descricao": "Descricao do comprovante",
    "Status": "PENDENTE"
  }
* Criar endpoint de consulta de despesas para que o Financeiro consiga visualizar todas as notas PENDENTES
* Criar endpoint para que o Financeiro consiga mudar o status da DESPESA para PAGA

---

## :zap: Desafio nº 2 - Motor de Encaminhamento
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen boo

### :clipboard: Detalhe técnico
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen boo

### :rocket: Proposta de solução
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen boo

---

### Enjoy!