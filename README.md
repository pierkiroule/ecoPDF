# ecoPDF

**ecoPDF — Pier CyberPsychologue** est un annotateur PDF ultra simple, 100 % local, pensé pour mobile, tablette et ordinateur.

- sans backend
- sans compte
- sans cloud
- sans envoi de données
- compatible GitHub Pages

## Fonctionnalités

- Ouverture d'un PDF local (toutes les pages)
- Défilement vertical fluide
- Affichage net HiDPI (prise en compte de `window.devicePixelRatio`)
- Outils minimalistes :
  - Ouvrir
  - Stylo
  - Surligneur
  - Texte
  - Gomme
  - Annuler
  - Zoom +
  - Zoom -
  - Ajuster largeur
  - Télécharger
- 4 couleurs fixes : noir, rouge, bleu, vert
- 3 épaisseurs fixes : fin, moyen, epais
- Historique multi-niveaux par page (traits + texte)
- Export PDF multi-pages annoté, JPEG qualité 0.92 pour un bon compromis qualité/poids

## Stack minimale

- HTML / CSS / JavaScript natifs
- [PDF.js](https://mozilla.github.io/pdf.js/) pour le rendu
- [jsPDF](https://github.com/parallax/jsPDF) pour l'export
- Service Worker pour le mode hors ligne (après premier chargement)

## Démarrage local

Option 1 (simple) : ouvrir `index.html` dans le navigateur.

Option 2 (recommandé pour tester le Service Worker) :

```bash
python3 -m http.server 8080
```

Puis ouvrir `http://localhost:8080`.

## Déploiement GitHub Pages

1. Pousser ce dépôt sur GitHub.
2. Activer **Settings → Pages**.
3. Choisir la branche (ex: `main`) et le dossier racine (`/root`).
4. L'app est installable comme PWA.

## Checklist de tests manuels mobile

- [ ] Ouvrir un PDF de plusieurs pages sur smartphone.
- [ ] Vérifier le scroll vertical fluide.
- [ ] Tester Stylo avec doigt (traits continus).
- [ ] Tester Surligneur (opacité visible, continue).
- [ ] Tester Gomme (effacement total net).
- [ ] Ajouter un texte, le déplacer, le modifier, puis le supprimer (texte vide en édition).
- [ ] Faire plusieurs actions puis **Annuler** plusieurs fois.
- [ ] Zoom + / Zoom - / Ajuster largeur : annotations toujours visibles.
- [ ] Recharger la page et vérifier que l'interface reste fonctionnelle.
- [ ] Installer la PWA puis relancer en mode autonome.

## Checklist de tests export

- [ ] Exporter un PDF annoté de 1 page.
- [ ] Exporter un PDF annoté multi-pages.
- [ ] Vérifier que tous les traits/texte sont présents sur chaque page.
- [ ] Vérifier que le poids du fichier reste raisonnable.
- [ ] Vérifier la netteté du texte et des annotations sur écran Retina.
- [ ] Vérifier que le nom de sortie est propre : `nomsource_ecopdf_annote.pdf`.

## Notes de robustesse

- Les annotations sont séparées du fond PDF (`pdf-layer` + `anno-layer`).
- Les annotations sont stockées par page et ré-appliquées à chaque rerender (zoom).
- Le scroll reste naturel ; le geste à deux doigts permet de naviguer sans dessiner par erreur.
- Le projet reste volontairement minimal pour limiter la complexité.
