# MANTAS 86 — Refonte du site (contexte projet)

> Fichier de reprise de contexte pour Claude Code. Résume le travail réalisé, les
> décisions prises et les contraintes techniques du site du **Club Mantas Plongée
> (MANTAS 86)**, club FFESSM de Poitiers, hébergé sur la plateforme **VP Dive**.
> Dernière mise à jour : 2026-08-07.

---

## 1. Contexte général

- **Club** : Club Mantas Plongée (MANTAS 86), association loi 1901, FFESSM, Poitiers, fondé en 1989.
- **Site actuel** : https://mantas86.vpdive.com — construit avec **VP Dive**, une plateforme
  builder pour clubs de plongée (thème basé sur **Novi / Bootstrap 4.0.0-beta**).
- **Objectif** : refonte « épurée / moderne » de la page d'accueil + pages annexes
  (mentions légales, tarifs, documents), à coller dans l'éditeur VP Dive.
- **Langue** : tout le contenu est en français.

### Coordonnées / infos légales réelles du club
- Siège : 57 rue de la Ganterie, 86000 Poitiers
- Tél : 07 63 90 73 06 · Email : jp.mar1@wanadoo.fr
- Président / directeur publication : **Jean-Paul MARIN**
- RNA : **W863001943** · Agrément J&S : 419 86 905 · Affiliation FFESSM : 02860158
- SIRET : 807 790 647 00018
- Instagram : @club_mantas_plongee · Facebook : profile.php?id=61551041642656
- Hébergeur : **VP Dive** (www.vpdive.com) — coordonnées légales complètes NON encore récupérées (à compléter pour conformité LCEN).

---

## 2. Fichiers du repo

| Fichier | Rôle |
|---|---|
| `preview.html` | **Maquette de travail principale** — page d'accueil refondue (hero, stats, activités, parcours, baptême, infos pratiques, prochaines activités, réseaux, carte). Sert à visualiser le rendu localement. |
| `mentions-legales.html` | Page mentions légales stylée (à coller dans VP Dive). Conforme LCEN/RGPD + section cookies. |
| `table.html` | Tableau **tarifs saison 2026/2027** stylé (carte arrondie, en-tête dégradé bleu). |
| `table-documents.html` | Tableau **documents PDF à télécharger** stylé (même look que table.html). |
| `accueil-nouveau*.html` | Anciennes versions / backups (ne pas toucher sauf demande). |
| `banniere.png` | Bannière hero (raie manta), **1983×793 px** (ratio 2.5:1). |
| `assets/css/` | `bootstrap.css` (v4.0.0-beta), `style.css` (thème Novi, 865 Ko), `novi.css`. |
| `assets/js/` | `jquery.min.js`, `core.min.js`, `script.js` (contient l'init Owl). |

Chaque fichier HTML autonome reprend le même `<head>` que `preview.html` (mêmes 3 CSS +
jquery) pour un rendu local fidèle. Un commentaire en tête indique quoi coller dans VP Dive
(en général : l'intérieur de `<section>…</section>`).

---

## 3. Contraintes techniques VP Dive / thème (IMPORTANT)

Ces points ont été **vérifiés dans les CSS/JS** et conditionnent toutes les décisions :

1. **Utilitaires de spacing Bootstrap DÉSACTIVÉS** : les classes `.mt-*`, `.mb-*`, `.py-*`,
   `.p*-*` sont **toutes commentées ligne par ligne** dans `bootstrap.css` (fichier en
   retours chariot `\r`). Elles n'ont AUCUN effet. → l'espacement doit passer par du
   **style inline** (`margin-top:60px` etc.).
2. **`offset-top-30`** : classe utilisée dans le HTML VP Dive mais **définie nulle part** → morte.
3. **Utilitaires flex ACTIFS** : `.d-flex`, `.align-items-center`, `.justify-content-*`,
   `.flex-column`, `.text-left/center`, `.align-self-center` fonctionnent (en `!important`).
4. **Pas de classe "carte" réutilisable** ni de couleurs de marque dans le thème → couleurs,
   ombres, dégradés, rayons = forcément inline.
5. **Conclusion inline** : on NE PEUT PAS réduire significativement le CSS inline avec les
   classes du thème sans changer le rendu. ~82% de l'inline (couleurs/marges/tailles/ombres)
   n'a aucun équivalent en classe. Un bloc `<style>` global serait la solution propre mais
   l'éditeur VP Dive risque de le stripper → non retenu.
6. **`custom.css` NON modifiable** côté VP Dive (indiqué dans un commentaire du HTML d'origine).

### Owl Carousel
- Le plugin **Owl** est présent (CSS dans `style.css`, JS dans `script.js`).
- **Auto-init** : `script.js` ligne ~31 fait `owl: $(".owl-carousel")` → tout élément
  `.owl-carousel` est initialisé automatiquement en lisant ses attributs `data-*`
  (`data-items`, `data-sm-items`, `data-md-items`, `data-nav`, `data-margin`, etc.).
- **Flèches natives** : le thème positionne `.owl-prev/.owl-next` en `position:absolute; top:50%`.
  **L'utilisateur NE PEUT PAS personnaliser Owl côté VP Dive** → sur la maquette on garde le
  style de flèches natif (ne pas re-styliser).
- Dans l'éditeur VP Dive (`isNoviBuilder`), Owl est volontairement désactivé (slides empilées) ;
  le carousel ne s'active que sur le site publié.

### Charte graphique
- Bleu foncé : **#062D63** · Cyan : **#20C4D8** · Bleu médian : **#0E66A9**
- Dégradés cartes : `linear-gradient(160deg,#0E66A9,#062D63)` et `...(#20C4D8,#0E66A9)`
- Texte gris : #5a6a7a / #8a97ab · Ombre douce : `0 10px 30px rgba(6,45,99,.08)`
- Polices : Montserrat (titres) + Roboto (corps).

---

## 4. Travail réalisé (chronologique)

1. **Mentions légales** (`mentions-legales.html`) : récupérées depuis la page VP Dive live,
   restructurées, complétées pour conformité (RGPD détaillé, section **Cookies** logique CNIL,
   responsabilité, liens tiers). Reste à compléter : coordonnées légales complètes de l'hébergeur VP Dive.
2. **Message par défaut formulaire baptême** : texte court fourni (sans nom/tél/email, champs séparés).
3. **Hero de la page d'accueil** : corrigé le problème de cadrage de la bannière raie manta.
   - Problème VP Dive : `background-image` + `height:65%` (invalide) → image rognée selon résolution.
   - **Solution appliquée** : `background-size:cover` + `background-position:center center` +
     **`aspect-ratio:1983 / 793`** (ratio exact de banniere.png) → cadrage stable à toute résolution.
     Texte centré via `flex + align-items:center`. VALIDÉ par l'utilisateur.
   - ⚠️ Côté VP Dive, mettre l'`aspect-ratio` = dimensions réelles de l'image uploadée.
4. **Section "Prochaines activités"** : plusieurs itérations.
   - Style retenu : **cartes horizontales** (pastille date en dégradé à gauche, contenu à droite),
     dans un **carousel Owl** (structure `.owl-carousel > .item`) reproduisant le comportement VP Dive
     (slider + flèches natives + responsive 1/2/3 items via `data-items`).
   - Données = **live VP Dive** (6 événements, config `nbr="6"`). Titres/lieux/dates/responsables EXACTS
     (ne pas reformuler les titres d'événements).
   - Détails de style validés : terme « Responsable » en **poids léger** (#8a97ab, 400), placé
     au-dessus du nom mais à droite de l'avatar ; contenu centré verticalement ; espacements internes.
   - Flèches : **style natif Owl conservé** (non personnalisable côté VP Dive).
5. **Section "Nos activités"** : les 4 images en haut des cartes converties de
   `<div background:url(...)>` en **vraies balises `<img style="object-fit:cover">`** pour que le
   module de gestion d'image VP Dive puisse changer l'image. Rendu visuel identique.
6. **`table.html`** : tableau tarifs 2026/2027 stylé (validé « niquel »). Libellés raccourcis,
   séparateur « Majorations & licence seule », cases vides = tiret, format € virgule.
7. **`table-documents.html`** : liste de 7 PDF téléchargeables, même style. Icône PDF `fa-file-pdf-o`,
   bouton pastille cyan « ⬇ PDF ». Colonne "Type" fusionnée dans le titre. Titres assurance raccourcis.

---

## 5. Préférences de l'utilisateur (méthode)

- Veut du **HTML brut sans style inline superflu** quand c'est possible, mais accepte l'inline
  quand le thème ne fournit pas d'alternative (cf. §3).
- Rendu doit **rester collable dans l'éditeur VP Dive** (pas de `<style>` global fragile,
  sections autonomes).
- Tient à la **fidélité au comportement réel VP Dive** (ex : garder Owl et ses flèches natives).
- Valide visuellement en ouvrant les fichiers dans le navigateur (`open fichier.html`).
- Attentif au détail visuel (espacements, poids de police, position des éléments).

---

## 6. Points ouverts / TODO

- [ ] Compléter les **coordonnées légales de l'hébergeur VP Dive** dans `mentions-legales.html` (obligation LCEN).
- [ ] Décider si on **reflète les couleurs réelles** des événements VP Dive (bleu/jaune/rose) sur les
      pastilles date des "Prochaines activités", ou si on garde la palette du club (actuel).
- [ ] Confirmer format des libellés des tableaux (raccourcis actuels vs intitulés exacts VP Dive).
- [ ] Étape non faite : appliquer réellement les styles sur VP Dive (coller les blocs / restyler
      le composant Owl natif — dépend de ce que l'éditeur autorise).
