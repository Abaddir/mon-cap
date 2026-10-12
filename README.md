# MON CAP · Construire ma liberté — PWA V4

**Application personnelle conçue pour iPhone, ordinateur et tablette.** Elle contient actuellement **la mission 1 complète** (15 questions ouvertes réparties en cinq étapes), le carnet, les synthèses et le bilan. Les missions 2–6 restent à développer.

## Utilisation

- Un site publié en HTTPS permet d'installer l'application sur l'écran d'accueil.
- Ouvrir `index.html` en local permet d'essayer l'interface, mais **pas d'installer le mode hors ligne** : les service workers requièrent HTTPS ou localhost.
- Sur iPhone : ouvrir l'URL **dans Safari** → Partager → **Sur l'écran d'accueil** → **Ouvrir comme app** si proposé → Ajouter.
- Après la première visite connectée, la coque de l'application (interface et questions) est normalement disponible hors ligne. **ChatGPT nécessite Internet.**
- L'icône et l'affichage autonome sont pris en charge. Les réponses sont enregistrées **sur cet appareil, dans ce navigateur / cette web app**, et non dans GitHub.
- Pour migrer depuis V3 : ouvrir **Mon carnet → Restaurer une sauvegarde** et sélectionner le JSON exporté depuis V3.

## Confidentialité

Aucun compte et aucun serveur de stockage de réponses. `localStorage` enregistre le carnet sous la clé `moncap_mission01_v1` dans l'origine web. Les ressources statiques seulement sont mises en cache par `sw.js`. Les réponses ne figurent pas dans les fichiers publics et ne sont pas envoyées à GitHub. Le prompt ChatGPT n'est transmis que si la personne choisit de le copier-coller. **Attention : ni chiffrement local ni synchronisation**, une autre personne ayant accès à l'appareil ou à la sauvegarde peut lire les données. Conserver la sauvegarde JSON dans un endroit privé.

La PWA installée depuis l'écran d'accueil et Safari peuvent, selon les versions d'iOS, avoir des espaces de données distincts : **ne pas se fier à une synchronisation entre eux**. Exporter / importer le JSON si besoin. Si Safari/iOS purge son stockage, seul un export antérieur peut restaurer le travail.

## Mise en ligne sur GitHub Pages (dépôt public)

1. Créer un nouveau dépôt GitHub **public**, par exemple `mon-cap` ; ne pas importer de sauvegardes ou de données réelles d'Ethan.
2. Importer tous les fichiers de ce dossier, y compris `.github/workflows/pages.yml` (l'ensemble du ZIP est prêt).
3. Dans le dépôt : **Settings → Pages → Build and deployment → Source → GitHub Actions**.
4. Dans **Actions**, attendre le succès du workflow « Déployer MON CAP sur GitHub Pages ». L'application sera disponible à l'URL indiquée par GitHub, généralement `https://IDENTIFIANT.github.io/mon-cap/`.
5. Ouvrir **l'URL effective** dans Safari de l'iPhone du jeune puis choisir **Sur l'écran d'accueil**.
6. En cas de mise à jour : envoyer les nouveaux fichiers dans la branche `main`. Un bandeau proposera de recharger l'application lorsqu'un nouveau service worker est prêt.

Le workflow exécute `actions/configure-pages`, `actions/upload-pages-artifact`, `actions/deploy-pages`. **GitHub Pages publie toujours les fichiers du site** : ils ne doivent contenir aucune information personnelle, code secret ou données issues du carnet.

## Travailler en local pour des tests PWA

Dans le dossier du projet :

```bash
python3 -m http.server 8000
```

Puis ouvrir `http://localhost:8000/` dans Chrome/Firefox (service worker autorisé). Depuis un iPhone, utiliser une URL HTTPS publiée ; `http://adresse-ip:8000` ne permet pas l'installation PWA complète.

## Fichiers

- `index.html` : structure du site.
- `app.js` : 15 questions, synthèses, carnet et export JSON / Markdown.
- `styles.css`, `theme-v2.css`, `workflow-v3.css`, `pwa-v4.css` : interface.
- `pwa-v4.js` : aide à l'installation, statut réseau, mises à jour.
- `sw.js` : cache hors ligne des fichiers statiques.
- `manifest.webmanifest`, `icons/` : configuration et icônes d'installation.
- `.github/workflows/pages.yml` : publication automatique sur GitHub Pages.

## Sauvegarde iPhone

Dans **Mon carnet**, toucher **Télécharger ma sauvegarde**. Si le partage iOS s'ouvre, choisir **Enregistrer dans Fichiers** ; sinon, récupérer le JSON dans les téléchargements Safari. Vérifier que le fichier existe et le conserver dans un dossier privé. Pour restaurer, choisir **Restaurer une sauvegarde** et sélectionner le fichier JSON.

Les réponses restent accessibles hors ligne, mais pas les liens externes (ChatGPT). Aucun score ni diagnostic n'est attribué. À un mineur, présenter la réflexion comme personnelle et non comme un test ou un outil de contrôle.