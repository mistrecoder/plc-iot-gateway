# Journal de bord

## Semaine 0 : mise en place
- Décision : OpenPLC v4 (runtime Docker + Editor v4), car v3 est archivé depuis avril 2026.
- Décision : environnement Windows + WSL2 + Docker Desktop.
- Décision : traçabilité par Conventional Commits `type(SX-TX.X)` + une branche et une PR par semaine.

## Semaine 1 : Fondamentaux & Premier circuit Ladder
- Réalisation T1.1 : Synthèse complète rédigée sur le principe du cycle de scan (PII, exécution logique, PIO, housekeeping/Watchdog) et l'adressage IEC 61131-3 (%IX, %QX, %MX, tailles X/B/W/D).
- Réalisation T1.3 : Conception du circuit de démarrage moteur sous OpenPLC Editor v4 (`ex01_moteur`).
- Tests et validation :
  1. Marche avec auto-maintien : impulsion sur `bp_marche` (%IX0.0) -> maintien de la bobine `moteur` (%QX0.0) via son contact auxiliaire en dérivation.
  2. Arrêt normal : impulsion sur `bp_arret` (%IX0.1) -> coupure du moteur et réinitialisation de l'auto-maintien.
  3. Arrêt d'urgence : déclenchement de `arret_urgence` (%IX0.2) -> coupure prioritaire immédiate et verrouillage de tout redémarrage intempestif.
- Preuves enregistrées dans `docs/preuves/t1.1-premier-programme.png`, `docs/preuves/t1.3-ex01-moteur-simulation_arret_normal.png` et `docs/preuves/t1.3-ex01-moteur-simulation_E-Stop.png`.