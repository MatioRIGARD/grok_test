# Sphère Ø70 mm

> **Projet en cours (Gate G3) : pas terminé, pas fabriqué, pas testé.**

Objet de bureau connecté, diamètre 70 mm : écran AMOLED 1,39″, module SoM i.MX 8M Plus, batterie LiPo 1500 mAh isolée, radiateur-lest en aluminium et laiton.

- Site : https://matiorigard.github.io/grok_test/
- Deck : https://matiorigard.github.io/grok_test/deck/
- Vidéo : https://matiorigard.github.io/grok_test/video/sphere-70mm-promo.mp4

## État G3

Cartes routées, rien de commandé.

- PCB MPU Ø56 mm, 4 couches : 1101 pistes / 298 vias
- PCB façade Ø37 mm, 2 couches : 98 pistes / 189 vias
- 0 connexion non routée, 0 erreur ERC, 0 erreur DRC
- Nomenclature candidate : 807,37 USD / 67 lignes — estimation, pas un devis

## Points ouverts

- Avertissement sérigraphie sur R3
- Skew de la paire HDMI CLK : 3,054 mm, à revoir avant toute commande
- Les vues 3D montrent les PCB nues
- L'autonomie et les températures sont des estimations

## Dépôt

- `index.html`, `_astro/`, `assets/`, `film/` — site publié par GitHub Pages depuis `master`
- `deck/` — deck
- `video/sphere-70mm-promo.mp4` — vidéo
- `fab/` — sorties de fabrication G3 (archives Gerber JLCPCB, Gerbers, perçages, CPL, `bom.csv`, rapport ERC/DRC). Pas commandées, pas fabriquées, pas testées. Voir `fab/README.md`.
- `.github/workflows/pages.yml` — déploiement Pages
- `.nojekyll` — publication du site tel quel
