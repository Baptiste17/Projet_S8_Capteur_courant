---
layout: default
title: Programmation des flux et du dashboard Node-Red
parent: Conception et prototypage
nav_order: 3
---

# 3. Programmation des flux et du dashboard Node-Red
Une fois que l'objet récupérait bien les données électriques, l'objectif était d'utiliser Fiware avec le context-broker Orion pour gérer facilement ces données. Pour ce faire nous avons décidé d'utiliser Node-Red afin de relier l'objet de calcul électrique à plusieurs services.

## 3.1 Récupération des flux MQTT
Pour récupérer les données envoyées par l'objet connecté, nous avons utilisé le protocole MQTT (Message Queuing Telemetry Transport). MQTT est un protocole léger de messagerie publish/subscribe qui convient parfaitement pour les appareils à faible bande passante. Dans Node-Red, nous avons ajouté un nœud mqtt in pour nous abonner aux messages envoyés par l'objet sur un sujet spécifique. Voici les étapes suivies :
*Ajouter un nœud mqtt in dans l'interface Node-Red.
*Configurer ce nœud avec l'adresse du broker MQTT et le sujet sur lequel les données sont publiées.
*Relier le nœud mqtt in à un nœud de débogage pour vérifier que les données sont correctement reçues.

## 3.2 Enregistrement de l'objet Fiware Orion et création d'abonnements
Pour gérer les données avec Fiware Orion, nous avons d'abord enregistré notre objet connecté comme une entité dans le context-broker Orion. Les étapes pour l'enregistrement sont les suivantes :
*Utiliser l'API REST de Fiware Orion pour créer une nouvelle entité représentant une mesure électrique (puissance, énergie, tension, courant, etc.).
*Définir les attributs de l'entité correspondant aux différents objets de mesure.

Ensuite une fois que les entités sont créés, nous avons configurer des abonnements dans Orion. Un pour que chaque mise à jour des données de l'objet soit envoyée à des services spécifiques. Et d'autres contenant des conditions afin d'envoyer une notification à chaque que cette condition est respectée. Lorsqu'un objet dépasse une certaine puissance par exemple une notification est envoyé. Celà permet d'indiquer par la suite que l'appareil dont la puissance est calulé est en fonctionnement.

## 3.3 Enregistrement historisé dans MySQL

## 3.4 Dashboard

## 3.5 Quelques images des flux et du dashboard

<img
    style="display: block; 
           margin-left: auto;
           margin-right: auto;
           width: 30%;"
src="../images/dashboard_node-red.jpg"
alt="dashboard node-red">
<p style="text-align: center;"><em>Rendu des données dans le dashboard de Node-Red</em></p>