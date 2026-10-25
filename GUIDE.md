# Mettre en ligne le portfolio BKD et son admin

Tout est gratuit. Compte à prévoir : GitHub (gratuit) et Cloudflare (gratuit, sans carte bancaire en principe).

## 1. Mettre le site sur GitHub
1. Crée un compte sur github.com, puis un nouveau dépôt **public** (ex. `portfolio`).
2. Envoie-y **tout le contenu du dossier** (index.html, admin/, content/, images/, .nojekyll). Sur GitHub : *Add file › Upload files*, glisse les dossiers.
3. Dans le dépôt : *Settings › Pages › Deploy from a branch › main / (root)*. Au bout d'une ou deux minutes, ton site est en ligne à l'adresse `https://TON-PSEUDO.github.io/portfolio/`.

## 2. Régler l'admin
Ouvre `admin/config.yml` sur GitHub (icône crayon) et remplace :
- `repo:` par `TON-PSEUDO/portfolio`
- `base_url:` par l'adresse du relais de connexion (étape 3)

## 3. Relais de connexion GitHub (une seule fois)
Sur GitHub Pages, la connexion à l'admin passe par un petit relais gratuit sur Cloudflare Workers : **Sveltia CMS Authenticator** (fonctionne avec Decap CMS). Suis le README du projet `sveltia/sveltia-cms-auth` : déploiement du Worker, création d'une « OAuth App » GitHub (callback = `https://TON-WORKER.workers.dev/callback`), puis ajout de `GITHUB_CLIENT_ID`, `GITHUB_CLIENT_SECRET` et `ALLOWED_DOMAINS` (= `TON-PSEUDO.github.io`) dans les variables du Worker.
Colle ensuite l'adresse du Worker dans `base_url:` (étape 2).

## 4. Utiliser l'admin
Va sur `https://TON-PSEUDO.github.io/portfolio/admin/` et connecte-toi avec ton compte GitHub. Il n'y a aucune création de compte : seuls les comptes ayant un droit d'écriture sur ton dépôt peuvent enregistrer.

Dans « Contenu du site » :
- **Sections** : ajoute (Services, Réalisations, À propos, Méthode, Tarifs, Section libre), supprime avec la corbeille, réordonne par glisser-déposer. Vider « Nom dans le menu » retire la section du menu.
- **Réalisations** : ajoute une réalisation, puis des images. **Une image = image seule, plusieurs = carrousel** (flèches, pastilles, glissement au doigt, clic pour agrandir).
- **Contact** : numéros, email, WhatsApp, réseaux sociaux.
Clique sur *Publier* : le site se met à jour en 1 à 2 minutes.

## À savoir
- Le dépôt est public : n'y mets rien de confidentiel.
- Active la double authentification sur ton compte GitHub.
- GitHub garde l'historique : en cas d'erreur, tu peux revenir en arrière (onglet *Commits*).
- Pour tester le site chez toi, ouvre-le via un petit serveur local ; en double-cliquant sur index.html, le navigateur bloque la lecture de `content/site.json`.
