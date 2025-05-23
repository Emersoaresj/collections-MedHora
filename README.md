# Documentação de Testes de API - MedHora

## 1. Descrição dos Testes Manuais

Esta documentação descreve como realizar testes manuais para validar os endpoints da API MedHora utilizando as collections do Postman.

---

## **Agendamento**

### **1. Criar Agendamento (POST /consultas)**

- **Objetivo**: Verificar se o cadastro de um novo agendamento de consulta está funcionando corretamente.

- **Passos**:
  1. Selecione o método `POST` no Postman.
  2. Insira a URL do endpoint:  
     `{{url}}/consultas`
  3. No corpo da requisição, selecione o tipo `JSON` e insira os dados do agendamento:
     ```json
     {
       "nomePaciente": "Emerson S",
       "nomeMedico": "Dr. Carlos Pereira",
       "dataHoraConsulta": "2025-05-15T11:00",
       "motivoConsulta": "Consulta Cardiologista"
     }
     ```
  4. Clique em **Send**.
  5. **Validação**:
     - Verifique se a resposta retorna o status `201 Created` ou `200 OK`.
     - Certifique-se de que o corpo da resposta contém os dados do agendamento recém-criado.

### **2. Listar Consultas (GET /consultas)**

- **Objetivo**: Obter a lista completa de consultas/agendamentos cadastrados.

- **Passos**:
  1. Selecione o método `GET` no Postman.
  2. Insira a URL do endpoint:  
     `{{url}}/consultas`
  3. Clique em **Send**.
  4. **Validação**:
     - Verifique se o status da resposta é `200 OK`.
     - A resposta deve conter um array de objetos representando os agendamentos.

### **3. Buscar Consulta por ID (GET /consultas/{id})**

- **Objetivo**: Obter os detalhes de uma consulta específica pelo ID.

- **Passos**:
  1. Selecione o método `GET` no Postman.
  2. Insira a URL do endpoint substituindo `{id}` pelo ID da consulta:  
     `{{url}}/consultas/1`
  3. Clique em **Send**.
  4. **Validação**:
     - Verifique se o status da resposta é `200 OK`.
     - A resposta deve conter os detalhes da consulta solicitada.

### **4. Atualizar Consulta (PUT /consultas/{id})**

- **Objetivo**: Atualizar os dados de uma consulta existente.

- **Passos**:
  1. Selecione o método `PUT` no Postman.
  2. Insira a URL do endpoint substituindo `{id}` pelo ID da consulta que deseja atualizar:  
     `{{url}}/consultas/1`
  3. No corpo da requisição, selecione o tipo `JSON` e insira os dados atualizados da consulta:
     ```json
     {
       "nomePaciente": "Emerson Soares",
       "nomeMedico": "Dra. Ana Souza",
       "dataHoraConsulta": "2025-05-20T14:30",
       "motivoConsulta": "Consulta Clínica Geral"
     }
     ```
  4. Clique em **Send**.
  5. **Validação**:
     - Verifique se o status da resposta é `200 OK`.
     - Certifique-se que os dados retornados correspondem aos dados atualizados.

### **5. Deletar Consulta (DELETE /consultas/{id})**

- **Objetivo**: Excluir uma consulta pelo ID.

- **Passos**:
  1. Selecione o método `DELETE` no Postman.
  2. Insira a URL do endpoint substituindo `{id}` pelo ID da consulta que deseja excluir:  
     `{{url}}/consultas/1`
  3. Clique em **Send**.
  4. **Validação**:
     - Verifique se o status da resposta é `200 OK` ou `204 No Content`.
     - A resposta deve indicar que a consulta foi deletada com sucesso.

---

## **GraphQL - Agendamento**

## 1. Buscar Agendamento por ID

- **URL:** `{{url}}/graphql`  
- **Method:** POST  
- **Headers:**  
  - Content-Type: application/json  
- **Body (raw JSON):**
  ```json
  {
    "query": "query { agendamentoPorId(id: 11) { id dataHora descricao paciente medico } }"
  }

Descrição: Retorna os dados do agendamento com o ID especificado (neste exemplo, ID 11).

## 2. Buscar Agendamentos por Paciente

- **URL**: `{{url}}/graphql`

- **Method**: POST

- **Headers**:  
  - Content-Type: application/json

- **Body (raw JSON)**:
  ```json
  {
    "query": "query { agendamentos(nomePaciente: \"Maria Silva\", somenteFuturos: true) { id dataHora descricao paciente medico } }"
  }

Descrição: Retorna todos os agendamentos futuros para o paciente "Maria Silva".

---

## 3. Link para a Collection do Postman

Para testar a API, importe a collection do Postman usando o link abaixo:

[Link para a Collection do Postman MedHora](https://github.com/Emersoaresj/collections-MedHora/blob/main/MedHora.postman_collection.json)

---

## 4. Executando os Testes

### Importando a Collection no Postman:

- No Postman, clique em **Import** no canto superior esquerdo.
- Selecione **Link** e cole o link da collection acima.
- Clique em **Import** para adicionar a collection ao seu Postman.

### Executando as Requisições:

- Escolha o endpoint desejado na collection importada.
- Clique em **Send** para enviar a requisição e validar a resposta.

---

## 5. Conclusão

Os testes manuais descritos acima podem ser realizados utilizando o Postman para garantir que os endpoints da API MedHora estão funcionando corretamente.
