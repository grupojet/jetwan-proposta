# Topologia da Solução — Colégio WR At Home

```text
[ Estúdio WR ]
   |  (câmera + áudio + tela)
   v
[ Ingest A ]  fibra principal  ----+----> [ Origin Server ]
[ Ingest B ]  backup 4G/satélite --+         |  (transcodificação adaptativa)
                                          v
                                   [ Player Web / App ]
                                          |
                    +---------------------+---------------------+
                    |                                           |
                    v                                           v
            [ Aluno em casa ]                          [ Gravação automática ]
                    |                                           |
                    |  (se stream cair)                         v
                    +----> [ Versão gravada ]          [ Storage local ]
                                                              |
                                                              v
                                                    [ Replicação contínua ]
                                                              |
                                                              v
                                                    [ Digital Ocean - DR ]
                                                              |
                    (se datacenter local cair)                v
                    <-------------------------------- [ DNS redireciona ]
```

**Pontos-chave da topologia**

- Dois caminhos de ingest independentes com failover automático.
- Origin gera 1080p, 720p e 480p ao mesmo tempo.
- Player escolhe a qualidade conforme a conexão do aluno.
- Gravação automática em paralelo ao stream ao vivo.
- Replicação contínua para a Digital Ocean como disaster recovery.
- DNS redireciona para o DR se o datacenter local cair.
