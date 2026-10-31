# Como buildar e editar este port — sem ROM e sem chaves no repositório

Este repositório é o **projeto funcional**: ele contém o perfil provisório e o
relatório do survey, que são o que falta para editar e rebuildar o port.
Ele **não** contém a ROM (XCI/NSP), as chaves (`prod.keys`), o APK, os dados,
os shaders traduzidos (`shaders.dmsv`) nem os módulos reescritos
(`*.patched.bin`). Tudo isso só é gerado na sua máquina, com a sua ROM e as
suas chaves — e nunca deve ser commitado aqui (o `.gitignore` bloqueia todos
esses tipos).

## O que está aqui, e o que cada coisa é

- `profile/0100A75005E92000/game.tsv` — perfil provisório gerado pelo survey:
  title ID, módulos (`main`, `subsdk0`, `sdk`), build IDs (hashes dos módulos,
  não o código deles), tamanhos de memória/heap e grupos de shaders.
- `profile/0100A75005E92000/android.tsv` — perfil Android: status experimental,
  pacote `org.nx2a.t0100a75005e92000`, orientação landscape.
- `profile/0100A75005E92000/shader_*.tsv` — tabelas de shaders: identificadores
  (chaves de shader, que são hashes de identificação, **não** chaves
  criptográficas) e fatos sobre os 7.734 shaders. Não contêm código de shader.
- `docs/survey.md` — relatório do survey em texto: módulos, SDK 10, Unity
  2019.4.8f1, RomFS, censo de reescrita e imports. A pasta de extração do
  survey (que contém os módulos do jogo) **não** está aqui, de propósito.
- `README.md` — estado do port, tutorial e log.
- `.gitignore` — bloqueia ROM, chaves, APK, dados, shaders, logs e capturas.

## Toolchain usada no port original (30/10/2026)

- nx2android 0.1.2 (shirai91), Python 3.12.3, Pillow, capstone, backports.zstd
- Android NDK 27.2.12479018, .NET SDK 10.0.403, adb (platform-tools)
- Comando original: `python -m porter port <pasta-do-jogo> --experimental --debug`

## Requisito que NÃO está neste repositório

O código do nx2android em si **não** está aqui — este repo só traz o perfil
do Baldo. No outro PC, baixe o nx2android à parte
(https://github.com/shirai91/nx2android) e rode `porter doctor` antes de
buildar. No Windows, o release vem como `nx2android.exe`; no Linux, rode
com `python -m porter`. O comando abaixo usa a forma Python; no Windows,
troque `python -m porter port` por `nx2android.exe port`.

## Versão da ROM: tem que ser a mesma

O perfil só registra a versão **1.1.0 (v0)**, com os build IDs
`main=ab144284…`, `subsdk0=84e50460…`, `sdk=d9add76f…`. Se a ROM do outro PC
for outra versão, outra região ou outro update, o porter recusa o build
("not the builds the provisional profile registers"). Nesse caso, apague a
pasta do perfil copiada e rode o port de novo: ele faz o survey de novo e
gera um perfil novo para aquela versão. O perfil deste repo só é reutilizado
quando a ROM bate com a versão que ele registra.

## Como buildar (com a sua ROM e as suas chaves)

1. Instale o nx2android e a toolchain acima, e configure as suas `prod.keys`
   no porter (`porter config keys <caminho>`). As chaves ficam só na sua
   máquina, fora do repositório.
2. Crie a pasta do jogo com o seu dump (XCI ou NSP base, versão 1.1.0).
3. Copie o perfil deste repositório para dentro da pasta de build do porter,
   antes de rodar o port:

   ```
   <pasta-do-jogo>/0100A75005E92000_build/profile/0100A75005E92000/
   ```

   Com o `game.tsv` já lá, o porter **reaproveita** este perfil em vez de
   fazer o survey de novo. Para refazer o survey, apague essa pasta e rode
   o port de novo.
4. Rode:

   ```
   python -m porter port <pasta-do-jogo> --experimental --debug
   ```

   O porter extrai a sua ROM, reescreve os módulos, traduz os 7.734 shaders,
   compila o host e gera o APK + o data pack na pasta do jogo. Nada disso
   volta para este repositório.

## Como editar

- **Mudar heap/memória, módulos ou grupos de shaders:** edite
  `profile/0100A75005E92000/game.tsv` e rode o port de novo com a sua ROM.
- **Mudar o comportamento do host (ex.: investigar o flicker do menu):**
  edite o código do nx2android (upstream, em `nxnative/dm/android/`), não os
  módulos reescritos do jogo — esses são gerados e não são editáveis aqui.
  Atenção: essa edição fica no clone do nx2android, **não** neste repositório
  do Baldo. Para guardar/compartilhar uma edição de host, commite-a no seu
  fork do nx2android, separado deste repo.
- **Mudar o APK/launcher:** o APK do porter é só `NativeActivity`; qualquer
  launcher é um APK à parte, com o mesmo pacote, que lança a `NativeActivity`.
- **Depois de editar:** rode o port de novo, confira o APK no binário
  (pacote, versionCode, `libdmhost.so`, assinatura) e só então teste no
  aparelho. O log do build debug fica em
  `Android/data/org.nx2a.t0100a75005e92000/files/log.txt`.
