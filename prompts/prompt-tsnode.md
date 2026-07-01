# Exemplo de Resposta — Modo ASK

1. **Resumo**  
O `ts-node` não roda com `import` porque, por padrão, ele espera CommonJS. O suporte a ESM precisa de configuração extra.

2. **Explicação curta**  
O TypeScript compila para CommonJS por default. Se você usa `import/export`, precisa habilitar `"module": "ESNext"` no `tsconfig.json` e rodar com a flag `--esm` ou usar `ts-node-esm`.

3. **Como confirmar**  
- Verifique seu `tsconfig.json` → campo `"module"`.  
- Rode `ts-node --esm index.ts` e veja se o erro persiste.  
- Se aparecer “Cannot use import statement outside a module”, é falta de configuração ESM.

4. **Opções**  
- [Ajustar tsconfig](ca://s?q=Como_configurar_tsconfig_para_ESM): `"module": "ESNext"`, `"target": "ES2020"`.  
- [Rodar com flag](ca://s?q=Rodar_ts-node_com_flag_esm): `ts-node --esm`.  
- [Usar loader oficial](ca://s?q=Usar_ts-node_loader_no_Node): `node --loader ts-node/esm index.ts`.

5. **Snippet opcional**  
Se você quiser, eu te dou um patch de `tsconfig.json` já pronto para ESM.
