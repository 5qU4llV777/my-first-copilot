# Exemplo — Endpoint GET /health

## (A) Descobrir
Objetivo: Criar um endpoint de health check (`GET /health`) que retorne status da API.  
Restrições: Stack Node.js 20, Express, ESM, Jest, Postgres, Docker.  
Contexto: Endpoint deve responder rápido, sem dependência externa.  

---

## (P) Planejar
Arquivos afetados:
- `src/server.js` → adicionar rota `/health`
- `tests/health.test.js` → criar teste para validar resposta

Critérios de aceite:
- Resposta HTTP 200
- JSON `{ status: "ok" }`
- Teste automatizado passando

---

## (I) Implementar

### Arquivo: `src/server.js`
```js
import express from "express";

const app = express();

// Health check endpoint
app.get("/health", (req, res) => {
  res.status(200).json({ status: "ok" });
});

export default app;
