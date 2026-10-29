# TAKATAK — Package de soumission Clover App Market

**Statut du document :** brouillon de préparation — rien n’a été publié ni soumis.  
**Préparé le :** 24 octobre 2026  
**Propriétaire du projet :** Matt, TAKATAK Marketing, Montréal  
**Assistance :** takatak.ca@gmail.com · +1 450-999-4999

## Ce qu’est TAKATAK, selon les sources locales

TAKATAK est le **tableau de bord d’agence et de gestion de marques** de Matt : un espace distinct par client/marque pour relier les actifs numériques, suivre les Pages et comptes, consulter les indicateurs et préparer le travail marketing sans mélanger les marques. Les notes des 21 et 22 octobre décrivent **takatak-v1 — “TAKATAK User Official Dashboard V1”**, une application Next.js/TypeScript avec Prisma/PostgreSQL, Supabase Auth/DB/Storage et Docker, déployable sur Vercel ou Coolify.

La règle d’architecture établie est stricte : **un espace distinct par client et par marque**. La seule vue regroupée documentée est celle du portefeuille, notamment Quadro Holdings, avec des espaces séparés par restaurant/emplacement. On2GO.ca et Délices d’Aden sont traités comme des marques individuelles en dehors de ce regroupement.

L’intégration Meta inspectée dans le code était réelle mais principalement en lecture : connexion Facebook OAuth2 + PKCE, liste des Pages, publications lues, indicateurs de Page, Instagram lié, comptes publicitaires et indicateurs Ads; jetons chiffrés et cloisonnés par client/marque; synchronisation incrémentale. Aucune implémentation de publication POST vers les Pages n’a été trouvée lors de cette inspection. Il ne faut donc pas présenter la publication automatique comme une fonction établie.

Pour Clover, ce package propose un **connecteur marchand en lecture** qui relie un établissement Clover au bon espace client TAKATAK et y apporte des indicateurs d’exploitation et de ventes. Les sources ne prouvent pas qu’une intégration Clover de takatak-v1 était déjà terminée; les contrats TAKATAK ↔ ON2GO Hub pour l’authentification unique, les droits, les événements d’usage et les analytiques agrégées étaient décrits comme un travail planifié. La fiche doit donc vendre le connecteur et le tableau de bord, sans prétendre que toutes les intégrations futures existent déjà.

### Sources

- `~/memory/2026-10-21.md` — takatak-v1, architecture, module Social et état de facturation historique
- `~/memory/2026-10-22.md` — registre de 67 espaces de connexion et cloisonnement par client/marque
- `~/workspace/sites-restaurants/foodhubca/docs/ON2GO_HUB_ECOSYSTEM.md` — TAKATAK Dashboard V1 comme plan de contrôle; contrats planifiés
- `~/workspace/sites-restaurants/foodhubca/BRAND.md` — identité GROUPE TAKATAK / TAKATAK et positionnement

## Nom de l’application

**TAKATAK**

## Slogan / Tagline

**FR :** Tous tes établissements, tes marques et tes résultats — chacun dans son espace.  
**EN :** Every location, brand and result — each in its own workspace.

## Description

### Français

TAKATAK est le tableau de bord de gestion pour les entreprises qui exploitent plusieurs marques, établissements ou Pages. Chaque client et chaque marque gardent leur propre espace : les accès, les données et les rapports ne sont pas mélangés pour économiser un abonnement ou simplifier la gestion.

Pour un marchand Clover, l’application relie l’établissement autorisé au bon espace TAKATAK. Elle lit les renseignements du marchand, les données d’inventaire nécessaires aux rapports et les commandes/paiements en mode lecture afin de présenter une vue claire de l’activité : ventes, commandes, articles et écarts à vérifier. Le marchand ou l’agence autorisée garde le contrôle des changements dans Clover; TAKATAK ne modifie ni les prix, ni le menu, ni les commandes dans le périmètre de base de ce package.

Fonctions du tableau de bord documentées ou proposées pour cette application Clover :

- espaces séparés par client, marque et emplacement;
- connexion d’un établissement Clover au bon espace;
- vue portefeuille pour un propriétaire de plusieurs établissements, sans fusion des données;
- indicateurs de commandes et de paiements en lecture;
- inventaire et état des actifs numériques reliés à la marque;
- suivi des Pages, profils et comptes connectés lorsque le client active ces modules;
- indicateurs sociaux et publicitaires en lecture lorsque les autorisations du client sont en place;
- brouillons assistés par IA soumis à l’approbation humaine, sans publication automatique présentée comme acquise;
- alertes sur les comptes non reliés, les données périmées et les écarts à vérifier.

### English

TAKATAK is the management dashboard for businesses operating multiple brands, locations or Pages. Each client and brand keeps its own workspace: access, data and reports are not merged merely to save a subscription or simplify administration.

For a Clover merchant, the app connects the authorized establishment to the correct TAKATAK workspace. It reads merchant information, the inventory data needed for reporting, and orders/payments in read-only mode to present a clear view of activity: sales, orders, items and exceptions to review. The merchant or authorized agency remains in control of changes in Clover; TAKATAK does not change prices, menus or orders within the base scope of this package.

Dashboard capabilities documented or proposed for this Clover app:

- separate workspaces by client, brand and location;
- connection of a Clover establishment to the correct workspace;
- portfolio view for a multi-location owner without merging underlying data;
- read-only order and payment indicators;
- inventory of the brand’s connected digital assets;
- tracking of connected Pages, profiles and accounts when the client enables those modules;
- read-only social and advertising insights when the client’s authorizations are in place;
- AI-assisted drafts subject to human approval, with no claim that automated publishing is already established;
- alerts for unconnected accounts, stale data and exceptions to review.

## Catégorie proposée

- **Primaire :** Business Management
- **Secondaires :** Reports & Analytics; Customer Engagement
- **Verticaux :** Quick Service Restaurant; Full Service Restaurant; Retail (si Clover le permet pour les clients multi-marques)

**À valider :** libellés exacts disponibles dans le portail Clover.

## Fonctions détaillées et état

| Fonction | État | Commentaire |
|---|---|---|
| Espace distinct par client/marque | Établi | Règle d’architecture centrale |
| 67 espaces de connexion préparés au registre du 2026-10-22 | Établi historiquement | Ne pas présenter ce nombre comme un nombre actuel de clients sans vérification |
| Connexion Meta en lecture et indicateurs | Établi dans l’inspection du code | Publication non prouvée; ne pas la promettre |
| Jetons chiffrés et cloisonnés | Établi dans l’inspection du code | À revalider sur l’environnement de production |
| Agent IA avec approbation humaine | Établi comme principe/service dans les notes | Sorties à réviser par une personne |
| Connecteur Clover | **Proposition de ce package** | Aucune preuve locale d’une intégration takatak-v1 terminée |
| SSO/entitlements TAKATAK ↔ ON2GO Hub | Planifié dans les contrats d’écosystème | Ne pas décrire comme livré |
| Modification de menu ou de prix Clover | Hors périmètre | Aucune permission d’écriture demandée au lancement |

## Permissions Clover demandées — lecture seulement au lancement

| Permission | Accès | Justification |
|---|---:|---|
| Merchant | Read | Identifier le marchand et l’établissement autorisés et les rattacher au bon espace client, sans mélanger les marques ni les succursales. |
| Inventory | Read | Lire les catégories et articles nécessaires aux rapports d’assortiment, aux vérifications de présence et à l’inventaire des actifs du menu. Aucune création ni modification. |
| Orders | Read | Calculer les volumes et statuts de commandes affichés dans le tableau de bord et repérer les écarts à vérifier. |
| Payments | Read | Afficher les totaux et rapprochements de paiements en lecture pour les rapports de ventes. TAKATAK ne traite pas le paiement et ne rembourse pas dans cette application. |

### Permissions expressément non demandées au lancement

- Inventory Write
- Orders Write
- Payments Write
- Customers Write

Toute écriture future devra correspondre à une fonction précise approuvée par Matt et par le marchand, puis être ajoutée par une nouvelle justification.

## Tarification — PROPOSITION SEULEMENT

**Proposition interne à confirmer par Matt :**

- essai de 14 jours;
- **CAD $49 par mois, par espace marchand/client connecté**;
- modules Social, publicitaires ou IA avancée : tarification séparée seulement si Matt décide de les vendre dans l’application Clover.

**Ne pas reprendre comme prix Clover les anciens montants du module Social de takatak-v1 observés dans les notes.** Ils étaient historiques, liés à un autre périmètre et à une facturation qui n’avait pas été conclue en production. Aucun prix n’est approuvé pour publication à ce stade.

## Assistance

- **Courriel :** takatak.ca@gmail.com
- **Téléphone :** +1 450-999-4999
- **Langues :** français et anglais
- **Heures d’assistance :** À CONFIRMER
- **Page d’assistance :** À CONFIRMER

## Checklist de soumission

- [x] Positionnement d’agence et règle « un espace par marque » documentés
- [x] Description FR et EN préparée
- [x] Permissions limitées à la lecture et justifiées
- [x] Script vidéo FR préparé
- [x] Politique de confidentialité FR/EN préparée en brouillon
- [x] Conditions d’utilisation FR/EN préparées en brouillon
- [ ] Matt confirme que l’application Clover publique s’appelle simplement « TAKATAK »
- [ ] Périmètre de lancement du connecteur Clover codé et testé en sandbox
- [ ] Décision : tableau de bord pour marchands tiers, outil réservé aux clients TAKATAK, ou les deux
- [ ] Prix et essai confirmés
- [ ] Entité légale, adresse et responsable Loi 25 confirmés
- [ ] Textes juridiques approuvés
- [ ] Captures d’écran sans données réelles de clients
- [ ] Vérification que les jetons sont chiffrés et cloisonnés dans l’environnement soumis
- [ ] Aucune promesse de publication Meta automatique dans la fiche

## À CONFIRMER

1. **Public cible :** tout marchand Clover peut-il installer TAKATAK, ou l’application est-elle réservée aux clients accompagnés par l’agence?
2. **Nom exact :** « TAKATAK » seul suffit-il dans l’App Market, ou faut-il un suffixe distinctif approuvé par Matt?
3. **Connecteur Clover :** la lecture Merchant/Inventory/Orders/Payments est-elle le bon périmètre de lancement?
4. **Modules inclus :** les indicateurs Meta/Instagram/Ads font-ils partie de cette fiche Clover ou restent-ils un produit distinct?
5. **Publication sociale :** exclure complètement la publication tant qu’elle n’est pas implémentée et testée.
6. **IA :** quels fournisseurs d’IA, quelles données peuvent leur être envoyées et quelles sorties exigent une approbation humaine documentée?
7. **Prix :** valider ou remplacer la proposition de CAD $49/mois par espace.
8. **Rôles :** agence, propriétaire, gestionnaire et personnel — qui peut relier ou déconnecter Clover?
9. **Entité légale et responsable Loi 25.**
10. **Preuve de production :** environnement, chiffrement, journaux et séparation des espaces à démontrer à Clover si demandé.
