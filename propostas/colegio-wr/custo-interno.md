# Custo Interno — Plataforma de Streaming Própria (Colégio WR)

**Documento interno — Grupo Jet**
Preparado por: Juan, CEO
Data: 2026
Classificação: Confidencial

---

## 1. Premissa

Rodar **on-premise** no datacenter do Grupo Jet (backbone, latência e Fortinet já existentes) e usar a **Digital Ocean só como DR**. Isso zera o custo de egress que mataria a conta na nuvem.

Volume de referência: ~43 aulas/semana ao vivo, pico estimado de 200–400 alunos simultâneos.

---

## 2. CapEx (investimento único)

| Item | Especificação | Qtd | Custo unit. (R$) | Total (R$) |
|---|---|---|---|---|
| Origin server (transcodificação) | 2× CPU, 64 GB RAM, GPU NVENC | 2 | 18.000 | 36.000 |
| Ingest / edge server | 16 vCPU, 32 GB RAM, SSD NVMe | 2 | 9.000 | 18.000 |
| Storage gravações (NAS) | 48 TB útil, RAID | 1 | 14.000 | 14.000 |
| Load balancer / roteador | Fortinet ou equivalente | 1 | 6.000 | 6.000 |
| Switches / cabeamento | 10 GbE | 1 lote | 4.000 | 4.000 |
| **Total CapEx** | | | | **78.000** |

> Se já houver hardware ocioso no datacenter, o CapEx cai para ~R$ 20–30 mil (só storage + switches).

---

## 3. OpEx mensal

| Item | Detalhe | Mensal (R$) |
|---|---|---|
| Energia + refrigeração | 2U–4U de rack | 800 |
| Link / backbone | Já existente — custo marginal | 0 |
| Digital Ocean (DR) | 2 droplets + object storage + bandwidth | 1.200 |
| Domínio + SSL + monitoramento | | 300 |
| Manutenção de software | Atualizações, patches | 1.500 |
| Suporte N1/N2 (plantão de aula) | 2 pessoas, escala | 4.000 |
| **Total OpEx** | | **~7.800** |

---

## 4. Custo de desenvolvimento (MVP)

| Item | Estimativa (R$) |
|---|---|
| Desenvolvimento MVP (10–15 dias, com IA) | 25.000 – 40.000 |
| Testes de carga + integração | 5.000 |
| **Total dev** | **30.000 – 45.000** |

> Usando IA pra gerar boilerplate (player, ABR, ingest, dashboard), o tempo de dev cai de meses pra ~15 dias. O gargalo vira teste de carga, não programação.

---

## 5. Resumo financeiro

| Categoria | Valor (R$) |
|---|---|
| CapEx (hardware) | 78.000 |
| Dev MVP | 30.000 – 45.000 |
| OpEx mensal | ~7.800 |
| **Investimento total ano 1** | **~115.000 – 130.000** |
| **Custo mensal recorrente (ano 2+)** | **~7.800** |

---

## 6. Comparativo rápido

| | Spalla (hoje) | Vimeo Enterprise | Plataforma Grupo Jet |
|---|---|---|---|
| Custo mensal | ~R$ 8–15 mil | ~R$ 20–40 mil | ~R$ 7.800 |
| Controle | Baixo | Médio | Total |
| Suporte | Terceiro | Terceiro | Local |
| Customização | Nenhuma | Limitada | Total |
| Risco de travamento | Alto (relatado) | Baixo | Baixo (sob medida) |

A plataforma própria se paga em relação à Spalla em **menos de 12 meses**, e em relação ao Vimeo em **menos de 6 meses**.

---

## 7. Riscos e mitigações

| Risco | Mitigação |
|---|---|
| Pico de alunos acima do estimado | ABR + escala horizontal nos origin servers |
| Queda do datacenter | DR na Digital Ocean com failover automático |
| Dependência de 1–2 devs | Documentação + IA pra manutenção |
| Atraso no MVP | Escopo mínimo definido: stream + player + gravação + fallback |

---

## 8. Decisão pedida

Aprovar o CapEx de ~R$ 78 mil e o orçamento de dev de ~R$ 40 mil para iniciar o MVP em 15 dias, com go-live completo em ~25 dias.

**Aprovação:** _______________ (Juan, CEO)
