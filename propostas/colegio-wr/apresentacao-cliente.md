# Plataforma de Streaming Própria — Colégio WR

**Proposta do Grupo Jet para o Colégio WR**
Preparado para: Saulo, Diretor — Colégio WR de Alto Padrão, Goiânia
Preparado por: Juan, CEO — Grupo Jet
Data: 2026

---

## 1. O problema que vocês estão sentindo

O Colégio WR é referência em Goiás no ENEM, com o **WR at Home** rodando mais de **quarenta e três aulas ao vivo por semana** direto do estúdio. A plataforma atual (Spalla) entrega multi-CDN e escala, mas os alunos relatam:

- Travamentos durante a aula
- Perda de comunicação e áudio
- Experiência instável no celular, que é onde a maioria assiste

Isso não é um problema de "mais um link". É uma plataforma genérica tentando servir um fluxo específico de colégio — e falhando no momento que mais importa.

---

## 2. A solução: plataforma própria, sob medida

O Grupo Jet propõe **substituir a Spalla por completo** com uma plataforma construída do zero para o Colégio WR, rodando na nossa infraestrutura:

- Datacenter próprio com **backbone de sobra** e latência muito baixa
- Firewall Fortinet analisando todo o tráfego
- Redundância de links que vocês já conhecem e confiam

### O que muda para o aluno

| Hoje (Spalla) | Com a plataforma do Grupo Jet |
|---|---|
| Travamentos frequentes | Stream estável, ABR adaptativo |
| Chat instável | Chat em tempo real, priorizado |
| Sem gravação confiável | Gravação automática de toda aula |
| Sem diagnóstico | Diagnóstico por aluno (velocidade, jitter, dispositivo) |
| Dependência de terceiros | Controle total, suporte local |

---

## 3. Arquitetura em três camadas

**Camada 1 — Ingest redundante**
Dois servidores de entrada (nginx-rtmp / Wowza), um ativo e um em standby. Múltiplos caminhos de entrada: fibra principal + 4G de backup. Failover automático se o caminho principal cair.

**Camada 2 — Origin e transcodificação**
Servidor origin com transcodificação adaptativa em tempo real, gerando várias qualidades simultâneas (1080p, 720p, 480p) para cada aula. O player escolhe a melhor qualidade conforme a conexão do aluno.

**Camada 3 — Entrega e experiência**
Player web otimizado para celular e desktop, chat estável, gravação automática, e dashboard de monitoramento em tempo real para a equipe do colégio.

---

## 4. Disaster Recovery na Digital Ocean

O datacenter do Grupo Jet é o primário. A Digital Ocean fica como **DR**:

- Replicação contínua do stream ao vivo
- Snapshot horário das gravações
- Se o datacenter local cair, o DNS redireciona para os droplets na Digital Ocean
- O aluno nem percebe a troca

RPO (perda máxima aceitável): segundos no stream, minutos nas gravações.

---

## 5. Por que o Grupo Jet

- Já operamos conectividade, firewall e backbone — não somos um fornecedor de software genérico
- Conhecemos o fluxo completo: estúdio, alunos, dispositivos, horários de pico
- Suporte local, em português, com quem entende a operação de colégio
- Vocês não dependem mais de uma plataforma que atende milhares de clientes diferentes

---

## 6. Cronograma

| Fase | Prazo | Entrega |
|---|---|---|
| MVP funcional | 10–15 dias | Stream estável, player, gravação, fallback |
| Teste com turma piloto | +5 dias | Validação com alunos reais |
| Ajustes e polimento | +5 dias | Analytics, multi-tenant, app nativo |
| Go-live completo | ~25 dias | Todas as turmas migradas |

**Entrega do MVP em até quinze dias.** Não é "pra ontem" no sentido de mágica — é o tempo realista pra algo que o aluno já usa sem travar.

---

## 7. Próximo passo

Reunião técnica de uma hora com o time do Colégio WR para mapear o fluxo exato de aulas, dispositivos e horários de pico. A partir disso, a gente fecha o escopo e começa a construir.

**Contato:** Juan, CEO — Grupo Jet
