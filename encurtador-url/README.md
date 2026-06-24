# PROJETO ENCURTADOR DE URL´s

**Nível:** básico <br>
**Tema(s):**
 - APIs REST; 
 - Persistência (simples);
 - Redirecionamento HTTP
 - Rate limiting básico (simples);

## ETAPA 1: ENTENDIMENTO DO PROBLEMA

:book: **Resumo do problema** 

Uma pequena agência de marketing precisa de um encurtador de URLs para acompanhar cliques de campanhas locais. 
O produto inicial deve permitir criar links curtos, redirecionar de forma rápida e registrar contagens de cliques por dia. 
O sistema será usado por poucos clientes (dezenas) e tráfego moderado (centenas a poucos milhares de cliques/dia).

### REQUISITOS FUNCIONAIS

1. **Encurtamento de URL:** Dado uma URL, retornar uma **NOVA URL** como o valor mais curto - _seguindo os critérios definido nos requisitos não funcionais_. 

2. **Redirecionamento de URL:** Dado o acesso via URL curta (gerada pelo encurtador), redirecionar para a URL original do cadastro.
   
3. **Registrar Métrica de Acessos**: o sistema deve registrar os acessos nas URL´s porta data (ex.: total diário) e expor consulta simples (ex.: GET /api/v1/links/{short_url}/stats?from=YYYY-MM-DD&to=YYYY-MM-DD).
   
4. **(Opcional) Permitir expiração do link:** poderá ser informada uma data de validade para o funcionamento da URL curta que será gerada.

### REQUISITOS NÃo FUNCIONAIS

1. **Latência:** redirecionamento abaixo de 100 ms p95 dentro da mesma região;   
2. **Disponibilidade:** 99,5% mensal é suficiente para o MVP;   
3. **Consistência:** leitura do redirecionamento deve ser forte; métricas podem ser atualizadas de forma assíncrona (eventual);   
4. **Observabilidade:** logs de acesso, métricas de p95/p99 e contador de erros 5xx;   
5. **Segurança:** 
   - Evitar colisões de URL´s;
   - ~~Validar domínio de destino opcionalmente (lista de bloqueio);~~
   - ~~Limitar criação por chave de API.~~
6. **Custos:** Preferencialmenta usar componentes gerenciados/básicos de baixo custo (banco de dados de baixa latência, cache opcional).