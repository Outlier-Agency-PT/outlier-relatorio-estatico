# outlier-relatorio-estatico

Relatório de acompanhamento de lançamento gerado como página HTML estática, sem framework nem build step. Os dados são actualizados directamente no `index.html` e publicados via Vercel.

## Estrutura

```
index.html   — página única com todos os dados embutidos no objecto DATA (JavaScript)
vercel.json  — headers de no-cache para garantir que cada deploy é imediatamente visível
```

## Como actualizar os dados

1. Abrir `index.html` no editor.
2. Localizar o objecto `const DATA = { … }` no início do bloco `<script>`.
3. Editar os campos pretendidos (ver secção *Campos principais* abaixo).
4. Guardar, fazer commit e push para `main` — o Vercel faz deploy automático em segundos.

> Os campos marcados com `null` ou `available: false` fazem com que a secção correspondente mostre estado pendente, não zero. Não substituir por `0` a menos que o valor real seja efectivamente zero.

## Campos principais em DATA

| Caminho | O que é |
|---|---|
| `meta.updatedAt` | Timestamp da última exportação do Meta Ads (ISO 8601) |
| `meta.account.*` | Totais acumulados da conta (spend, leads, CPL, etc.) |
| `meta.daily[]` | Array com um objecto por dia de campanha |
| `meta.audiences[]` | Totais por ad set (Sinais / Aberto) |
| `meta.creatives[]` | Totais por criativo |
| `manual.sales.*` | Dados de vendas/faturação (Hotmart) — preencher quando disponível |
| `manual.whatsapp.*` | Membros no grupo WhatsApp (Sendflow) — preencher quando disponível |
| `analysis.leituraPeriodo` | Array de strings com a leitura narrativa do período |

## Deploy

O repositório está ligado ao Vercel. Qualquer push para `main` despoleta um deploy automático. O `vercel.json` garante que os browsers não servem versão em cache.

## Requisitos

Nenhum. É HTML puro — abre directamente no browser sem servidor.
