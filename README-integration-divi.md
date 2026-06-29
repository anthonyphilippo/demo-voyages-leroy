# Voyages Leroy — Maquette web & guide d'intégration WordPress / Divi

Maquette de démonstration moderne et responsive pour **Voyages Leroy (Jovial Car)**,
agence de voyages et d'autocars du Hainaut (Tournai, Péruwelz, Mons, Havinnes).

---

## 1. Contenu de la maquette

| Fichier | Page |
|---|---|
| `index.html` | Accueil (hero, recherche, catégories, voyages à la une, autocars, Club, agences, newsletter) |
| `voyages.html` | Catalogue avec **filtres interactifs** par type de voyage |
| `voyage.html` | **Fiche voyage type** (exemple : Venise) — galerie, itinéraire, carte de réservation |
| `autocars.html` | Location d'autocars + formulaire de devis |
| `club.html` | Club Jovial Car (programme fidélité) + adhésion |
| `contact.html` | 4 agences + formulaire de contact |
| `assets/css/style.css` | Design system (variables `:root`) |
| `assets/js/main.js` | Header sticky, menu mobile, filtres, reveal, formulaires démo |

Design system → tout est centralisé dans `:root` (couleurs, typo, rayons, ombres).
Modifier une variable = répercussion sur tout le site.

```css
--primary:#1466b8;   /* bleu voyage */
--accent:#ff6b35;    /* orange "Jovial" / soleil */
--gold:#ffb703;      /* doré accents */
```

---

## 2. ⚠️ Point clé d'architecture : le catalogue de voyages

**Ne PAS créer chaque voyage comme une page Divi à la main.**
Voyages Leroy ajoute et met à jour des voyages en permanence (dates de départ, prix,
disponibilités). Gérer ça à la main dans Divi deviendrait ingérable.

### Architecture recommandée

| Brique | Outil | Rôle |
|---|---|---|
| **Habillage** : header, footer, pages fixes (accueil, autocars, Club, contact) | **Divi + Theme Builder** | Édition visuelle, parfait pour le client |
| **Catalogue de voyages** (les ajouts fréquents) | **Custom Post Type « Voyage »** + champs ACF (type, destination, durée, prix, date de départ, photo, places) | 1 voyage = 1 fiche remplie via formulaire, pas une page |
| **Listing + filtres** (`voyages.html`) | Module Divi **Blog/Portfolio** sur le CPT, ou plugin de filtres (FacetWP / JetEngine) | Affichage et tri automatiques |
| **Réservation + paiement** | Plugin dédié (**WP Travel Engine**, **WooCommerce Bookings**) | Panier, acompte, paiement (Ogone/Stripe), comptes clients |

> Concrètement : la maquette `voyage.html` montre **à quoi ressemble une fiche** ;
> en production, ce gabarit devient un **template ACF/Divi** rempli automatiquement
> pour chaque voyage du CPT. Ajouter un voyage = remplir un formulaire en 2 minutes.

---

## 3. Reprise dans Divi (habillage)

1. **Theme Builder** → header & footer globaux (repris à l'identique sur tout le site).
2. Chaque `<section>` de la maquette = un **module Code** Divi (ou recréée en modules natifs).
3. Reporter les variables `:root` dans **Divi → Options du thème → CSS personnalisé**.
4. Polices : **Poppins** (titres) + **Inter** (texte) — déjà dispo dans Divi.
5. Brancher les formulaires (`data-demo`) sur **Divi Contact Form**, Gravity Forms ou WPForms.

### Responsive (déjà géré dans la maquette)
- **1024 px** : menu → hamburger (évite que le numéro de tél se serre)
- **980 / 820 px** : grilles et colonnes
- **560 px** : une colonne
- **Bouton d'appel flottant** mobile (`.fab-call`) sous 1024 px

---

## 4. Charte graphique

Parti pris propre avec clin d'œil à l'esprit « Jovial Car » (convivial, soleil, voyage).
**Avant la version finale, récupérer la charte officielle** (logo vectoriel, couleurs
exactes, typo) et ajuster les variables `:root`.

---

## 5. Images

- Photos de destinations / autocars = **exemples libres (Unsplash)**, à remplacer par
  les **vraies photos** de Voyages Leroy (autocars, équipe, voyages réalisés).
- Prix, dates, itinéraires = **fictifs**, à remplacer par le catalogue réel.

---

*Maquette réalisée par Anthony Philippo — Email Evolution.*
