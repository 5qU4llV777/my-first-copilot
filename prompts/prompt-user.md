# Plano — Endpoint GET /users

### ✅ Objetivo
Expor um endpoint `GET /users` que retorne a lista de usuários cadastrados no banco, em formato JSON.

---

### 🧭 Contexto e Assunções
* Stack: Node.js + TypeScript, Express, Postgres, Jest, ESLint/Prettier.  
* Assumo que já existe conexão com Postgres configurada.  
* Assumo que há uma tabela `users` com colunas mínimas (`id`, `name`, `email`).  
* Preciso confirmar: se o retorno deve incluir todos os campos ou apenas alguns (ex.: ocultar senha).

---

### 📦 Escopo
* Inclui: rota `GET /users`, integração com DB, resposta JSON, testes básicos.  
* Não inclui: paginação, filtros avançados, autenticação (a menos que solicitado).  

---

### 🧩 Estratégia
* Criar rota no Express que consulta tabela `users`.  
* Usar camada de serviço para separar lógica de DB.  
* Validar resposta e tratar erros (ex.: conexão falhou).  
* Testar com Jest: sucesso e erro.  
* Alternativa: mockar DB em testes para isolamento.  

---

### 🗂️ Arquivos/áreas provavelmente afetadas
* `src/routes/users.ts` → definição da rota.  
* `src/services/userService.ts` → lógica de acesso ao DB.  
* `tests/users.test.ts` → testes da rota.  
* `src/db/connection.ts` → já existente, usado para query.  

---

### 🪜 Plano passo a passo
1. Criar serviço `userService` com função `getAllUsers(): Promise<User[]>`.  
2. Implementar rota `GET /users` chamando o serviço.  
3. Garantir tratamento de erro → resposta 500 em caso de falha.  
4. Adicionar testes:  
   - retorno 200 com array de usuários;  
   - retorno 500 em erro simulado.  
5. Rodar lint e formatar.  
6. Validar manualmente via `curl` ou browser.  

---

### 🧪 Testes e validação
* Teste unitário do serviço com mock de DB.  
* Teste de integração da rota com `supertest`.  
* Edge cases:  
  - tabela vazia → retornar `[]`;  
  - erro de conexão → retornar 500.  

---

### ⚠️ Riscos e mitigação
* **Risco:** retorno de dados sensíveis (senha).  
  * Mitigação: selecionar apenas colunas seguras (`id`, `name`, `email`).  
* **Risco:** performance em tabelas grandes.  
  * Mitigação: futura paginação.  
* **Risco:** compatibilidade Node/TS.  
  * Mitigação: confirmar versão e ESM vs CommonJS.  

---

### ❓ Perguntas
1. O endpoint deve ser público ou exigir autenticação?  
2. Quais campos de usuário devem ser expostos (id, name, email, outros)?  
3. Precisa de paginação já nesta versão?  

---

### ▶️ Próximo passo
Confirme os pontos acima. Depois disso, posso gerar o patch completo com código para `GET /users`.
