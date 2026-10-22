# workflowN8N — Veille automatique

Projet de cours : automatiser une veille sur l’intelligence artificielle avec n8n, Google Gemini, Notion et Gmail.

## Organisation

```text
workflows/
  Veille automatique.json         # À importer dans n8n
  Veille automatique.workflow.ts  # Version TypeScript du workflow
skills/
  interview/
  doubt-driver-dev/
  hostile-review/
videos/                           # Vidéo de démonstration à ajouter
```

## Fonctionnement

Le workflow se déclenche chaque jour à 8 h, lit un flux RSS, conserve les articles avec un titre et une date dans les dernières 24 heures, dédoublonne les liens, puis regroupe les articles. Gemini produit une synthèse structurée en XML, enregistrée dans Notion et transformée en newsletter HTML pour Gmail.

Le nœud Markdown est conservé mais désactivé. La note collante présente des pistes initiales plus larges ; Tavily, Firecrawl, Claude et PostgreSQL ne font pas partie du flux actuel.

## Importer et configurer

1. Dans n8n, importer `workflows/Veille automatique.json`.
2. Dans `RSS Read`, remplacer `https://example.com/veille-rss.xml` par votre flux RSS.
3. Associer vos connexions Gemini, Notion et Gmail aux nœuds correspondants.
4. Dans `Saving the report`, remplacer `VOTRE_DATA_SOURCE_ID` par votre source de données Notion. Prévoir une propriété de titre et une propriété de date nommée `Date de veille`, ou adapter le mapping.
5. Dans le nœud Gmail, remplacer `destinataire@example.com` par l’adresse de destination.
6. Régler le fuseau horaire du workflow sur `Europe/Paris` et vérifier la disponibilité du modèle Gemini configuré.
7. Tester la collecte et la synthèse, puis le flux complet. Un test complet crée une page Notion et envoie un courriel. Activer ensuite le workflow pour la planification.

Les connexions et références personnelles ont été retirées de l’export public. Aucun secret n’est nécessaire dans ce dépôt. Le JSON est le fichier à importer dans l’interface n8n ; le TypeScript est une représentation de code générée avec `@n8n/workflow-sdk` via n8ncli.

## Les trois skills

- **interview** : clarifier le besoin et rédiger une spécification de projet ; son modèle de spécification est inclus.
- **doubt-driver-dev** : développer, vérifier les hypothèses et tester le résultat.
- **hostile-review** : examiner le projet, corriger les défauts établis et documenter les limites.

Ces fichiers décrivent des consignes pour l’assistant de développement ; ils ne sont pas des nœuds à importer dans n8n.

## Vérifications et limites

Les exports JSON et TypeScript ont été contrôlés pour vérifier la cohérence des nœuds et des connexions. Aucun workflow n’a été exécuté pour préparer ce dépôt.

La création Notion n’est pas protégée contre plusieurs rapports du même jour. La disponibilité de Gemini et le respect du format XML restent nécessaires au bon fonctionnement ; cette publication GitHub ne constitue pas une validation du flux de bout en bout.

## Démonstration

La vidéo de présentation sera ajoutée dans `videos/`.
