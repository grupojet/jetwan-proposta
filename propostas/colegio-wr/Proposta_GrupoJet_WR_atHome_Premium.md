# Plataforma de Streaming Própria — Colégio WR At Home

**Proposta do Grupo Jet**  
Preparado para: Saulo, Diretor — Colégio WR de Alto Padrão, Goiânia  
Data: 2026  
Formato: Apresentação + narração em áudio (voz corporativa feminina, natural)

---

## 1. Visão geral

O Colégio WR já aprovou o piloto. Esta proposta descreve **como o sistema vai funcionar**, o escopo completo e o modelo comercial.

A plataforma roda no datacenter próprio do Grupo Jet, com fibra de sobra, backbone redundante e Fortinet. A Digital Ocean fica como disaster recovery. Nada de depender de plataforma genérica de terceiros.

---

## 2. Arquitetura

**Ingest redundante**  
Dois caminhos de entrada independentes: fibra principal e backup 4G. Failover automático. Se um caminho oscilar, o outro assume em segundos, sem o aluno perceber.

**Origin e transcodificação**  
Servidor origin com transcodificação adaptativa em tempo real, gerando várias qualidades simultâneas (1080p, 720p, 480p). O player escolhe a melhor qualidade conforme a conexão do aluno.

**Entrega**  
Player web otimizado para celular e desktop. Chat em tempo real, priorizado. Gravação automática de toda aula. Dashboard de monitoramento para a equipe do colégio.

---

## 3. Redundância real

Sinal A e sinal B separados geograficamente. Quando o A cai, o B assume de verdade — diferente do que acontece hoje, onde o B não inicia.

---

## 4. Gravação e fallback

Toda aula grava automaticamente. Se o stream cair de vez, o aluno cai numa versão gravada sem interrupção. A aula não para.

---

## 5. Disaster Recovery

Replicação contínua do stream para a Digital Ocean. Snapshot horário das gravações. Se o datacenter local cair, o DNS redireciona e a aula segue de lá. O aluno nem percebe a troca.

---

## 6. Modelo comercial

- Mínimo mensal equivalente a mil alunos ativos (cobre o custo de infraestrutura)
- Taxa por aluno ativo acima desse piso
- Com três mil alunos, o valor mensal fica em torno de vinte e quatro mil reais
- Investimento inicial em hardware: cerca de setenta e oito mil reais, que se paga em menos de um ano

---

## 7. Cronograma

- MVP funcional: 10 a 15 dias
- Teste com turma piloto: mais 5 dias
- Ajustes e polimento: mais 5 dias
- Go-live completo: cerca de 25 dias

---

## 8. Áudio de narração

A narração que acompanha esta apresentação está disponível no link:

https://cdn.kairogen.ai/audio-generations/6a9f53f0283c2ce5cb1b23c5/6ab15b22399d4861993d379e/speech.mp3

Voz feminina corporativa premium, natural e humana, sem menção a nomes. Pode ser ouvida enquanto o Saulo lê os slides.

---

**Grupo Jet**  
Conectividade e infraestrutura própria para educação.
