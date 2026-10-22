# Veille IA automatisée avec n8n

Projet réalisé dans le cadre du cours : créer un workflow de veille sur l’intelligence artificielle et utiliser trois skills pour accompagner la conception, le développement et la revue du projet.

## Objectif

Automatiser la collecte d’articles, produire une synthèse en français, l’archiver dans Notion et la recevoir par e-mail.

## Fonctionnement du workflow

```text
Déclenchement quotidien à 8 h
  → Lecture du flux RSS
  → Filtrage des articles des dernières 24 heures avec un titre
  → Suppression des liens en double
  → Préparation et regroupement des articles
  → Synthèse avec Google Gemini
  → Enregistrement dans Notion
  → Envoi d’une newsletter HTML avec Gmail
```

Gemini reçoit les titres, dates, liens et extraits RSS. Il produit un rapport structuré en XML : résumé, faits rapportés, analyse, piste d’action, articles suivis et limites des sources. Le workflow utilise ce rapport pour l’archivage Notion et la mise en forme du courriel. Il ne vérifie pas le contenu complet des pages liées.

## Contenu du dépôt

| Dossier | Contenu |
|---|---|
| [`workflows/`](workflows/) | Workflow **Veille automatique**, en JSON pour l’import dans n8n et en TypeScript pour la lecture du code. |
| [`skills/`](skills/) | Les trois skills utilisés pour structurer le travail avec l’assistant IA. |
| [`videos/`](videos/) | Emplacement prévu pour la vidéo de démonstration. |

## Les trois skills

Ils organisent le travail en trois étapes :

1. **[interview](skills/interview/SKILL.md)** : clarifier le besoin et rédiger une spécification exploitable.
2. **[doubt-driver-dev](skills/doubt-driver-dev/SKILL.md)** : développer la solution, vérifier les hypothèses et tester son comportement.
3. **[hostile-review](skills/hostile-review/SKILL.md)** : examiner le résultat, repérer les défauts et documenter les corrections et limites.

Les skills sont des consignes pour l’assistant de développement. Ils ne s’importent pas comme des nœuds n8n. Le modèle de spécification du skill `interview` est également inclus.

## Importer et configurer le workflow

1. Télécharger [`Veille automatique.json`](workflows/Veille%20automatique.json), puis l’importer dans n8n.
2. Dans **RSS Read**, remplacer l’URL d’exemple par son propre flux RSS.
3. Configurer les connexions **Google Gemini**, **Notion** et **Gmail** dans n8n.
4. Dans **Saving the report**, sélectionner sa source de données Notion et vérifier les propriétés de titre et de date (`Date de veille`).
5. Dans le nœud Gmail, remplacer `destinataire@example.com` par l’adresse de destination.
6. Régler le fuseau horaire sur **Europe/Paris** et vérifier que le modèle Gemini choisi est disponible.
7. Tester le workflow, puis l’activer pour les exécutions planifiées.

Un test complet crée une page Notion et envoie un e-mail. Les connexions et références personnelles ont été retirées des exports publics et doivent être renseignées après l’import.

Le fichier [`Veille automatique.workflow.ts`](workflows/Veille%20automatique.workflow.ts) est la représentation TypeScript générée avec le SDK n8n via n8ncli. Pour l’import dans l’interface n8n, utiliser le JSON.

## Vidéo de démonstration

La vidéo sera ajoutée dans [`videos/`](videos/). Elle présentera le workflow, ses principales étapes et le résultat obtenu dans Notion et Gmail.

## Vérifications et limites

- La cohérence des nœuds et des connexions entre les exports JSON et TypeScript a été contrôlée. Aucun workflow n’a été exécuté pour préparer cette publication GitHub.
- Le bon fonctionnement dépend notamment de la disponibilité de Gemini et du respect du format XML demandé.
- Plusieurs exécutions le même jour peuvent créer plusieurs rapports dans Notion : la création n’est pas protégée contre ce cas.
- Les synthèses reposent sur les extraits RSS reçus ; les informations peuvent être incomplètes et nécessiter une vérification auprès des sources.
- Le nœud Markdown est conservé mais désactivé. La note collante décrit des pistes initiales ; Tavily, Firecrawl, Claude et PostgreSQL ne sont pas intégrés au flux actuel.
