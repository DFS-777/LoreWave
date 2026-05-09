# Lore Weave

🇫🇷 [Français](#lore-weave) · 🇬🇧 [English](#lore-weave--english)

---

**Un outil de graphe narratif pour les créateurs de mondes, les auteurs et les game designers.**

Lore Weave vous permet de cartographier les personnages, factions, lieux et relations de votre univers sous forme de graphe interactif — avec un wiki intégré, des tags, des images et des variables personnalisées. Tout fonctionne dans un seul fichier HTML, sans installation ni connexion internet.

> By [Destiny Forge Studio](https://destinyforgestudio.com)

---

## Une note sur ce projet

*Ce projet a été entièrement vibe codé — l'idée était d'avoir un outil pour structurer mes univers de jeu, pas de faire un produit. Pas de vocation commerciale, pas de prétention.*

*Il a été généré avec une IA. Et une IA, c'est l'agrégat de tout ce que l'humanité a produit, documenté, partagé — chaque ligne de code open source, chaque réponse sur Stack Overflow, chaque tutorial écrit gratuitement par quelqu'un quelque part. En ce sens, ce projet appartient un peu à tout le monde, alors autant le rendre à tout le monde.*

*Le commercialiser irait directement à l'encontre de cet esprit. Ce code est libre, pas à vendre.*

---

## Fonctionnalités

### Canvas de graphe
- Modes **graphe libre** et **arbre hiérarchique**
- Déplacez les nœuds librement, connectez-les en maintenant le clic
- Pan (Espace + glisser ou clic droit) et zoom (molette)
- **Sélection au lasso** — dessinez un rectangle pour sélectionner plusieurs nœuds et les déplacer ensemble
- Recherche sur le canvas (icône 🔍) avec navigation clavier
- Double-clic sur le canvas vide pour créer un nœud instantanément

### Nœuds
- Descriptions en texte riche avec support **Markdown**
- **@mentions** dans les descriptions et les titres — cliquez pour naviguer vers le nœud ou tag référencé
- Tags avec couleurs personnalisées
- **Variables** clé/valeur personnalisées (string, number, boolean, enum)
- Image principale + galerie avec upload par glisser-déposer
- Importer un nœud d'un autre graphe comme référence partagée

### Liens (Edges)
- Connexions nommées ou anonymes entre les nœuds
- Description Markdown
- Variables clé/valeur avec **Collections de variables** — définissez un ensemble de variables une fois, appliquez-le à n'importe quel lien
- Images
- Label déplaçable le long du lien

### Tags
- Code couleur avec un sélecteur HSL personnalisé
- **Vue Focus Tag** — disposition en étoile montrant tous les nœuds liés à un tag
- Importer un tag depuis un autre graphe
- **Importer tous les nœuds d'un tag** dans le graphe actuel, en conservant leurs interconnexions
- Filtre rapide par tag dans la sidebar

### Mode Wiki
- Vue encyclopédie plein écran de tous les nœuds, tags et liens
- Éditeur Markdown inline par entrée
- Cartes de relations cliquables — cliquez sur le nœud *ou* directement sur le lien nommé
- Recherche + filtres par type (Nœuds / Tags / Liens)
- Purger les entrées orphelines (entités n'appartenant à aucun graphe)

### Écran d'accueil
- Plusieurs graphes par projet
- **Dossiers** — créez des dossiers, glissez-déposez des graphes dedans et dehors
- Renommez les graphes (double-clic) et les dossiers
- Badge arbre hiérarchique sur les graphes de type arbre

### Données & Persistance
- **Sauvegarde automatique** — structure dans `localStorage`, images dans `IndexedDB`
- **Export** vers fichier `.dfs` (JSON) avec Ctrl+S ou le bouton Sauvegarder
- **Import** par bouton ou glisser-déposer d'un fichier `.dfs` sur l'écran d'accueil
- Session restaurée automatiquement à la prochaine ouverture

### Collections de variables
- Définissez des ensembles de variables réutilisables dans la sidebar
- Appliquez une collection à n'importe quel lien en un clic — les clés existantes ne sont jamais écrasées

---

## Démarrage rapide

1. Téléchargez `LoreWeave.html`
2. Ouvrez-le dans n'importe quel navigateur moderne (Chrome, Firefox, Edge, Safari)
3. C'est tout — pas de serveur, pas d'installation, pas de compte

---

## Utilisation

| Action | Comment |
|---|---|
| Créer un nœud | Double-clic sur le canvas, ou "Nœud" dans la sidebar |
| Connecter deux nœuds | Maintenir le clic sur un nœud (~300ms) puis glisser vers un autre |
| Ouvrir les détails d'un nœud | Clic simple sur un nœud |
| Sélectionner plusieurs nœuds | Dessiner un rectangle lasso sur le canvas |
| Déplacer plusieurs nœuds | Glisser n'importe quel nœud sélectionné |
| Créer un tag | Bouton "Tag" dans la sidebar |
| Filtrer par tag | Cliquer sur un tag dans la sidebar |
| Ouvrir le Wiki | Bouton "Mode Wiki" (bas droite) |
| Sauvegarder le projet | Ctrl+S ou "Sauvegarder" |
| Charger un projet | "Charger" ou glisser un fichier `.dfs` sur l'écran d'accueil |
| Changer le type de graphe | Bouton "Type" dans la toolbar |

---

## Format de fichier

Les projets sont sauvegardés en fichiers `.dfs` — du JSON simple avec la structure suivante :

```json
{
  "graphs": [...],
  "nodes": [...],
  "edges": [...],
  "tags": [...],
  "folders": [...],
  "varCollections": [...]
}
```

Les images sont stockées séparément dans l'IndexedDB du navigateur et réintégrées lors de l'export.

---

## Détails techniques

- **Fichier HTML unique** — ~3600 lignes, aucune étape de build, aucune dépendance à l'exécution
- [Marked.js](https://marked.js.org/) pour le rendu Markdown (chargé depuis CDN)
- Police [Satoshi](https://www.fontshare.com/fonts/satoshi) (chargée depuis Fontshare CDN)
- Système d'icônes SVG personnalisé (pas de bibliothèque d'icônes)
- Sélecteur de couleur HSL personnalisé (pas de bibliothèque externe)

Utilisation hors ligne : les ressources CDN (police + marked.js) nécessitent une connexion internet au premier chargement. Pour une utilisation entièrement hors ligne, remplacez ces deux liens CDN par des copies locales.

---

## Compatibilité navigateurs

| Navigateur | Support |
|---|---|
| Chrome / Edge 90+ | ✅ Complet |
| Firefox 90+ | ✅ Complet |
| Safari 15+ | ✅ Complet |
| Navigateurs mobiles | ⚠️ Partiel (interactions canvas limitées) |

---

## Idées pour la suite

- [ ] Synchronisation Google Drive / cloud
- [ ] Annuler / rétablir (Undo / Redo)
- [ ] Modèles de types de nœuds
- [ ] Export PDF / image
- [ ] Thème clair / sombre
- [ ] Édition collaborative

---

## Licence

MIT — libre d'utilisation, de modification et de distribution. Mention de l'auteur appréciée.

---

*Lore Weave — By Destiny Forge Studio*

---
---

# Lore Weave — English

**A narrative graph tool for worldbuilders, writers, and game designers.**

Lore Weave lets you map your story's characters, factions, locations, and relationships as an interactive node graph — with a built-in wiki, tags, images, and custom variables. Everything runs in a single HTML file, no installation or internet connection required.

> By [Destiny Forge Studio](https://destinyforgestudio.com)

---

## A note on this project

*This project was entirely vibe coded — the idea was to have a tool to structure my game universes, not to build a product. No commercial purpose, no pretension.*

*It was generated with AI. And an AI is the aggregate of everything humanity has produced, documented, shared — every open source line of code, every Stack Overflow answer, every tutorial written for free by someone somewhere. In that sense, this project belongs a little to everyone, so it might as well be given back to everyone.*

*Commercializing it would go directly against that spirit. This code is free, not for sale.*

---

## Features

### Graph Canvas
- **Free graph** and **hierarchical tree** modes
- Drag nodes freely, connect them by holding a node
- Pan (Space + drag or right-click drag) and zoom (scroll wheel)
- **Lasso selection** — draw a rectangle to select multiple nodes and move them together
- Canvas search (click the 🔍 icon) with keyboard navigation
- Double-click on empty canvas to create a node instantly

### Nodes
- Rich text descriptions with **Markdown** support
- **@mentions** in both descriptions and titles — click to navigate to the referenced node or tag
- Tags with custom colors
- Custom key/value **variables** (string, number, boolean, enum)
- Main image + gallery with drag & drop upload
- Import a node from another graph as a shared reference

### Edges (Links)
- Named or anonymous connections between nodes
- Markdown description
- Key/value variables with **Variable Collections** — define a set of variables once, apply it to any edge
- Images
- Draggable label along the edge

### Tags
- Color-coded with a custom HSL color picker
- **Tag Focus View** — star layout showing all nodes linked to a tag
- Import a tag from another graph
- **Import all nodes of a tag** into the current graph, preserving their inter-connections
- Sidebar quick filter by tag

### Wiki Mode
- Full-screen encyclopedia view of all nodes, tags, and edges
- Inline Markdown editor per entry
- Clickable relation cards — click the node *or* the named edge directly
- Search + type filters (Nodes / Tags / Links)
- Purge orphan entries (entities belonging to no graph)

### Home Screen
- Multiple graphs per project
- **Folders** — create folders, drag & drop graphs in and out
- Rename graphs (double-click) and folders
- Hierarchical tree badge on tree-type graphs

### Data & Persistence
- **Auto-save** — structure in `localStorage`, images in `IndexedDB`
- **Export** to `.dfs` file (JSON) with Ctrl+S or the Save button
- **Import** by button or drag & drop a `.dfs` file onto the home screen
- Session restored automatically on next open

### Variable Collections
- Define reusable sets of variables in the sidebar
- Apply a collection to any edge in one click — existing keys are never overwritten

---

## Getting Started

1. Download `LoreWeave.html`
2. Open it in any modern browser (Chrome, Firefox, Edge, Safari)
3. That's it — no server, no install, no account

---

## Usage

| Action | How |
|---|---|
| Create a node | Double-click on the canvas, or "Nœud" in the sidebar |
| Connect two nodes | Hold click on a node (~300ms) then drag to another |
| Open node details | Single click on a node |
| Multi-select nodes | Draw a lasso rectangle on the canvas |
| Move multiple nodes | Drag any selected node |
| Create a tag | "Tag" button in the sidebar |
| Filter by tag | Click a tag in the sidebar |
| Open Wiki | "Mode Wiki" button (bottom right) |
| Save project | Ctrl+S or "Sauvegarder" |
| Load project | "Charger" or drag a `.dfs` file onto the home screen |
| Change graph type | "Type" button in the toolbar |

---

## File Format

Projects are saved as `.dfs` files — plain JSON with the following structure:

```json
{
  "graphs": [...],
  "nodes": [...],
  "edges": [...],
  "tags": [...],
  "folders": [...],
  "varCollections": [...]
}
```

Images are stored separately in the browser's IndexedDB and re-embedded on export.

---

## Technical Details

- **Single HTML file** — ~3600 lines, zero build step, zero dependencies at runtime
- [Marked.js](https://marked.js.org/) for Markdown rendering (loaded from CDN)
- [Satoshi](https://www.fontshare.com/fonts/satoshi) font (loaded from Fontshare CDN)
- Custom SVG icon system (no icon library dependency)
- Custom HSL color picker (no external color library)

Offline use: the CDN assets (font + marked.js) require an internet connection on first load. For fully offline use, you can replace those two CDN links with local copies.

---

## Browser Support

| Browser | Support |
|---|---|
| Chrome / Edge 90+ | ✅ Full |
| Firefox 90+ | ✅ Full |
| Safari 15+ | ✅ Full |
| Mobile browsers | ⚠️ Partial (canvas interactions limited) |

---

## Roadmap ideas

- [ ] Google Drive / cloud sync
- [ ] Undo / redo
- [ ] Node type templates
- [ ] Export to PDF / image
- [ ] Dark / light theme toggle
- [ ] Collaborative editing

---

## License

MIT — free to use, modify, and distribute. Attribution appreciated.

---

*Lore Weave — By Destiny Forge Studio*
