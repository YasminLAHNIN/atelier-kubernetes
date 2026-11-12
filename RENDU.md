# Rendu — Atelier Kubernetes

> Complétez ce fichier au fil de l'atelier, puis faites un commit et un push (voir la section « Rendu » du README).

**Nom / Prénom :** Lahnin Yasmin
**Groupe :** RS2

---

## Exercice 1 — Cluster

1. Combien de nœuds affiche `kubectl get nodes` ? Quel est le rôle de chacun ?
   > 3 nœuds. k3d-lab-server-0 est le control plane (master) : il contient l’API Server, le scheduler et les contrôleurs. k3d-lab-agent-0 et k3d-lab-agent-1 sont les agents qui exécutent les pods.
2. Que montre `docker ps` ? Qu'est-ce qu'un « nœud » dans k3d, concrètement ?
   > docker ps montre un conteneur Docker par nœud (server-0, agent-0, agent-1), plus k3d-lab-serverlb, le load balancer qui publie le port 8081 et l’API.

## Exercice 2 — Premier déploiement

3. Quels objets Kubernetes ont été créés par `kubectl create deployment` ? (indice : `kubectl get all`)
   > kubectl create deployment a créé un Deployment web. Le Service web vient de kubectl expose, et le service kubernetes existait déjà.
4. Vous avez supprimé le pod `web-...` : que s'est-il passé, et pourquoi ?
   > Un nouveau pod a été recréé avec un autre nom.

## Exercice 3 — Modifier un conteneur en direct

5. Après suppression du pod, votre message « Bienvenue... » a-t-il survécu ? Pourquoi ?
   > Non, le message n’a pas survécu. Le système de fichiers d’un conteneur est éphémère, le nouveau pod repart de l’image nginx d’origine.
6. Pourquoi le `port-forward` a-t-il cessé de fonctionner après la suppression du pod ?
   > Un port-forward vers un Service s’attache à un seul pod. Ce pod a été supprimé, donc le tunnel a cassé.

## Exercice 4 — Déclaratif

7. Quelle différence entre `kubectl create` et `kubectl apply` ?
   >
8. À quoi sert le `selector` d'un Service ? Que se passe-t-il s'il ne correspond à aucun pod ?
   >

## Exercice 5 — Scaling & mises à jour

9. Sur quels nœuds se trouvent vos 3 réplicas ? Collez la sortie de `kubectl get pods -l app=site -o wide`.
   ```

   ```
10. Avec l'image `nginx:9.99`, quel statut avait le pod ? Quelle commande vous a donné la cause ?
    >
11. Pendant la panne, le site restait-il accessible ? Pourquoi ?
    >

## Exercice 6 — Portainer & Mario

12. URL publique de votre Mario :
    >
13. Retrouvez le Deployment `mario` en ligne de commande. Portainer et `kubectl` parlent-ils au même composant ? Lequel ?
    >

## Bonus (facultatif)

14. Bonus réalisés et remarques :
    >

---

**Score obtenu avec `./scripts/check.sh` :** ... / ...
