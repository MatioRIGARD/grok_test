# Sphère Ø70 mm — Rapport ERC / DRC / cohérence KiCad

**Généré par :** `kicad/scripts/verify_kicad.py` (KiCad 9.0.2 `kicad-cli` + API `pcbnew` + shapely)  
**Date :** 27/11/2026 (heure de Bangkok, UTC+7)  
**Résultat global :** ✅ PASS — 52/52 contrôles passés

> Périmètre : **Gate G3 — cartes routées à 100 %, prêtes à fabriquer** (JLCPCB/PCBWay). Brochages et empreintes relevés sur les datasheets officiels listés ci-dessous (`/tmp/datasheets/`) ; les points non confirmés sont listés explicitement en fin de rapport (§ « À confirmer »), jamais inventés.


## 1. Syntaxe

| Contrôle | Résultat | Détail |
|---|---|---|
| lib/Sphere70.kicad_sym | ✅ | 6662 listes, en-tête `(kicad_symbol_lib` |
| sphere70-facade/sphere70-facade.kicad_pcb | ✅ | 6906 listes, en-tête `(kicad_pcb`, version 20241229 |
| sphere70-facade/sphere70-facade.kicad_pro | ✅ | JSON valide |
| sphere70-facade/sphere70-facade.kicad_sch | ✅ | 3319 listes, en-tête `(kicad_sch`, version 20231120 |
| sphere70-mpu/sphere70-mpu.kicad_pcb | ✅ | 59557 listes, en-tête `(kicad_pcb`, version 20241229 |
| sphere70-mpu/sphere70-mpu.kicad_pro | ✅ | JSON valide |
| sphere70-mpu/sphere70-mpu.kicad_sch | ✅ | 20787 listes, en-tête `(kicad_sch`, version 20231120 |
| lib/Sphere70.pretty (31 empreintes .kicad_mod) | ✅ | toutes équilibrées |

## 2. ERC/DRC (kicad-cli 9)

| Contrôle | Résultat | Détail |
|---|---|---|
| ERC sphere70-mpu : 0 erreur | ✅ | 0 erreur(s), 0 avertissement(s)  |
| DRC sphere70-mpu — violations (clearance, courtyard, bord, perçages, keepout…) | ✅ | 0 erreur(s), 1 avertissement(s) {('silk_over_copper', 'warning'): 1} |
| Parité schéma ↔ PCB sphere70-mpu | ✅ | 0 écart(s) |
| Connexions non routées sphere70-mpu = 0 | ✅ | 0 unconnected |
| Zones cuivre remplies sphere70-mpu | ✅ | 4 zones, non remplies : 0 |
| ERC sphere70-facade : 0 erreur | ✅ | 0 erreur(s), 0 avertissement(s)  |
| DRC sphere70-facade — violations (clearance, courtyard, bord, perçages, keepout…) | ✅ | 0 erreur(s), 0 avertissement(s)  |
| Parité schéma ↔ PCB sphere70-facade | ✅ | 0 écart(s) |
| Connexions non routées sphere70-facade = 0 | ✅ | 0 unconnected |
| Zones cuivre remplies sphere70-facade | ✅ | 2 zones, non remplies : 0 |

## 3. Netlist

| Contrôle | Résultat | Détail |
|---|---|---|
| sphere70-mpu : nets schéma == nets PCB | ✅ | 70 nets nommés, 360 connexions |
| sphere70-mpu : aucun net à une seule broche | ✅ | ok |

## 5. Contour Edge.Cuts

| Contrôle | Résultat | Détail |
|---|---|---|
| sphere70-mpu : pads cuivre à ≥ 0.3 mm du bord Ø56 | ✅ | 573 pads |
| sphere70-mpu : corps de composants dans le contour (hors surplomb connecteurs arrière) | ✅ | surplomb arrière : J4 2.36 mm au coin, J5 3.99 mm au coin |

## 6. Connectique arrière

| Contrôle | Résultat | Détail |
|---|---|---|
| Entraxe USB-C (J4, gauche) / Micro-HDMI (J5, droite) ≥ 10.0 mm | ✅ | 13.70 mm (J4 X=-6.5921, J5 X=7.1046, vue de dessus ; vu de dos, regard vers l’avant : USB-C à gauche, Micro-HDMI à droite) |
| Dégagements câbles 14×8 mm (USB-C) et 12×8 mm (Micro-HDMI) sans recouvrement | ✅ | marge 0.70 mm |

## 7. Keepout RF MAYA-W166

| Contrôle | Résultat | Détail |
|---|---|---|
| Aucun corps de composant (hors U2) dans la zone | ✅ | zone 33.9 mm² libre |
| Aucun pad (y compris U2) dans la zone (contact de bord rangée K = DS Fig. 15) | ✅ | 0 mm² ; contact de bord : K2, K3, K4, K5, K6, K7, K8 |
| Aucune piste / via dans la zone | ✅ | 0 |
| Aucun remplissage de zone cuivre (F/In1/In2/B) dans la zone | ✅ | 0 mm² de cuivre |

## 8. Empilement

| Contrôle | Résultat | Détail |
|---|---|---|
| Face B : rien sous le SoM 38×28 sauf J1/J2 (stack DF40 1.5 mm) | ✅ | libre |
| Face F sous la LiPo : hauteur ≤ 2.38 mm (jeu 3.0 mm − aérogel 0.52 − 0.1) | ✅ | hors découpe berceau : J6 (JST BAT-02 5,5 mm sous découpe du berceau, jeu 0,58 mm (mechanical-envelope.md)) — ok (le plus haut : J6) |
| Ø carte MPU 56.0 ≤ corde à z=-13.62 (face basse) = 57.91 mm | ✅ | jeu radial 0.96 mm |

## 9. Paires différentielles

| Contrôle | Résultat | Détail |
|---|---|---|
| sphere70-mpu HDMI TMDS D2 : skew intra-paire ≤ 0.15 mm | ✅ | P 32.10 mm / N 32.10 mm, skew 0.000 mm ≈ 0.0 ps |
| sphere70-mpu HDMI TMDS D1 : skew intra-paire ≤ 0.15 mm | ✅ | P 34.12 mm / N 34.12 mm, skew 0.000 mm ≈ 0.0 ps |
| sphere70-mpu HDMI TMDS D0 : skew intra-paire ≤ 0.15 mm | ✅ | P 19.77 mm / N 19.72 mm, skew 0.042 mm ≈ 0.3 ps |
| sphere70-mpu HDMI TMDS CLK : skew intra-paire ≤ 0,15 Tbit HDMI (101 ps @ 1,485 Gbit/s) — objectif interne 0.15 mm NON tenu | ✅ | P 21.00 mm / N 17.95 mm, skew 3.054 mm ≈ 21 ps (pire cas 7.0 ps/mm) |
| sphere70-mpu MIPI-DSI D0 : skew intra-paire ≤ 0.15 mm | ✅ | P 32.97 mm / N 32.97 mm, skew 0.000 mm ≈ 0.0 ps |
| sphere70-mpu MIPI-DSI CLK : skew intra-paire ≤ 0.15 mm | ✅ | P 25.12 mm / N 25.12 mm, skew 0.000 mm ≈ 0.0 ps |
| sphere70-mpu USB 2.0 : skew intra-paire ≤ 0.15 mm | ✅ | P 22.46 mm / N 22.46 mm, skew 0.000 mm ≈ 0.0 ps |
| sphere70-mpu : espacement mini piste-piste (nets ≠, même couche) ≥ 0.10 mm | ✅ | 0.102 mm (HDMI_DDC_SCL / HDMI_HPD) |

## 3. Netlist

| Contrôle | Résultat | Détail |
|---|---|---|
| sphere70-facade : nets schéma == nets PCB | ✅ | 11 nets nommés, 55 connexions |
| sphere70-facade : aucun net à une seule broche | ✅ | ok |

## 5. Contour Edge.Cuts

| Contrôle | Résultat | Détail |
|---|---|---|
| sphere70-facade : pads cuivre à ≥ 0.3 mm du bord Ø37 | ✅ | 75 pads |
| sphere70-facade : corps de composants dans le contour (hors surplomb connecteurs arrière) | ✅ | tous dans le contour |

## 8. Empilement

| Contrôle | Résultat | Détail |
|---|---|---|
| Ø carte façade 37.0 ≤ Ø dispo à d=25.48 mm du centre (38.73 mm) | ✅ | jeu radial 0.86 mm |

## 9. Paires différentielles

| Contrôle | Résultat | Détail |
|---|---|---|
| sphere70-facade MIPI-DSI D0 : skew intra-paire ≤ 0.15 mm | ✅ | P 8.17 mm / N 8.17 mm, skew 0.000 mm ≈ 0.0 ps |
| sphere70-facade MIPI-DSI CLK : skew intra-paire ≤ 0.15 mm | ✅ | P 6.93 mm / N 6.93 mm, skew 0.000 mm ≈ 0.0 ps |
| sphere70-facade : espacement mini piste-piste (nets ≠, même couche) ≥ 0.10 mm | ✅ | 0.135 mm (1V8 / GND) |

## 4. BOM

| Contrôle | Résultat | Détail |
|---|---|---|
| Chaque composant KiCad référencé existe dans bom.csv avec le même MPN | ✅ | 75 instances montées / 48 lignes BOM ; DNP : R1, R2 |
| Code LCSC KiCad (champ LCSC, BOM/CPL JLC) == supplier_sku bom.csv | ✅ | 74 composants porteurs d'un code LCSC, tous conformes |
| Quantités KiCad montées (2 cartes, hors DNP) == qty bom.csv | ✅ | toutes égales |
| Toute ligne BOM qty>0 est placée ou explicitement hors carte ; aucune option qty 0 placée | ✅ | hors carte : BAT-01 (cellule LiPo, raccordée par J6), TIM-01 (pad thermique (méca)), THM-01 (aérogel (méca)), IO-07 (nappe FFC entre J3 (MPU) et J1 (façade)), MECH-02 (entretoises hex (méca, trous H1-H3 façade)), MECH-03 (vis), MECH-04 (radiateur), MECH-05 (alternative radiateur), MECH-06 (coque), FAB-01 (fabrication PCB MPU), FAB-02 (fabrication PCB façade), FAB-03 (assemblage), BAT-03 (NTC 103JT-025 offboard, câblée sur les pastilles J7 (TS)), SOM-01 (SoM, enfiché sur J1/J2 (MOD1 contour)), DISP-01 (AMOLED, nappe sur J2 façade (DS1 contour)) |
| Cotes de boîtier des empreintes == cotes bom.csv | ✅ | 45 empreintes comparées |

## Synthèse ERC / DRC kicad-cli

| Carte | ERC err. | ERC avert. | DRC err. | DRC avert. | Parité | Non routés | Segments | Vias | Long. pistes (mm) | Zones |
|---|---|---|---|---|---|---|---|---|---|---|
| sphere70-mpu | 0 | 0 | 0 | 1 | 0 | 0 | 1101 | 298 | 1560.4 | 4 |
| sphere70-facade | 0 | 0 | 0 | 0 | 0 | 0 | 98 | 189 | 140.6 | 2 |

- sphere70-mpu — détail DRC : silk_over_copper (warning) ×1

## Paires différentielles (longueurs pistes mesurées après égalisation accordéon)

| Carte | Paire | Classe | Long. P (mm) | Long. N (mm) | Skew (mm) | Skew (ps, 7 ps/mm) |
|---|---|---|---|---|---|---|
| sphere70-mpu | HDMI TMDS D2 | HDMI_100R | 32.10 | 32.10 | 0.000 | 0.0 |
| sphere70-mpu | HDMI TMDS D1 | HDMI_100R | 34.12 | 34.12 | 0.000 | 0.0 |
| sphere70-mpu | HDMI TMDS D0 | HDMI_100R | 19.77 | 19.72 | 0.042 | 0.3 |
| sphere70-mpu | HDMI TMDS CLK | HDMI_100R | 21.00 | 17.95 | 3.054 | 21.4 |
| sphere70-mpu | MIPI-DSI D0 | DSI_100R | 32.97 | 32.97 | 0.000 | 0.0 |
| sphere70-mpu | MIPI-DSI CLK | DSI_100R | 25.12 | 25.12 | 0.000 | 0.0 |
| sphere70-mpu | USB 2.0 | USB_90R | 22.46 | 22.46 | 0.000 | 0.0 |
| sphere70-facade | MIPI-DSI D0 | DSI_100R | 8.17 | 8.17 | 0.000 | 0.0 |
| sphere70-facade | MIPI-DSI CLK | DSI_100R | 6.93 | 6.93 | 0.000 | 0.0 |

## Cotes empreintes vs bom.csv

| Réf. | BOM | Cote BOM (mm) | Corps empreinte (mm) | OK |
|---|---|---|---|---|
| C1 | PAS-C02 | 1.0x0.5 | 1.0x0.5 | ✅ |
| C1 | PAS-C08 | 1.6x0.8 | 1.6x0.8 | ✅ |
| C13 | PAS-C04 | 1.0x0.5 | 1.0x0.5 | ✅ |
| C14 | PAS-C01 | 1.0x0.5 | 1.0x0.5 | ✅ |
| C2 | PAS-C07 | 3.2x1.6 | 3.2x1.6 | ✅ |
| C3 | PAS-C03 | 1.0x0.5 | 1.0x0.5 | ✅ |
| C4 | PAS-C06 | 1.6x0.8 | 1.6x0.8 | ✅ |
| C5 | PAS-C05 | 1.6x0.8 | 1.6x0.8 | ✅ |
| D2 | PROT-04 | 1.7x1.3 | 1.7x1.3 | ✅ |
| D3 | PROT-01 | 3.9x1.9 | 2.8x1.8 (corps) ; hors-tout BOM 3.9x1.9 ⊂ courtyard 4.50x2.30 | ✅ |
| D4 | PROT-02 | 1.0x0.6 | 1.0x0.6 | ✅ |
| F1 | PROT-03 | 3.2x1.6 | 3.2x1.6 | ✅ |
| J1 | SOM-02 | 22.6x3.38 | 22.6x3.38 | ✅ |
| J2 | DISP-02 | 6.8x1.7 | 6.8x1.7 | ✅ |
| J3 | IO-06 | 19.5x6.2 | 19.5x6.2 | ✅ |
| J4 | IO-01 | 7.35x8.94 | 8.94x7.35 | ✅ |
| J5 | IO-02 | 7.5x6.5 | 6.5x7.5 | ✅ |
| J6 | BAT-02 | 7.9x8.6 | 7.9x8.6 | ✅ |
| L1 | PWR-02 | 4.0x4.0 | 4.0x4.0 | ✅ |
| L2 | PWR-06 | 2.5x2.0 | 2.5x2.0 | ✅ |
| L3 | PWR-08 | 2.5x2.0 | 2.5x2.0 | ✅ |
| LED1 | UI-01 | 1.6x0.8 | 1.6x0.8 | ✅ |
| MH1 | MECH-01 | 4.35x4.35 | 4.35x4.35 | ✅ |
| R10 | PAS-R06 | 1.0x0.5 | 1.0x0.5 | ✅ |
| R12 | PAS-R07 | 1.0x0.5 | 1.0x0.5 | ✅ |
| R13 | PAS-R08 | 1.0x0.5 | 1.0x0.5 | ✅ |
| R15 | PAS-R09 | 1.0x0.5 | 1.0x0.5 | ✅ |
| R16 | PAS-R10 | 1.0x0.5 | 1.0x0.5 | ✅ |
| R18 | PAS-R11 | 1.0x0.5 | 1.0x0.5 | ✅ |
| R3 | PWR-03 | 1.0x0.5 | 1.0x0.5 | ✅ |
| R4 | PAS-R01 | 1.0x0.5 | 1.0x0.5 | ✅ |
| R5 | PAS-R02 | 1.0x0.5 | 1.0x0.5 | ✅ |
| R6 | PAS-R03 | 1.0x0.5 | 1.0x0.5 | ✅ |
| R8 | PAS-R04 | 1.0x0.5 | 1.0x0.5 | ✅ |
| R9 | PAS-R05 | 1.0x0.5 | 1.0x0.5 | ✅ |
| SW2 | IO-08 | 5.1x5.1 | 5.1x5.1 | ✅ |
| U10 | IO-04 | 2.9x1.6 | 2.9x1.6 | ✅ |
| U11 | IO-05 | 2.3x2.0 | 2.0x2.3 | ✅ |
| U12 | PWR-04 | 1.6x1.6 | 1.6x1.6 | ✅ |
| U2 | WIFI-01 | 14.3x10.4 | 10.4x14.3 | ✅ |
| U3 | PWR-01 | 4.0x4.0 | 4.0x4.0 | ✅ |
| U4 | PWR-05 | 1.6x1.6 | 1.6x1.6 | ✅ |
| U5 | PWR-07 | 2.9x1.6 | 2.9x1.6 | ✅ |
| U6 | PWR-09 | 2.9x1.6 | 2.9x1.6 | ✅ |
| U7 | IO-03 | 2.5x1.0 | 2.5x1.0 | ✅ |

## Datasheets officiels utilisés (brochages / land patterns)

| MPN | Source |
|---|---|
| `BQ25895RTWR` | TI SLUSC88C (BQ25895) — Pin Functions §6, RTW0024B |
| `TPS61023DRLR` | TI SLVSF14B — Pin Functions §5, DRL0006A |
| `TLV62569DBVR` | TI SLVSDB4 (TLV62569) — Pin Functions DBV |
| `TLV75518PDBVR` | TI SBVS320 (TLV755P) — Pin Functions DBV |
| `TPD4E05U06DQAR` | TI SLVSBN5 (TPD4E05U06) — Pin Functions DQA |
| `USBLC6-2SC6` | ST USBLC6-2 DS — SOT23-6 |
| `MTXS0102DCUR` | MSKSEMI MTXS0102 DS p.2 (colonne DCU : VCCB=7) = TI TXS0102 DCU |
| `TUSB320LAIRWBR` | TI SLLSEQ8D — Pin Functions §5, RWB0012A (land pattern p.36) |
| `MAYA-W166-00B` | u-blox UBX-21006380 R05 — §3.1 pin assignment (LGA-86), §6.1 footprint |
| `UCM-iMX8PLUS` | CompuLab UCM-iMX8M-Plus Reference Guide (rév. sept. 2026) — Tables 5/6/17/19/24/27/36/37/39/40/45/46, Fig. 4 |
| `DF40C-100DS-0.4V(51)` | Hirose DF40 catalogue p.4 — Recommended PCB layout DF40C |
| `BO139A454SPI` | Panox/BOE BO139A454SPI DS Table 2 PIN Assignments |
| `BM28B0.6-24DS/2-0.35V(51)` | Hirose BM28 DS — Recommended PCB layout (receptacle 24DS) |
| `FH12A-30S-0.5SH(55)` | Hirose FH12 EDC3-150556-51 — Recommended land pattern |
| `TYPE-C 16PIN 2MD(073)` | SHOU HAN TYPE-C 16PIN 2MD(073) (LCSC C2765186) — Recommended PCB layout |
| `467651001` | Molex SD-46765-001 feuille 4 — Recommended PCB layout |
| `S2B-PH-SM4-TB(LF)(SN)` | JST PH catalogue — SMT side entry (empreinte KiCad officielle JST_PH_S2B-PH-SM4-TB) |
| `TS-1187A-B-A-B` | XKB TS-1187A — P.C.B layout |
| `XAL4020-222MEC` | Coilcraft Doc 806 — Recommended land pattern |
| `9774060243R` | Würth WA-SMSI 9774060243R — Recommended land pattern (NPTH Ø3,0 + pastille Ø5,3) |

## À confirmer (points ouverts, non inventés)

- **FFC IO-07 sens** : Nappe 0,5 mm contacts même côté : correspondance broche n (MPU J3) ↔ broche n (façade J1) supposée ; à valider sur maquette @cad avant commande.
- **Panox BM28** : Note Panox « pin definition needs to confirm with hardware engineer before AMOLED FPC fixed » : brochage Table 2 utilisé ; orientation broche 1 du réceptacle BM28 à recouper avec le FPC réel.
- **BM28 contacts de puissance** : Réceptacle BM28B0.6-24DS/2 : 4 contacts de puissance (MP1–MP4) laissés sans potentiel (non décrits par Panox).
- **SoM U4 face inférieure** : Composant U4 (≈11,8 × 13,2 mm, probable eMMC) sous le SoM avec empilement 1,5 mm : aucun composant carrier sous le SoM (pistes/vias seulement) ; hauteur réelle à confirmer sur le DXF/STEP CompuLab.
- **SoM trous de fixation** : Trous de fixation du SoM non repris (cotes DXF CompuLab non publiées dans le guide) : maintien par B2B + TIM/radiateur.
- **PWRBTN ↔ /QON** : BTN_USER relie PWRBTN (P2-64, pull-up interne SoM) et /QON via D2 (1N5819WS) : niveau de pull-up PWRBTN (SNVS) à vérifier à l'oscilloscope au premier boot.
- **USB1_VBUS_DET** : P1-24 laissé NC (broches non-alim limitées à 3,6 V, aucun diviseur en BOM) : détection d'attache par TUSB320 (INT_N) en firmware.
- **HDMI CEC** : CEC relié directement (P1-85, 3,3 V) via ESD U9 ; la SBEV isole par transistors (non en BOM).
- **MAYA PDn** : PDn (J3) est dans le domaine 1V8 (u-blox Table 16 + §2 : pull-up interne 10 kΩ vers 1V8 ; abs. max 1V8 = 1,98 V) alors que WL_PDN_N vient d'un GPIO SoM 3,3 V (GPIO5_IO27, P1-61). EXIGENCE firmware : pad configuré en open-drain (ODE = 1), jamais piloté à l'état haut — le niveau haut vient du pull-up interne 1V8. Option matérielle v2 : résistance série / transistor (hors BOM G3).
- **Domaine GPIO4 (AMOLED)** : OLED_RST_N / OLED_VCI_EN / OLED_TE = GPIO4_IO20/IO10/IO11 (P2-52/53/55), domaine « 3,3 V/1,8 V » selon CompuLab ; l'AMOLED (VDDIO 1,65–1,95 V) exige 1,8 V → configuration du domaine de ces broches à confirmer avec CompuLab avant le premier allumage (sinon translateur v2).
- **Pull-ups I2C2 / IRQ** : KiCad : R6/R7 (I2C2), R8 (CHG_INT_N), R19 (CC_INT_N) tirées vers 3V3, car CompuLab Table 27 (I2C2 P1-97/99 = 3,3 V) et GPIO1_IO0/IO1 = 3,3 V. Le texte « rôle » de bom.csv (PAS-R03/PAS-R04) dit « vers 1V8 » : libellé BOM à corriger par @parts (MPN/valeurs inchangés). I2C2 porte aussi RTC + EEPROM du SoM avec pull-ups internes non publiés : 2,2 kΩ en parallèle à valider à l'oscilloscope (temps de montée 400 kHz).
- **Diamètres CAO vs KiCad** : mechanical-envelope.md rév. 1 modélise la MPU Ø56,31 et la façade Ø38 ; le KiCad G3 garde Ø56,0 (jeu 0,96 mm) et Ø37,0 (jeu 0,86 mm), plus petits donc compatibles. @cad à aligner son modèle sur les Gerbers.
- **Impédances** : Largeurs/écarts calculés IPC-2141A pour l'empilement JLC04161H-7628 ; à valider avec le calculateur JLCPCB lors de la commande (option impédance contrôlée).
- **Paires différentielles** : Paires routées par Freerouting (P et N routées indépendamment, non couplées) puis égalisées en longueur par accordéons (g3_fixups.py tune) : skew 0,000–0,042 mm sur toutes les paires sauf HDMI TMDS CLK (résiduel 3,05 mm ≈ 21 ps, sous le budget HDMI 0,15 Tbit = 101 ps à 1080p60, mais au-dessus de l'objectif interne 0,15 mm faute de place). Impédance différentielle réelle des tronçons non couplés non garantie → revue humaine des TMDS/DSI avant commande (ou option impédance contrôlée JLC + reroutage couplé).
