# Atlas — guide d'utilisation

Éditeur de carte à points et liaisons, dans un seul fichier HTML. Ouvrez `editeur-carte.html`
dans un navigateur : aucune installation, aucun serveur.

---

## 1. Le principe : rien n'est prédéfini

Au démarrage, la carte est vierge et **aucun type n'existe**. Vous créez vos types au fil de
l'eau, et la légende se construit toute seule à mesure. Un type, c'est un nom associé à une
apparence :

- **Type de lieu** — un symbole (parmi douze) ou une image importée, une couleur, une taille,
  un style de texte, et la liste des paramètres proposés pour ce type.
- **Type de liaison** — un tracé (parmi douze), une teinte, un style de texte, et sa liste de
  paramètres.

Le nom que vous donnez à un visuel *devient* le type. Il apparaît aussitôt dans la barre
d'outils et dans la légende, avec le nombre d'éléments qui l'utilisent.

---

## 2. Poser des lieux

- **Clic sur le fond** → boîte « Nouveau lieu » : son nom, son type, ses paramètres,
  le placement de son texte.
- Si aucun type n'existe encore (ou si vous choisissez **Nouveau type…**), la création du type
  s'intercale, puis vous revenez au lieu avec ce que vous aviez déjà saisi.
- **Glisser un lieu** le déplace ; les liaisons suivent.
- **Clic sur un lieu** amorce une liaison. **Reclic sur le même lieu** ouvre sa fiche pour
  modifier son nom, son type ou ses paramètres. `Échap` annule l'amorce.
- **Double-clic** ouvre aussi la fiche. **Clic droit** ou `Suppr` au survol efface le lieu et
  ses liaisons.

---

## 3. Tracer des liaisons

- Cliquez un premier lieu, puis un second. Pendant le trajet, une ligne fantôme suit le curseur
  et affiche la distance en direct.
- La boîte « Nouvelle liaison » demande le type, les paramètres et la courbure.
- **Clic sur une liaison** la sélectionne : une poignée laiton apparaît en son milieu. Tirez-la
  perpendiculairement pour creuser ou inverser la courbe ; elle se raccroche à la ligne droite
  près de zéro.
- **Reclic sur une liaison déjà sélectionnée** la **scinde** à l'endroit cliqué : un lieu est
  posé sur le tracé (vous le nommez et lui donnez son type), puis le coût de chaque moitié est
  demandé, prérempli avec celui de la liaison d'origine. La courbure d'origine est répartie
  exactement entre les deux moitiés, et une nouvelle liaison s'amorce depuis l'intersection.
  Pour désélectionner sans scinder : `Échap`, ou un clic sur le fond.
- **Double-clic** sur une liaison ouvre sa fiche. **Clic droit** ou `Suppr` l'efface.

---

## 4. Les paramètres

Rien n'est imposé : chaque lieu et chaque liaison porte autant de couples **nom / valeur** que
vous voulez — coût, durée, garnison, saison praticable, note. Les noms saisis sont mémorisés
sur le type : l'élément suivant de ce type les proposera d'emblée, vides.

La valeur affichée sur la carte est celle du **premier paramètre renseigné**, dans l'ordre des
champs du type. Le cartouche de survol les liste tous.

Un dialogue de type comporte aussi sa propre liste de champs, pour préparer les paramètres à
l'avance. Une nouvelle liaison propose « Coût » par défaut, à supprimer si vous n'en voulez pas.

---

## 5. Les tracés de liaison

Douze tracés, tous déclinables dans huit teintes :

| Tracé | Aspect |
|---|---|
| Sentier à traverses | bande claire barrée de traverses sombres, tracé tremblé |
| Piste large | même principe, plus épais |
| Sente pointillée / tiretée | points ou tirets à bouts ronds |
| Route | trait plein avec liseré |
| Chaussée pavée | trait plein strié de pavés |
| Voie ferrée | filet central et traverses régulières |
| Chaîne | maillons à bouts ronds |
| Cours d'eau | trait large au tremblé plus ample, avec reflet |
| Fil ténu | trait fin |
| Voie barrée | tirets coupés de barreaux |
| Voie fléchée | tirets terminés par une pointe |

Le tremblé est obtenu par un filtre de turbulence SVG appliqué au tracé.

## 6. Les symboles de lieu

Ville, capitale, village, lieu-dit, contrée, montagne, forêt, tour, ruine, port, croisée,
repère — ou **votre propre image** (PNG, JPG, WebP), automatiquement réduite à 256 px pour que
le fichier exporté reste léger. Un curseur règle la taille du symbole sur la carte,
indépendamment du zoom.

---

## 7. Les textes

**Le style appartient au type** (dialogue de type, section *Style du texte*) :

- sept polices : titrage condensé, capitales romaines, ancienne presse, Garamond, onciale,
  machine à écrire, sans système ;
- gras, italique, souligné, majuscules ;
- couleur des lettres et couleur du contour, avec l'option *sans contour* ;
- taille, et un aperçu en direct.

La première pastille des deux palettes, moitié sombre moitié claire, signifie **selon le
thème** : le texte suit alors le thème clair ou sombre. Une couleur choisie explicitement ne
bouge plus.

**Le placement appartient à l'élément** :

- **Placement auto** (par défaut) : douze orientations à trois éloignements sont essayées, la
  première qui ne recouvre ni un autre texte, ni un symbole, ni un tracé est retenue. Les lieux
  sont placés avant les liaisons.
- **À la main** : attrapez le texte et faites-le tourner autour de son lieu, ou autour du
  sommet de sa liaison. Il bascule seul en placement manuel. Les curseurs *Orientation* et
  *Éloignement* de la fiche font la même chose au degré près.
- Le bouton **Placement auto** de la barre remet toute la carte en automatique.
- Un clic simple sur un texte ouvre l'élément correspondant.

---

## 8. Le fond de carte

- **Fond → Image…** charge une image ; elle est ajustée à l'écran et le mode calage s'ouvre.
- En calage : glisser l'image la déplace, les curseurs règlent son **échelle** (5 à 400 % de sa
  taille réelle) et son **opacité**. *Ajuster* la recadre, *Terminer* referme le mode et rend le
  clic à la création de lieux.
- **Grille** masque le quadrillage. La grille fine s'efface d'elle-même sous 45 % de zoom.

L'échelle du fond est indépendante du zoom de la vue : vous calez une fois, vous naviguez
ensuite sans rien décaler.

---

## 9. Naviguer

| Geste | Effet |
|---|---|
| Glisser le fond | déplacer la vue |
| Molette | zoomer au curseur |
| Pincer à deux doigts | zoomer et déplacer |
| Boutons − / + | zoomer par crans |
| **Cadrer** | tout ramener à l'écran, fond compris |

Amplitude : 10 % à 400 %.

---

## 10. Thème et langue

- **Thème clair / sombre** : un bouton bascule l'ensemble, quadrillage et fond de carte compris.
- **Langue** : menu à drapeaux, français et anglais. Vos noms de types restent tels que vous les
  avez écrits.

Les deux réglages sont conservés avec la carte.

---

## 11. Réinitialiser

Le menu **Réinitialiser** propose quatre portées :

1. **Effacer les éléments** — lieux et liaisons ; types et fond conservés.
2. **Réinitialiser les types** — types, icônes et éléments : on repart de zéro.
3. **Retirer le fond** — l'image et son calage.
4. **Tout réinitialiser**.

Tout cela reste annulable par `Ctrl+Z`.

---

## 12. Exporter et importer

Le menu **Exporter** propose trois formats :

- **Image PNG** — le fond calé et les éléments aplatis en un seul rendu, cadré sur le contenu,
  en double résolution. Les polices Google n'étant pas embarquées dans le SVG rasterisé, le
  texte y retombe sur une police système.
- **Données JSON** — types, icônes en base64, lieux et liaisons avec positions, courbures,
  paramètres et placement des textes, plus une **matrice d'adjacence** (`matrice.ordre` et
  `matrice.cellules`) qui donne la même information sous forme tabulaire. Sans le fond.
- **Carte complète JSON** — les mêmes données, avec l'image de fond et son calage.

**Importer** relit indifféremment les trois formes et reconstruit tout à l'identique, icônes
personnalisées comprises.

Structure du JSON de données :

```json
{
  "format": "atlas-carte", "version": 3,
  "typesLieux":   [{ "id": "nt1", "name": "Port franc", "color": "#E8B04B",
                     "symbol": 9, "icon": null, "size": 56,
                     "label": { "font": "cinzel", "size": 13, "color": "auto" },
                     "fields": ["Coût"] }],
  "typesLiaisons":[{ "id": "lt1", "name": "Voie du sel", "trace": 0, "color": "#EADFC4" }],
  "icones":  [{ "id": "i3", "src": "data:image/png;base64,…", "w": 256, "h": 192 }],
  "lieux":   [{ "id": "n1", "typeId": "nt1", "name": "Havreport",
                "x": 320, "y": 180, "params": { "Coût": "3" },
                "label": { "auto": true } }],
  "liaisons":[{ "id": "l4", "typeId": "lt1", "a": "n1", "b": "n2",
                "curve": 0.18, "params": { "Coût": "10" } }],
  "matrice": { "ordre": ["n1", "n2"], "cellules": [[null, { "liaison": "l4" }], […]] },
  "cadre":   { "x": 0, "y": 0, "w": 1400, "h": 900 },
  "fond":    { "src": null, "x": 0, "y": 0, "scale": 1, "opacity": 0.7 }
}
```

---

## 13. Raccourcis

| Touche | Effet |
|---|---|
| `Échap` | annule l'amorce d'une liaison, la sélection, le mode calage ou une boîte de dialogue |
| `Suppr` / `Retour arrière` | efface l'élément survolé ou la liaison sélectionnée |
| `Ctrl+Z` / `Cmd+Z` | annule (60 étapes) |
| `Entrée` | valide la boîte de dialogue ouverte |
| Clic droit | efface l'élément visé |

La carte est sauvegardée automatiquement dans le navigateur ; une image de fond trop lourde
(plus de 4 Mo) n'est pas conservée, seul son calage l'est. Pour un travail durable, exportez
en JSON.

---

## 14. Ajouter une langue

Tout le texte de l'interface passe par un dictionnaire. Deux endroits à modifier, dans le bloc
`<script>` du fichier.

### a. Déclarer la langue

Dans la liste `LANGS`, ajoutez une entrée : identifiant, nom **écrit dans sa propre langue**, et
drapeau en SVG (gardez `class="flag"`).

```js
const LANGS = [
  { id:"fr", name:"Français", flag:`…` },
  { id:"en", name:"English",  flag:`…` },
  { id:"es", name:"Español",  flag:`<svg class="flag" viewBox="0 0 9 6">
      <rect width="9" height="6" fill="#AA151B"/>
      <rect y="1.5" width="9" height="3" fill="#F1BF00"/></svg>` }
];
```

Le menu se construit à partir de cette liste : drapeau puis nom, dans l'ordre déclaré.

### b. Traduire les clés

Dans l'objet `I18N`, ajoutez un bloc portant le même identifiant :

```js
const I18N = {
  fr: { … },
  en: { … },
  es: {
    "app.sub": "editor de mapas",
    "tb.places": "Lugares",
    …
  }
};
```

**Toute clé absente retombe automatiquement sur le français**, donc une traduction partielle
fonctionne : vous pouvez commencer par les clés les plus visibles et compléter ensuite.

### c. Les familles de clés

| Préfixe | Contenu |
|---|---|
| `app.` `tb.` `btn.` `menu.` | barre d'outils et menus |
| `hint.` `meter.` `zoom.` `calib.` | repères d'écran, compteurs, calage du fond |
| `leg.` `co.` | légende et cartouche de survol |
| `tt.` `ti.` | infobulles et tuiles de choix |
| `dlg.` `pa.` | boîtes de dialogue et éditeur de paramètres |
| `ty.` `el.` `sp.` | types, éléments, scission d'une liaison |
| `al.` | alertes et confirmations |
| `tr.0` … `tr.11` | noms des douze tracés |
| `sy.0` … `sy.11` | noms des douze symboles |
| `fo.` | noms des sept polices |

Deux clés contiennent des variables entre accolades, à conserver :
`el.linkSub` utilise `{a}` et `{b}`, `al.typeUsed` utilise `{n}` et `{name}`.

### d. Vérifier

Rechargez la page, choisissez la langue dans le menu : l'interface se retraduit sans perdre la
carte en cours. Le choix est mémorisé avec elle.

Pour repérer les oublis, comparez les jeux de clés dans la console :

```js
Object.keys(I18N.fr).filter(k => !(k in I18N.es));
```
