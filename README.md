# MON CAP · Construire ma liberté — PWA V5

Application personnelle responsive, avec **six missions** : Mes moteurs, Mes priorités, Mes méthodes, Effort & Persévérance, Écoute & Confiance, Ma synthèse personnelle.

## Parcours
- 3 questions ouvertes par mission, soit **18 questions** au total.
- Mission 02 : choix de trois priorités parmi six cartes, puis réflexion ouverte.
- Chaque mission possède son accent couleur et ses propres formulations de synthèse.
- Échange avec ChatGPT préparé à partir des réponses écrites et, pour la mission 06, des synthèses précédemment validées.
- **Aucune transmission automatique à ChatGPT** : relire, modifier, copier le prompt et le coller volontairement.
- Une synthèse personnelle en quatre rubriques, relue et validée par l'utilisateur.

## Sauvegarde et migration
Les réponses sont stockées localement dans le navigateur, sans serveur de stockage. La clé historique `moncap_mission01_v1` est conservée pour retrouver le carnet de la V4. Le schéma V5 (version 3) migre les réponses des anciennes questions et les synthèses V4, dont les anciennes étapes 2 à 5 deviennent respectivement les missions 3 à 6. Les anciennes sauvegardes JSON (versions 1 et 2) peuvent aussi être importées. **Faire une sauvegarde JSON avant toute mise à jour.**

L'app et ses fichiers sont publics sur GitHub Pages, **pas les réponses du carnet**. Éviter d'inclure des données privées dans le dépôt public, les tickets ou les sauvegardes partagées. Les données locales ne sont pas chiffrées ni synchronisées entre appareils.

## Publication
Le workflow `.github/workflows/pages.yml` publie automatiquement chaque commit sur `main`. Les modifications de la branche `evolution-six-missions` doivent d'abord être relues dans une Pull Request, puis fusionnées vers `main`. Le cache service worker est versionné dans `sw.js` pour permettre à l'application installée de récupérer les nouvelles ressources.

## Installation
Ouvrir le site GitHub Pages en HTTPS, puis sur iPhone dans Safari choisir « Partager » > « Sur l'écran d'accueil ». Le service worker garde l'interface accessible hors ligne après un premier chargement connecté ; ChatGPT reste accessible uniquement en ligne.

## Exécution locale
```bash
python3 -m http.server 8000
```
Puis ouvrir http://localhost:8000/.
