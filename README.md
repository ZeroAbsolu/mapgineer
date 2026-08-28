# Mapgineer

*Un éditeur de cartes à lieux et liaisons, dans un seul fichier HTML.*

[English version](README.en.md) · [Guide d'utilisation](guide-utilisateur.md) · [Licence](LICENSE.md)

---

## Pourquoi ce projet

J'avais besoin de pouvoir dessiner et éditer des cartes : poser des lieux, les relier, attacher
un coût à chaque trajet, et pouvoir rouvrir le tout plus tard pour le modifier. Je n'ai rien
trouvé sur internet qui réponde à ce besoin — les éditeurs de cartes existants dessinent du
décor mais pas de réseau, les outils de graphes tracent des réseaux mais ne ressemblent pas à
des cartes, et presque aucun ne laisse définir librement ce qu'est un lieu ou un chemin.

Alors je l'ai fait. Et puisqu'il existe, autant le rendre disponible : si le besoin était le
mien, il est probablement aussi celui de quelqu'un d'autre.

![Exemple de carte produite avec Mapgineer](exemple-carte.png)

---

## Le concept

Une carte, ici, c'est un **graphe habillé** : des lieux, des liaisons entre ces lieux, et des
paramètres accrochés aux uns comme aux autres.

Le principe qui gouverne tout le reste : **rien n'est prédéfini**. Au premier lancement, la
carte est vierge et aucun type n'existe. C'est vous qui les créez au fil de l'eau, et le nom que
vous donnez à une apparence *devient* un type — « Cité franche », « Voie du sel », « Passe
fermée ». Chaque type porte son visuel, son style de texte et la liste des paramètres qu'il
propose. La légende se construit toute seule à mesure, avec le compte des éléments qui utilisent
chaque type.

Concrètement :

- **Cliquer sur le fond** pose un lieu ; **cliquer sur un lieu** amorce une liaison vers un
  autre.
- **Douze symboles** de lieu et **douze tracés** de liaison, déclinables en huit teintes — ou
  vos propres images en guise d'icônes.
- **Des paramètres libres** : autant de couples nom/valeur que vous voulez, mémorisés sur le
  type pour être proposés aux éléments suivants.
- **Une image de fond** que l'on cale à l'échelle et à l'opacité voulues, pour décalquer une
  carte existante.
- **Des textes maîtrisés** : police, gras, italique, souligné, couleurs des lettres et du
  contour, et un placement qui tourne librement autour de l'élément — ou se règle tout seul pour
  ne rien chevaucher.
- **Une liaison scindable** en cliquant dessus : un lieu se pose à l'intersection, et le coût de
  chaque moitié est demandé.
- **Thème clair ou sombre**, interface en français ou en anglais.
- **Trois exports** : image PNG aplatie, données JSON avec matrice d'adjacence, ou carte
  complète avec son fond. Tout se réimporte à l'identique.

Le tout tient dans un fichier HTML : pas d'installation, pas de serveur, pas de compte. On
l'ouvre dans un navigateur et on dessine.

---

## Démarrer

1. Téléchargez `editeur-carte.html`.
2. Ouvrez-le dans un navigateur récent (Chrome, Firefox, Edge, Safari).
3. Cliquez n'importe où sur la carte : le premier lieu, et son premier type, se créent dans la
   foulée.

La carte en cours est sauvegardée automatiquement dans le navigateur. Pour un travail durable,
exportez en JSON — c'est le format qui restitue tout, jusqu'aux icônes importées.

---

## Contenu du dépôt

| Fichier | Rôle |
|---|---|
| `editeur-carte.html` | l'application entière |
| `guide-utilisateur.md` | le guide complet, en français |
| `user-guide.md` | le même en anglais, avec la marche à suivre pour ajouter une locale |
| `LICENSE.md` | la licence et le détail des droits qu'elle accorde |
| `exemple-carte.png` | l'exemple ci-dessus, produit avec l'outil |

---

## Contribuer

Les traductions sont les bienvenues, et c'est la contribution la plus simple : tout le texte de
l'interface passe par un dictionnaire, une nouvelle langue tient en une entrée et un bloc de
clés. La marche à suivre est en fin de guide. Les clés manquantes retombent sur le français,
donc une traduction partielle fonctionne déjà.

---

## Licence

<a href="https://github.com/ZeroAbsolu/mapgineer">Mapgineer</a> © 2026 par
<a href="https://github.com/ZeroAbsolu">Kevin NIVA</a> est distribué sous licence
<a href="https://creativecommons.org/licenses/by-nc-sa/4.0/">CC BY-NC-SA 4.0</a>.

Partagez-le, modifiez-le, traduisez-le : il faut créditer l'auteur, signaler vos modifications,
ne pas en faire un usage commercial, et redistribuer vos versions sous la même licence. Les
cartes que vous produisez, elles, vous appartiennent. Le détail est dans [`LICENSE.md`](LICENSE.md).
