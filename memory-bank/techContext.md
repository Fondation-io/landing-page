# Contexte Technique: Cyborg Dev

## Technologies Utilisées

### Languages de Base
- **HTML5**: Structure sémantique pour une accessibilité et un référencement optimaux.
- **CSS**: Styling via Tailwind CSS.

### Framework CSS
- **Tailwind CSS**: Utilisé via CDN pour sa flexibilité et son approche utility-first qui permet un développement rapide et cohérent.

### Polices
- **Inter**: Police principale pour les titres, offrant une esthétique moderne et technologique.
- **Roboto**: Police secondaire pour le corps du texte, optimisée pour la lisibilité sur écran.

### Optimisation des Performances
- Chargement paresseux des images et des contenus hors-écran.
- Utilisation minimale de JavaScript pour préserver les performances.
- Optimisation des images pour réduire la taille des fichiers.

## Configuration de Développement

### Environnement
- Développement en local sans besoin de serveur spécifique (fichiers statiques).
- Possibilité d'utiliser un serveur local simple pour le développement (Live Server, etc.).

### Structure des Fichiers
```
/
├── index.html                 # Fichier principal HTML
├── assets/
│   ├── css/                   # Styles personnalisés si nécessaire
│   ├── js/                    # JavaScript minimal
│   ├── images/                # Images et icônes
│   └── fonts/                 # Polices si non chargées via Google Fonts
└── memory-bank/               # Documentation du projet
```

### Workflow de Développement
1. Création de la structure HTML de base
2. Mise en place des styles avec Tailwind CSS
3. Ajustements responsive pour différentes tailles d'écran
4. Intégration des animations et interactions subtiles
5. Tests et optimisations

## Contraintes Techniques

### Langage
- Tout le contenu doit être en français avec une grammaire et des accents parfaits.
- Terminologie spécifique au développement et à l'IA doit être précise et professionnelle.

### Compatibilité
- La page doit être entièrement responsive et fonctionner sur tous les appareils:
  - Desktop (>1024px)
  - Tablette (768px-1024px)
  - Mobile (<768px)
- Compatibilité avec les navigateurs modernes (Chrome, Firefox, Safari, Edge)

### Performance
- Temps de chargement rapide: objectif < 3 secondes sur connexion 4G
- Score PageSpeed Insights > 90 pour mobile et desktop
- Optimisation des animations pour éviter la consommation excessive de ressources

### Accessibilité
- Contraste suffisant entre le texte et l'arrière-plan malgré le design sombre
- Structure sémantique appropriée
- Texte alternatif pour tous les éléments visuels

## Dépendances

### CDN
- **Tailwind CSS**: Via CDN pour simplicité d'implémentation (v2.2.19)
  ```html
  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
  ```

### Polices
- **Google Fonts**: Pour charger Inter et Roboto
  ```html
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Roboto:wght@300;400;500&display=swap" rel="stylesheet">
  ```

### JavaScript (Minimal)
- Animations et interactions subtiles uniquement
- Gestion du formulaire de capture d'email
- Éventuellement bibliothèque légère pour les animations de particules dans la section héro

### Ressources Graphiques
- Icônes minimalistes pour les sections de défis
- Éléments graphiques subtils pour les arrière-plans
- Éventuellement photos/avatars pour les témoignages (option)

## Notes Techniques Additionnelles

- Privilégier l'utilisation de CSS Grid et Flexbox pour les mises en page
- Utiliser les variables CSS pour la cohérence des couleurs et des valeurs
- Implémenter des transitions CSS pour les animations simples
- Minimiser l'utilisation des média queries personnalisées en tirant parti des classes responsive de Tailwind