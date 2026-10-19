# Suivi des pages — Refonte MANTAS 86 (saison 2026)

> Recensement de **toutes les pages** du site live https://mantas86.vpdive.com et de leur
> statut dans la refonte « épuré / moderne ». Objectif final : chaque page stylée et
> uniformisée à la charte de l'accueil, en HTML collable dans l'éditeur VP Dive.
>
> - **Livrables finalisés** → dossier [`2026/`](2026/) (pages prêtes à coller).
> - **Exemples / composants de démo** → dossier [`exemples/`](exemples/) : maquettes de style des
>   composants VP Dive (Documents, Trombinoscope, Formulaire, Liste d'articles, Grille vidéos) +
>   composants maison (`choix-boutons.html`, `table.html`, `table-documents.html`). Non destinés au
>   site tel quel, servent de référence de composants. (Les démos `choix-hero-*` ont été supprimées
>   le 2026-08-13 — elles servaient juste à choisir les images de hero.)
> - **Référence de style** → `2026/accueil.html` (ex-`preview.html`). Charte détaillée dans `CONTEXTE-PROJET.md`.
> - Ménage 2026-08-10 : `scrap-*.html`, `*.bak.html`, anciens doublons racine (mentions-legales, table*, accueil-nouveau)
>   SUPPRIMÉS. `preview.html` conservé à la racine comme maquette de référence.
>
> Dernière mise à jour : 2026-08-11 (chantier B : liens-utiles fusionnée dans infos-pratiques ;
> formation-n1 + rifap + les-detendeurs déportées dans formation.html § « Ressources en ligne »).

## Règles de style à appliquer sur CHAQUE page

Consignes permanentes — valables pour toute page restylée (livrable `2026/`) :

1. **Bannière hero obligatoire** en haut de chaque page, sur le modèle du hero de `2026/accueil.html` :
   image de bannière en fond (`background-size:cover`, `background-position:center`, `aspect-ratio` = ratio réel
   de l'image) + overlay dégradé bleu, puis, centrés : **petit trait** `<hr class="divider-sm">` cyan,
   **titre** `<h1>` blanc en majuscules, **sous-titre** blanc, et **bouton(s) optionnel(s)**.
2. **Mêmes couleurs partout** : bleu foncé `#062D63`, cyan `#20C4D8`, bleu médian `#0E66A9`,
   gris texte `#5a6a7a` / `#8a97ab`, ombre douce `0 10px 30px rgba(6,45,99,.08)`.
   Titres en Montserrat, corps en Roboto.
3. **Priorité aux classes CSS existantes de VP Dive** (thème Novi / Bootstrap) ; le **CSS inline
   n'est utilisé que lorsqu'aucune classe n'existe** (rappel : les utilitaires d'espacement Bootstrap
   `.mt-*/.mb-*/.py-*` sont désactivés dans le thème → l'espacement passe forcément par de l'inline ;
   les utilitaires flex, eux, sont actifs). Détails dans `CONTEXTE-PROJET.md` §3.

## Légende

**Statut**
- ✅ **Fait** — stylé à la charte, dans `2026/`, prêt à coller.
- 🟡 **Partiel** — stylé et utilisable, mais un point reste à revoir (voir note).
- 🟠 **À réaligner** — présent en local mais pas (encore) à la charte.
- ⬜ **À faire** — contenu scrapé, restylage non commencé.
- 📄 **À faire** — pas encore restylé (les scraps bruts d'origine ont été supprimés le 2026-08-10 ;
  pour retraiter une page, re-scraper le contenu depuis le live V5 en session connectée).
- ⏸️ **En pause** — volontairement mise de côté pour le moment (à reprendre plus tard).

**Personnalisable ?** — colonne à renseigner par l'utilisateur :
- `oui` — on peut restyler librement (contenu statique éditable dans VP Dive).
- `non` — contenu **dynamique** VP Dive (agenda, carte, trombinoscope, liste d'articles…) : le rendu est généré par la plateforme, on ne peut pas coller notre HTML → on ne touche pas / on adapte seulement autour.
- `partiel` — une partie statique restylable + une partie dynamique intouchable.
- `?` — à décider ensemble.

---

## Pages principales (menu du site)

| Page | URL live | Fichier livrable (`2026/`) | ~~Scrap~~ (supprimé) | Statut | Personnalisable ? |
|---|---|---|---|---|---|
| Accueil | `/w/accueil` | `accueil.html` | — | ✅ Fait (référence) | oui |
| Baptême | `/w/bapteme` | `bapteme.html` | `scrap-bapteme.html` | 🟡 Partiel | partiel |
| Qui sommes-nous ? | `/w/qui-sommes-nous-` | `qui-sommes-nous.html` | `scrap-qui-sommes-nous.html` | ✅ Fait | oui |
| Infos pratiques | `/w/infos-pratiques` | `infos-pratiques.html` | `scrap-infos-pratiques.html` | ✅ Fait | oui |
| Formation | `/w/formation-2` | `formation.html` | `scrap-formation.html` | ✅ Fait | oui |
| Nos activités | `/w/nos-activites` | `nos-activites.html` | `scrap-nos-activites.html` | 🟡 Partiel | oui |
| Voyages | `/w/voyages` | — | `scrap-voyages.html` | ⏸️ En pause (non traitée pour le moment) | oui |
| Actus | `/w/actus` | — | `scrap-actus.html` | 📄 À faire | non |
| Contact | `/w/contact-1` | `contact.html` | `scrap-contact.html` | 🟡 Partiel | partiel |
| Comité | `/f/office` | — | — (non scrapé) | ⬜ À faire | non |
| Mentions légales | `/w/mentions-legales` | `mentions-legales.html` | — | ✅ Fait (sans hero) | oui |

## Composants / tableaux (intégrés dans des pages, pas dans le menu)

| Élément | Rattaché à | Fichier livrable (`2026/`) | Statut | Personnalisable ? |
|---|---|---|---|---|
| Tableau des tarifs 2026/2027 | Infos pratiques / page dédiée | `table.html` | ✅ Fait | oui |
| Tableau des documents PDF | Infos pratiques / page dédiée | `table-documents.html` | ✅ Fait | oui |

---

## ✅ Correctifs transverses (remontés + FAITS le 2026-08-10)

Appliqués sur les 7 pages (accueil + 6 secondaires), reportés dans VP Dive par l'user :
1. ✅ **Titre hero** remis en poids fin (font-weight:300) — plus de gras.
2. ✅ **Hauteur hero** uniformisée (min-height:340px identique, avec ou sans bouton).
3. ✅ **Overlay bleu** présent et vérifié partout.
4. ✅ **Rendu mobile** validé (heros, formulaires + grilles = responsive natif `col-*`, galerie).
5. ✅ **Centrage hero** corrigé : suppression du `width:100%` (décentrait), remplacé par un wrapper flex maison (centrage H+V fiable car `.row` du thème = display:block). Seul autre bloc modifié hors hero : la **galerie de qui-sommes-nous** (grille CSS → flex-wrap pour l'empilement mobile).

## Nouvelles pages découvertes en V5 (scrap 2026-08-10, session connectée)

Le site est passé en **V5** (URLs `/v5/public/<slug>`). 16 pages n'existaient pas dans l'inventaire du 07/08.
À trier avec l'user : lesquelles méritent un restylage (beaucoup ne sont que des listes de PDF).

| Nouvelle page V5 | Slug | Type de contenu |
|---|---|---|
| Liens utiles | `liens-utiles` | raccourcis pratiques (3 liens) — ✅ **DONE — FUSIONNÉE dans infos-pratiques** (section 3bis, 3 cartes-photo à la charte) |
| Photos | `photos` | galerie photos (albums) — ✅ **FAIT** (`2026/photos.html`) : hero + intro + grille 2×2 cartes-photo (Le Rubis, Le Togo, Fréjus 2023, Hendaye 2023) + zoom lightGallery au clic (`data-lightgallery` conservé) |
| Videos | `videos` | vidéos du club — ✅ **HABILLÉE** (`2026/videos.html`) : hero + intro SEULEMENT (à insérer au-dessus). Le **module vidéo est DYNAMIQUE** (extraction miniature YouTube + lecteur lightGallery) → laissé intact, NE PAS coller de grille statique. Maquette de style de la grille dans `exemples/demo-videos-style.html`. |
| Quiz | `quiz` | quiz bio sous-marine — ✅ **FAIT** (`2026/quiz.html`) : hero « Quiz Bio » + intro + **grille de 5 cartes-quiz à la charte** (couverture image + badge « ? Quiz » cyan + titre-lien vers le quiz `target=_parent` + sous-titre). 4 quiz CIBPL cliquables + « ASTER QUIZZ » reproduit **sans lien** (fidèle à l'original, carte non cliquable). Cartes de même hauteur (flex stretch). |
| Sur le WEB | `sur-le-web` | liens bio externes — ✅ **FAIT** (`2026/sur-le-web.html`) : page « Biologie Sous Marine ». Hero + intro + **grille de 9 cartes-vidéos à la charte** (couverture image + badge lecture cyan + titre-lien YouTube `target=_blank` + auteur + description), cartes de même hauteur (flex stretch). 2 cartes sans image (Les requins / Dessus-Dessous) = couverture dégradé de marque + icône. Contenu réel scrapé (session connectée, iframe srcdoc). HTML statique côté VP Dive. |
| Notes Bio de Dominique | `notes-bio-de-dominique` | ~48 fiches PDF bio |
| Documents annexes | `documents-annexes` | docs bio annexes |
| Soirées Bio | `soirees-bio` | ~38 PDF par thème |
| Formation N1 | `formation-n1` | renvoi cours FFESSM en ligne — ✅ **DÉPORTÉE dans formation.html** (section « Ressources en ligne ») |
| RIFAP | `rifap` | extrait MFT/livret — ✅ **DÉPORTÉE dans formation.html** (section « Ressources en ligne ») |
| Les détendeurs | `les-detendeurs` | renvoi cours FFESSM — ✅ **DÉPORTÉE dans formation.html** (section « Ressources en ligne ») |
| Membres | `membres-1` | espace docs membres (~52 fichiers / 9 dossiers) — ✅ **MAQUETTE COMPLÈTE** (`2026/membres.html`) pour l'équipe VP Dive : hero (image fond sableux) + intro + **tableau documents NAVIGABLE à la charte** (liste dossiers → clic ouvre le dossier → retour, onclick inline) + **tableau « Liens & références »** stylisé (4 liens statiques). Simulation statique du contenu au 2026-08-11 à intégrer côté VP Dive. |
| Comité Directeur | `comite-directeur` | espace docs CoDir (≠ page « Comité » trombinoscope) — ✅ **HABILLÉE** (`2026/comite-directeur.html`, jumelle de Membres) : hero + intro + tableau docs = **MOCK de style** (données fictives, navigation multi-niveaux illustrée) car dynamique/gros volume + tableau « Liens & références » (2 liens Honorabilité réels) |
| Encadrants | `encadrants` | espace docs encadrants (~196 fichiers) — ✅ **HABILLÉE** (`2026/encadrants.html`, jumelle Membres/CoDir) : hero + intro + tableau docs = MOCK de style (navigation multi-niveaux) + tableau « Liens & références » avec **10 liens réels** (6 Google Sheets suivi/surveillance + MFT + honorabilité + Charte 50m) |
| Gonflage | `gonflage` | PDF tours de gonflage par saison — ✅ **HABILLÉE** (`2026/gonflage.html`) : hero + intro + **2 blocs distincts** : (a) carte « à la une » = 1 lien **Google Sheets** planning saison + (b) tableau **archives PDF** (composant `documents-variant-8`, dynamique). Mock de style. |
| Inscription (club) | `/w/inscription` | page de contenu — ✅ **FAIT** (`2026/inscription.html`) : hero + bouton Tarifs + 2 parcours (nouveau / déjà connecté) en cartes de même hauteur, aperçus recréés en HTML (bouton « Connexion », encart « Campagne d'adhésion disponible »). |
| Connexion / Inscription site | `/login` | **page plateforme** (non intégrable) — ✅ maquette de style `exemples/connexion-vpdive.html` (états initial / erreur / chargement) pour VP Dive. |
| Politique de confidentialité | `politique-de-confidentialite` | **VIDE en V5** (contenu non migré) |

**Décisions de tri (2026-08-10)** — pages V5 à TRAITER : ~~`liens-utiles`~~ (✅ fusionnée dans
infos-pratiques), ~~`photos`~~ (✅), ~~`formation-n1`~~ ~~`rifap`~~ ~~`les-detendeurs`~~ (✅ déportées dans
formation.html), ~~`sur-le-web`~~ (✅ page Biologie Sous Marine). Pages LAISSÉES tel quel (espaces documentaires dynamiques /
listes de PDF) : notes-bio-de-dominique, documents-annexes, soirees-bio, membres-1, comite-directeur,
encadrants, gonflage, videos. (`quiz` finalement ✅ TRAITÉE.) `politique-de-confidentialite` = laissée vide pour l'instant.

Pages connues confirmées en V5 (contenu stable) : accueil, bapteme, qui-sommes-nous-, infos-pratiques,
formation-2, nos-activites, comite (trombinoscope), actus, voyages, contact-1, mentions-legales-1.
Formulaires présents : `bapteme`, `contact-1`.

## Notes / points d'attention

- **✅ Maquettes de style des composants DYNAMIQUES VP Dive** (dossier `exemples/`, fichiers autonomes
  `<style>` + FontAwesome CDN, à remettre à l'équipe VP Dive — chacun avec un bloc « Note pour l'équipe ») :
  - `table-documents-vpdive.html` — plugin `template="documents"` : **2 vues sur la même page** (refonte
    2026-08-13, fidèle au vrai mécanisme `data-depth-paths`/`data-nav-paths`) → vue RACINE (liste dossiers,
    bouton « Ouvrir » bleu) qui bascule in-place vers vue DOSSIER (fil d'Ariane pour remonter + fichiers,
    bouton « Télécharger » cyan). Données fictives (mock allégé). Colonnes Type/Nom/Action.
  - `team-members-vpdive.html` — **Trombinoscope** (`team-members`) : grille `col-lg-3`, avatar cerclé +
    nom + pastille rôle + lien Contacter. Données **fictives** (avatars silhouette maison, 0 dépendance externe).
  - `formulaire-vpdive.html` — **Formulaire** (`rd-mailform`) : 2 colonnes nom/prénom + email/tél, message,
    honeypot masqué, zone captcha `cap-widget`, bouton cyan. Labels flottants (focus cyan). Structure fidèle
    (action `/f/contactForm`, contraintes @Email/@Numeric, form_ts).
  - `articles-vpdive.html` — **Liste d'articles** (page Actus) : grille 2 col, vignette gauche + titre/extrait/
    date, badge « Brouillon » optionnel, lien « Lire ». Données **fictives** (images de démo Unsplash).
  - (déjà existant) `demo-videos-style.html` — grille du module vidéo (miniatures YouTube).


- **Nos activités (✅ FAIT — 2026-08-11)** : carousel Owl **SUPPRIMÉ** → remplacé par une **grille de 4
  cartes-photo maison** (Piscine, Fosse de Civaux, Saint-Lin, Roussay) en `col-sm-6` (2×2 desktop,
  1 col mobile), image de fond + overlay dégradé bleu permanent + étiquette type de spot cyan + titre
  Montserrat blanc + lien « Découvrir → » cyan. Plus de JS, tout visible sur mobile, plus de biseau vert.
  **Les 4 pages de spots liées sont FAITES** (✅ 2026-08-11) : `saint-lin.html` (hero + Le site + Organisation
  des sorties [2 cartes] + galerie 6 photos légendées lightGallery + plan), `roussay.html` (hero + Le site +
  3 cartes Bon à savoir + plan), `piscine.html` (hero + 3 cartes créneaux + charte 50m + matériel/image),
  `civaux.html` (hero + présentation + image ; carousel Owl 1-image supprimé).

- **Infos pratiques (✅ Fait)** : hero + inscription/docs + accès & horaires + carte à la charte.
  Les onglets du thème (datés + état actif cassé par l'inline) ont été **remplacés par 3 mini-cartes**
  100% inline (icônes fa du thème : fa-life-ring / fa-dashboard / fa-graduation-cap, à la charte).
  Le tableau de PDF n'est PAS un doublon (validé par l'user) → conservé tel quel.

- **Qui sommes-nous (🟡 Partiel)** : hero + à propos (texte + **galerie MOSAÏQUE** 1 grande + 2 petites,
  paysages cadrés via object-fit:cover + **zoom lightGallery** au clic — `data-lightgallery="group"` sur
  la grille, chaque photo dans `<a data-lightgallery="item" href="grand-format">`. lightGallery ne dépend
  PAS d'isotope, donc on n'utilise PAS `gallery-justify` qui cassait le rendu des paysages en barres
  verticales) + bureau + activités + texte « Dominique » (prénoms en gras #062D63). Composant dynamique
  conservé : **trombinoscope `team-members`** (14 membres) → **À TESTER VP Dive** (liste régénérée +
  zoom lightGallery initialisé par la plateforme). Cartes « activités » = mini-cartes charte.
  Pour + de photos : ajouter un `<a data-lightgallery="item">` dans la grille.

- **Baptême (🟡 Partiel)** : hero + présentation (texte + image) + **formulaire de demande** à la charte.
  Le `<form class="rd-mailform">` VP Dive est **conservé intact** (action `/f/contactForm`, champs
  name/phone/message/email, honeypot + `form_ts` + script anti-spam, widget captcha `<cap-widget>`) —
  seul l'habillage (carte blanche) + le bouton (cyan inline) ont été restylés. → **À TESTER dans VP Dive** :
  labels flottants, validation, envoi et captcha sont initialisés par le JS de la plateforme.

- **Contact (🟡 Partiel)** : hero + **formulaire de contact** (rd-mailform conservé intact : action,
  champs name/last-name/email/phone/message, honeypot + form_ts + captcha `<cap-widget>` ; bouton cyan)
  + carte « Votre interlocuteur » (J.-P. Marin — refaite en carte statique charte, le composant
  team-members-variant-4 d'origine n'avait qu'un membre codé en dur). → **À TESTER dans VP Dive**
  (validation/envoi/captcha initialisés par la plateforme).

- **Menu obsolète dans l'accueil** : le menu de `accueil.html` date d'avant une refonte du site.
  Écarts à corriger : `News → Actus`, `Sorties/voyages/Stages → Voyages`, ajout de « Nos activités »
  en page dédiée, et `Formation` passé de `/w/formation` à `/w/formation-2`.
- **Formulaires** (Baptême, Contact) : contiennent un widget captcha `cap-widget` + un honeypot
  générés par VP Dive → probablement `partiel` (on restyle l'habillage, pas le mécanisme).
- **Comité** (`/f/office`) : page de type `/f/` = fonctionnalité dynamique VP Dive (trombinoscope) →
  a priori `non` personnalisable, à confirmer.
- **Actus** (`/w/actus`) : liste d'articles alimentée dynamiquement → à confirmer si `non` ou `partiel`.
