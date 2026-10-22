# Conception PCB - Altium Designer 26

Depot unique regroupant les projets electroniques et les bibliotheques Altium
Designer 26 du workspace local. La structure existante a ete conservee pour ne
pas casser les chemins relatifs entre les fichiers Altium.

## Contenu

### Projets

- `PCB_Project/MultiVibrateur.PrjPcb`
  - schema : `MultiVibrateur.SchDoc`
  - PCB : `MultiVibrateur.PcbDoc`
  - BOM active : `MultiVibrateur.BomDoc`
  - configuration de sorties : `Job1.OutJob`
  - `Copy of MultiVibrateur.PcbDoc` est conserve comme document PCB non rattache
    au projet.
- `Amplificateur_Audio/PreAmpli.PrjPcb`
  - schema : `PreAmli.SchDoc` (orthographe d'origine conservee)
  - PCB : `PreAmpli.PcbDoc`
  - BOM active : `PreAmpli.BomDoc`
  - configuration de sorties : `Job1.OutJob`

### Bibliotheques

- `Library/First Integrated Library.LibPkg`
  - `Symboles.SchLib`
  - `Footprints.PcbLib`
  - `1206_CAPACITOR_PACKAGE.PcbLib`
- `Bibliotheques/AltiumCAOQ2_2023/AltiumCAOQ2_2023.LibPkg`
  - `Schlib1_2023.SchLib`
  - `PcbLib1_2023.PcbLib`
- `Bibliotheques/1984617/`
  - `1984617.SchLib`
  - `1984617.PcbLib`
- `AOP-1671IDBVR.PcbLib`
- Les sources exportees presentes sous `AD26/Library/ExportIntLib/` sont aussi
  conservees. Les exemples, modeles et OutputJobs livres avec l'installation
  Altium 26 sont exclus du depot car ils ne constituent pas des projets utilisateur.

Les bibliotheques compilees `.IntLib` ne sont pas versionnees : elles sont
recreees en compilant les fichiers `.LibPkg` dans Altium Designer.

## Ouvrir le workspace

1. Cloner le depot sous Windows.
2. Dans Altium Designer 26, ouvrir `ElectronicWorkSpace.DsnWrk`.
3. Le workspace charge `MultiVibrateur`, `PreAmpli`, `First Integrated Library`
   et `AltiumCAOQ2_2023` via des chemins relatifs.
4. Si une bibliotheque integree n'est pas encore installee, ouvrir son `.LibPkg`,
   lancer **Compile Integrated Library**, puis installer le `.IntLib` genere
   depuis le panneau **Components/Libraries**.

Les projets font reference aux noms `First Integrated Library.IntLib` et
`AltiumCAOQ2_2023.IntLib`. Leurs sources se trouvent dans les dossiers indiques
ci-dessus. Les documents declares par chaque `.PrjPcb` utilisent des chemins
relatifs et restent dans le meme dossier que le projet.

## Utiliser Git

Avant de commencer une modification :

```bash
git pull --ff-only
```

Pour sauvegarder un travail :

```bash
git status
git add -A
git diff --cached --stat
git commit -m "Description de la modification"
git push
```

Les dossiers `History`, `__Previews`, journaux, caches et sorties de compilation
recreables sont ignores. Les fichiers sources Altium (`.PrjPcb`, `.SchDoc`,
`.PcbDoc`, `.SchLib`, `.PcbLib`, `.LibPkg`, `.OutJob`, `.BomDoc`) restent suivis.

## Historique de la consolidation

`MultiVibrateur` et `PreAmpli` etaient auparavant deux depots Altium 365
independants. Leurs historiques complets ont ete sauvegardes localement sous
`.legacy-git/` avant la creation de ce depot unique. Ces sauvegardes et les
anciens dossiers Git renommes sont volontairement ignores et ne sont pas publies.
