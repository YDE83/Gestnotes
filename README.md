# GestNotes autonome : mise en service (environ 30 minutes)

## 1. Base de données (Supabase, gratuit)
1. Créez un compte sur supabase.com, puis un projet (choisissez la région la plus proche).
2. Ouvrez SQL Editor, collez le contenu de `schema.sql`, cliquez sur Run.
3. Project Settings > API : copiez l'URL du projet et la clé « anon public ».
4. Authentication > Providers > Email : désactivez « Confirm email » si vous voulez que les comptes fonctionnent sans confirmation.

## 2. Configuration de la page
Dans `index.html`, remplacez `SUPABASE_URL` et `SUPABASE_KEY` (tout en haut du script) par vos deux valeurs.
La clé anon est publique par conception : la sécurité repose sur les règles d'accès du `schema.sql`.

## 3. Hébergement gratuit de la page (Cloudflare Pages)
Créez un dépôt GitHub avec le contenu de ce dossier, puis sur Cloudflare Pages : Create > Pages > connecter le dépôt, sans commande de build, dossier de sortie `/`.

## 4. Premier lancement
1. Ouvrez le site et cliquez sur « Créer un compte » : **le premier compte devient administrateur**.
2. Onglet Administration : créez l'année, les classes, les matières, ajoutez les élèves, attribuez les matières aux enseignants. Onglet Conseil de classe : saisissez absences, conduite et observation de chaque élève par trimestre (elles apparaissent sur le bulletin trimestriel).
3. Les enseignants créent leur compte, puis vous leur attribuez classe et matière (« Attribuer une matière »). Ils ne voient et ne modifient que leurs notes.

## 5. Éviter la pause Supabase
Dans votre dépôt GitHub : Settings > Secrets and variables > Actions, ajoutez `SUPABASE_URL` et `SUPABASE_KEY` (même valeurs). Le fichier `.github/workflows/keepalive.yml` enverra une requête tous les 3 jours.

## 6. Sauvegardes
Administration > « Exporter toutes les données » : faites-le au moins une fois par mois et à la fin de chaque trimestre. Conservez le fichier ailleurs que sur l'ordinateur de l'école.
