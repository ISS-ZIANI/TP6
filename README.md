#Rapport de Projet – MCP AI Agents (Java + Python)

## Introduction

Dans ce projet, j’ai développé une application basée sur le protocole **MCP (Model Context Protocol)**, permettant la communication entre un **agent intelligent en Java (Spring Boot)** et un **serveur Python** contenant des outils.  
L’objectif était de simuler un système **agentique** inspiré des intelligences artificielles modernes comme ChatGPT, Claude ou les agents LangChain.

---

## Ce que j’ai réalisé

### 1. Développement du client agent Java

J’ai utilisé Spring Boot pour créer une application Java qui agit comme **un agent intelligent** capable de :

- S’identifier auprès d’un serveur distant (initialisation MCP)
- Écouter les événements via une connexion **SSE (Server-Sent Events)**
- Découvrir les outils disponibles via `tools/list`
- Appeler un outil spécifique via `tools/call` en lui envoyant des paramètres

Ce client est configurable via un fichier `application.properties` et peut se connecter à plusieurs serveurs d’outils.

### 2. Développement du serveur Python

Le serveur Python simule une **plateforme d’outils distants**.  
Il contient plusieurs outils comme `hello`, `sum`, `echo`, etc.  
Le serveur expose deux endpoints :

- `/sse` : pour envoyer des événements au client agent via SSE
- `/tools/call` : pour répondre aux appels de l’agent

Le serveur est simple et extensible pour accueillir plus d’outils à l’avenir.

### 3. Utilisation du protocole MCP

J’ai respecté le **cycle de vie MCP** :

- **InitializationRequest** : identification de l’agent
- **InitializationResponse** : enregistrement réussi
- **tools/list** : récupération de la liste d’outils
- **tools/call** : appel dynamique à un outil distant avec réponse

Ce mécanisme montre comment les agents peuvent **raisonner dynamiquement** et interagir avec un environnement d’outils.

---

## Configuration et environnement

- **Langages** : Java 17, Python 3.10  
- **Frameworks** : Spring Boot, Flask (léger pour le serveur)  
- **Protocole de communication** : HTTP + SSE  
- **IDE utilisé** : IntelliJ IDEA  
- **Ports utilisés** :
  - Serveur Python : `8899`
  - Client Spring Boot : `8066`

Le fichier `application.properties` permet de configurer l’URL du serveur Python et les endpoints.


##

![Initialisation](images/sec1.PNG)

---

![Démarrage](images/sec2.PNG)

---

![SSE Connexion](images/sec3.PNG)

---

![Liste des outils](images/sec4.PNG)

---


![Appel outil](images/sec5.PNG)

---


![Résultat](images/sec6.PNG)

---

## Conclusion

Ce projet m’a permis de :

- Comprendre le fonctionnement des architectures agentiques modernes
- Mettre en place un **protocole de communication structuré (MCP)**
- Expérimenter la **connexion SSE** et l’échange dynamique entre des composants hétérogènes
- Intégrer Java et Python dans une solution distribuée


---
