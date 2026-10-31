<p>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/banner-dark.svg">
    <img alt="lord.sh_ — cybersécurité @ Thales, sécurité système, kernel Windows, reverse engineering" src="assets/banner-light.svg" width="100%">
  </picture>
</p>

Je travaille en **cybersécurité chez Thales**. En parallèle, je creuse le **bas niveau** : mémoire, pagination x64, drivers kernel Windows, structures internes des moteurs de jeu. Comprendre un système de l'intérieur, c'est savoir où il peut céder et comment le protéger.

J'apprends en construisant. Chaque projet part d'une question précise, comme « comment le CPU traduit-il une adresse virtuelle ? » ou « comment détecter un débordement de tas ? », et va jusqu'au code qui y répond.

Background réseaux & télécoms (BUT R&T). Côté plus haut niveau : Python pour les bots et l'automatisation, TypeScript pour le reste.

## Cybersécurité

**Chez Thales**, je sécurise des stacks systèmes et je mets en place des solutions de sécurité. Ces missions ne sont pas publiques : elles n'apparaissent donc pas sur ce GitHub.

**Dans mes projets perso**, je travaille les mêmes sujets côté technique :

- **Protéger la mémoire** : détection des débordements de tas par canaries, métadonnées isolées des données ([secmalloc](https://github.com/Lord83700/secmalloc))
- **Sécuriser un canal** : échanges user ↔ kernel chiffrés pour résister à un dump mémoire ([driver-extended](https://github.com/Lord83700/driver-extended-public))
- **Comprendre l'attaque pour mieux défendre** : lecture de la mémoire d'un processus depuis l'extérieur et reverse engineering d'Unreal Engine ([dbd-external-esp-base](https://github.com/Lord83700/dbd-external-esp-base))

## Projets

### [driver-extended](https://github.com/Lord83700/driver-extended-public)

Driver kernel Windows (KMDF) construit par itérations : chaque étape explore un nouvel aspect du développement kernel.

- Traduction d'adresses virtuelles en physiques faite à la main (PML4 → PDPT → PD → PT), pages de 1 Go, 2 Mo et 4 Ko
- Lecture et écriture de la mémoire virtuelle et physique, résolution du CR3 depuis l'`EPROCESS` ou via les PFN
- Offsets de l'`EPROCESS` résolus dynamiquement, énumération des modules via PEB / LDR
- Communication user ↔ kernel par mémoire partagée chiffrée

`C++` · `WDK / KMDF` · `Windows x64`

### [secmalloc](https://github.com/Lord83700/secmalloc)

Allocateur mémoire sécurisé en C : réimplémentation de `malloc`, `free`, `calloc` et `realloc`, compilable en bibliothèque partagée pour remplacer celui de la libc.

- Métadonnées isolées des données, dans deux pools réservés avec `mmap`
- Canary aléatoire de 32 octets après chaque bloc pour détecter les débordements de tas
- Tests unitaires (Criterion) et stress test

`C` · `Linux` · `mmap`

### [dbd-external-esp-base](https://github.com/Lord83700/dbd-external-esp-base)

Projet d'apprentissage des structures internes d'Unreal Engine, sur Dead by Daylight : un ESP externe qui lit la mémoire du jeu depuis un autre processus.

- Parcours des structures UE (`GWorld`, `GNames`) à partir d'un SDK reconstruit
- Squelette de 22 os lu depuis `ComponentSpaceTransforms` et projeté à l'écran
- Overlay DirectX 11 et menu ImGui

`C++` · `Unreal Engine` · `DirectX 11` · `ImGui`

### Autres projets

| Projet | Description | Stack |
|---|---|---|
| **Plist** *(privé)* | Outil en ligne de commande qui liste les processus Windows et le détail de leurs threads, de leur mémoire et de leur temps CPU | C · Win32 |
| **Bot Discord** *(privé)* | Bot d'administration : giveaways, rôles, modération, tâches planifiées | Python · discord.py · MongoDB · Docker |
| **[Projet Thales](https://github.com/Lord83700/Projet-Thales)** | Projet de groupe en BUT R&T : décodage de trames Ethernet depuis un fichier binaire, stockage en base et affichage web | Python · PHP · SQL |

## Stack

<img src="https://skillicons.dev/icons?i=c,cpp,py,ts,php,mongodb,docker,git,linux,windows,visualstudio,vscode&perline=12" alt="C, C++, Python, TypeScript, PHP, MongoDB, Docker, Git, Linux, Windows, Visual Studio, VS Code">

**Domaines** : cybersécurité · sécurisation de systèmes · Windows internals · WDK / KMDF · pagination x64 · reverse engineering · Unreal Engine · DirectX 11 · ImGui
