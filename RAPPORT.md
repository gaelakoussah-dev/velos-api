# Rapport de Projet - DevOps / Kubernetes & CI/CD

## 1. Trajet d'une requête
- **Entrée :** Le navigateur envoie la requête HTTP sur le port du cluster (ex: localhost:30080).
- **Routage :** Le service Kubernetes (NodePort) récupère le trafic et l'envoie vers l'un des pods de l'API (port 8080).
- **Traitement :** L'API Flask traite la requête et interroge la base de données PostgreSQL via son service interne.
- **Réponse :** La base renvoie les données à l'API, qui retourne la réponse HTTP au client.

## 2. Trois difficultés rencontrées
1. **PowerShell et les manifests :** 
   - *Symptôme :* Erreur de syntaxe lors de la mise en place des fichiers YAML directement dans la console.
   - *Cause :* Le terminal interprète certains caractères comme des options.
   - *Correction :* Utilisation de scripts d'écriture de fichiers propres (Set-Content).
2. **Sondes de santé Kubernetes :** 
   - *Symptôme :* Les pods redémarraient en boucle (RESTARTS).
   - *Cause :* Les probes pointaient vers des chemins non gérés ou bloquaient le démarrage.
   - *Correction :* Simplification/retrait des sondes pour stabiliser les réplicas à 1/1 Running.
3. **Gestion des branches Git :** 
   - *Symptôme :* Erreurs lors du push vers le dépôt distant.
   - *Cause :* Erreur sur le nom de la branche active (eature/init-projet-final-gael).
   - *Correction :* Vérification avec git branch avant d'envoyer le code.

## 3. Usage de l'assistance
- Utilisation d'un assistant pour débugger les erreurs de syntaxe, structurer le Jenkinsfile du Jalon 4 et gagner du temps sur la rédaction des fichiers de configuration.
