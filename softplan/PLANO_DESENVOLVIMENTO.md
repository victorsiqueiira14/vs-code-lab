# Plano de Desenvolvimento — 90 dias

Objetivo: entregar mais e com mais visibilidade em **leitura de documentos**, **performance** e
**banco de dados**. Ajuste depois de preencher o perfil no `SUPER_PROMPT.md`.

## Dias 1–30 — Fundamentos que mais dão retorno

**Banco de dados / performance**
- [ ] Ler um **plano de execução** com segurança: scan vs seek, key lookup, sort, hash/nested loop, custo estimado vs real.
- [ ] **Índices**: clusterizado vs não clusterizado, índice composto (ordem das colunas), índice de cobertura (`INCLUDE`), custo de índice em escrita.
- [ ] **SARGability**: por que `WHERE YEAR(data) = 2026` ou `WHERE CAST(coluna...)` matam o índice e como reescrever.
- [ ] Medir antes de otimizar: `SET STATISTICS IO, TIME ON` (SQL Server) / `EXPLAIN ANALYZE` (PostgreSQL) / `EXPLAIN PLAN` + `DBMS_XPLAN` (Oracle).
- [ ] Prática: pegar 1 query lenta real por semana (anonimizada), otimizar com `/sql` e registrar o ganho (ex.: 12s → 0,8s).

**Leitura de documentos**
- [ ] Método em 3 passadas: (1) estrutura e objetivo, (2) regras e requisitos, (3) lacunas e perguntas.
- [ ] Usar `/doc` em todo documento importante e guardar as perguntas geradas.

**Hábito com IA**
- [ ] Usar o super prompt diariamente em pelo menos 1 tarefa real.
- [ ] Toda sexta: `/carreira` com a lista do que fez na semana.

## Dias 31–60 — Profundidade

- [ ] **Transações e concorrência**: níveis de isolamento, locks, bloqueios, deadlocks — como identificar e evitar.
- [ ] **Estatísticas** e **parameter sniffing**: por que a mesma query é rápida às vezes e lenta outras.
- [ ] **Monitoramento**: queries mais caras do banco (DMVs / `pg_stat_statements` / AWR), esperas (waits).
- [ ] **Modelagem**: normalização, chaves, tipos de dados corretos, impacto de tipos errados em performance.
- [ ] Criar um **"livro de receitas"** pessoal: consultas de diagnóstico que você usa sempre (sem dados de cliente).

## Dias 61–90 — Visibilidade e senioridade

- [ ] Escolher **1 problema recorrente** do time (query lenta, chamado repetido, processo manual) e resolvê-lo de ponta a ponta.
- [ ] Documentar a solução (problema → causa → solução → ganho medido) e apresentar ao time/liderança (`/comunicar`).
- [ ] Propor 1 melhoria de processo usando IA (ex.: modelo padrão de análise de chamado).
- [ ] Revisar o plano com `/carreira` e definir os próximos 90 dias.

## Como medir a evolução

| Indicador | Como medir |
|---|---|
| Ganho de performance | Tempo/leituras antes vs depois de cada query otimizada |
| Qualidade de análise | Retrabalho e perguntas devolvidas pelo time |
| Velocidade | Tempo médio para entender um documento / resolver um chamado |
| Visibilidade | Soluções documentadas e apresentadas |

## Certificações e estudo (opcionais, conforme o banco usado)

- SQL Server: trilhas Microsoft Learn de administração/performance (DP-300).
- PostgreSQL: documentação oficial (capítulos "Performance Tips" e "Indexes").
- Oracle: SQL Tuning Guide.
- Livro de referência geral: *SQL Performance Explained* (Markus Winand) — também em use-the-index-luke.com.
