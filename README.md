# MANTAS 86 — Refonte du site (prévisualisation locale)

> ## 🔖 Accès rapide
> **Tableau de bord :** `http://localhost:8765/index.html`
>
> Le pane du navigateur Claude Code n'a pas de favoris : **demande simplement à Claude
> « ouvre l'index »** — il relance le serveur si besoin et ouvre la page. Sinon, colle
> l'URL ci-dessus dans la barre d'adresse du pane (serveur lancé au préalable, cf. plus bas).

Ce dépôt contient les pages HTML restylées à la charte du club, prêtes à coller dans
l'éditeur VP Dive. Un tableau de bord (`index.html`) permet de prévisualiser chaque page.

## ⚠️ Toujours prévisualiser via le serveur local (pas en `file://`)

Les pages de `2026/` chargent le CSS et le JS du thème via des chemins **relatifs**
(`../assets/css/...`). Ouvertes directement en `file://` (double-clic), les images et
le style ne se chargent pas correctement. **Il faut passer par un petit serveur web local.**

### 1. Lancer le serveur (au démarrage)

Depuis la racine du dépôt :

```bash
python3 -m http.server 8765 --bind 127.0.0.1
```

Laisser cette commande tourner dans un terminal (elle occupe le port 8765).

### 2. Ouvrir le tableau de bord

Une fois le serveur lancé, ouvrir dans le navigateur :

```
http://localhost:8765/index.html
```

Depuis l'index, cliquer sur une carte ouvre la page correspondante (les liens sont
relatifs et fonctionnent car servis par le serveur). Choisir le dossier `2026/`
(pages du site) ou `exemples/` (démos de composants).

### 3. Stopper le serveur (quand le travail est terminé)

Dans le terminal où il tourne : `Ctrl + C`.
Ou, s'il tourne en arrière-plan, libérer le port :

```bash
lsof -ti tcp:8765 | xargs kill
```

## Structure du dépôt

- `index.html` — tableau de bord de prévisualisation (sélecteur de dossier + cartes).
- `2026/` — **livrables** : pages finalisées, stylées à la charte, à coller dans VP Dive.
- `exemples/` — démos de composants (tableaux, boutons, choix d'images de hero, maquettes de style).
- `assets/css/` — CSS officiel du thème VP Dive V5 (`bootstrap.css`, `style.css`, `novi.css`, `custom.css`).
- `assets/js/` — JS du thème (`jquery.min.js`, `core.min.js`, `script.js`).
- `SUIVI-PAGES.md` — recensement de toutes les pages + statut + « personnalisable ? ».
- `CONTEXTE-PROJET.md` — contexte du club et de la plateforme VP Dive, charte graphique.

## Rappels VP Dive (pour coller les pages)

- **CSS inline uniquement** : VP Dive supprime les blocs `<style>`. Tout le style des
  livrables est en `style="..."` inline.
- **Chemins d'images** : en local ils sont en absolu (`https://mantas86.vpdive.com/...`)
  pour que la prévisualisation fonctionne ; **côté VP Dive, remettre les chemins relatifs**.
- **Composants dynamiques** (tableaux de documents, module vidéos, carte Google Map,
  trombinoscope, formulaires) : générés par la plateforme → **ne pas les remplacer** par
  du HTML statique. Sur ces pages, seuls le hero + l'intro (+ blocs de liens statiques) sont
  personnalisables ; le reste est laissé au module natif.
