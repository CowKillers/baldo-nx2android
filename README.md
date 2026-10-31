# Baldo: The Guardian Owls no Android (nx2android)

Port experimental de **Baldo: The Guardian Owls** (Switch) para Android, feito com o
[nx2android](https://github.com/shirai91/nx2android) — o código arm64 do jogo roda
nativamente no celular, com o host substituindo os serviços do Switch e o NVN
reproduzido em Vulkan, sem emulador.

> **Experimental — sem release.** Este repositório não contém o jogo, as chaves,
> o APK, os dados, os shaders nem nenhum arquivo extraído do jogo. Não há release
> aqui, e não haverá, até que o port esteja provado no aparelho.

## Vídeo

🎬 Gameplay no Android — link a ser adicionado.

## Estado atual (31/10/2026, honesto)

- Port experimental construído com o porter do nx2android
  (`porter port --experimental --debug`): perfil provisório adivinhado pelo survey,
  porque o jogo **não tem perfil** no nx2android para o title
  `0100A75005E92000`.
- O jogo é Unity 2019.4.8f1, IL2CPP, NVN, SDK 10, versão 1.1.0.
  O survey traduziu **7.734 de 7.734 shaders** (bundle de 101 MB).
- APK gerado pelo porter: pacote `org.nx2a.t0100a75005e92000`,
  versionCode 1, versão do jogo 1.1.0, build debug (gera `log.txt`).
- Data pack gerado pelo porter: 40 arquivos, 1,0 GB
  (`RomFS/`, `mods/`, `shaders.dmsv`, `env.txt`).
- **O que já se sabe no aparelho:** num port feito no Windows, o jogo abre e
  chega ao menu, mas as texturas explodem e o vídeo pisca. Isso está em
  investigação — o diagnóstico depende do `log.txt` da versão debug no Galaxy S23.
  Não trate este port como jogável até que esse sintoma esteja resolvido e
  provado no aparelho.

## Mini tutorial — como instalar

### Requisitos

- Android arm64, com Vulkan. Alvo do teste: Galaxy S23 (Adreno 740, Vulkan 1.3).
- O APK sozinho **não** é o jogo: ele é só o executável do port.

### Passo 1 — Gere os seus próprios dados

**Os dados NÃO vêm no APK e NÃO estão neste repositório.** Você precisa gerar
o seu próprio pacote de dados com o porter do nx2android, a partir do
**seu próprio dump do jogo (XCI/NSP) e das suas próprias chaves** — nunca baixe
nem compartilhe RomFS, XCI/NSP, shaders ou chaves de terceiros.

O port experimental usa:

```
python -m porter port <pasta-do-jogo> --experimental --debug
```

### Passo 2 — Coloque os dados do jogo no lugar certo

Depois de gerar o pacote, copie o conteúdo **solto** (sem pasta extra no meio)
para:

```
Android/data/org.nx2a.t0100a75005e92000/files/
```

A pasta tem que ficar assim:

```
Android/data/org.nx2a.t0100a75005e92000/files/
├── RomFS/
├── mods/
├── shaders.dmsv
├── env.txt
└── nx2a-data.json
```

O `shaders.dmsv` vai **na raiz de `files/`**, não dentro de `mods/` e não com
outro nome (por exemplo, `shaders2.dmsv` é ignorado pelo host).

### Passo 3 — Instale o APK gerado pelo porter e abra o jogo

1. Instale o APK gerado na pasta do jogo.
2. Abra o jogo. Se ele parar sem os dados, é porque a pasta acima ainda não
   está completa — complete os dados antes de concluir qualquer coisa sobre o port.

### Log

O build debug escreve o log em:

```
Android/data/org.nx2a.t0100a75005e92000/files/log.txt
```

A cada novo lançamento, o log anterior vira `log.prev.txt`. Copie o `log.txt`
**antes** de abrir o jogo de novo, senão a sessão do problema se perde.

## Créditos e aviso

- Ferramenta: [nx2android](https://github.com/shirai91/nx2android), port Android
  do [nxnative](https://github.com/seedds/nxnative).
- Uso pessoal, sem distribuição e sem arquivos do jogo neste repositório.
