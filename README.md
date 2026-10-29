# TAKATAK

**App ID Clover (production) :** `F4TMP23FM7K5M`
**Développeur :** TAKATAK (compte développeur Clover 9KJ25ATT15TTW)
**État au portail :** brouillon (draft) — rien de soumis.
**Dépôt :** ⚠️ AUCUN dépôt GitHub dédié — dossier local seulement (voir DEPLOY.md).

## Ce que fait l'app

Tableau de bord d'agence et de gestion de marques : un espace distinct par client/marque ; le connecteur Clover (lecture) relie chaque établissement au bon espace et y apporte ventes, commandes, articles et écarts. Jumeau sandbox : TAKATAK P8JGS60SV1R7W.

## Paliers (doctrine de prix de Matt, 2026-10-28)

Chaque app a SES propres paliers. Base = le nécessaire essentiel · Premium = plus d'avantages · VIP = le full kit, tout ce que Clover offre pour la catégorie.

- **Base 50 $/mois** — connexion d'un établissement Clover à son espace ; indicateurs de ventes/commandes en lecture ; état de l'inventaire ; alertes « compte non relié / données périmées ».
- **Premium 100 $/mois** — + vue portefeuille multi-établissements sans fusion des données ; écarts à vérifier (commandes sans paiement, ruptures fréquentes) ; suivi des actifs numériques reliés à la marque.
- **VIP 150 $/mois** — full kit : plan de contrôle complet de la suite — état de toutes les apps TAKATAK installées (webhooks App), facturation et usage consolidés, indicateurs sociaux/publicitaires en lecture, brouillons IA approuvés par un humain.

Prix facturés via les plans d'abonnement du Clover App Market (à créer au portail — voir DEPLOY.md).

## Permissions Clover visées

Merchant R · Inventory R · Orders R · Payments R (tout en lecture)

## Structure

- `docs/listing/` — fiche marketplace (description FR/EN) et textes légaux, depuis le package de soumission local (`~/workspace/clover-apps/`)
- `app/api/clover/` — points d'entrée webhook + OAuth (scaffold, même patron que Food Hub)
- `lib/clover/config.ts` — configuration par variables d'environnement (aucun secret dans le code)
- `config/app.config.json` — identité de l'app et paliers
- `DEPLOY.md` — ce qui reste à faire, étape par étape, pour la vague portail

## Le système unique TAKATAK

Cette application fait partie de la suite TAKATAK sur Clover : toutes les apps partagent le même dos d'événements (webhooks Clover), le même **client unique reconnu par son numéro de téléphone** (+ courriel), et les mêmes commandes et paiements Clover. Aucune app ne vit en silo : les données qu'elle produit alimentent les autres apps de la suite (voir « Clover API — Main Stuff — Robot Notepad », section 3, déposé au Drive Opérations et dans `~/workspace/clover-apps/`).

