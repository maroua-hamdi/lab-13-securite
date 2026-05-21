# LAB 13 : Bypass de la Détection de Root Android avec Objection

**Réalisé par : Hamdi Maroua**  
**Cours : Sécurité des applications mobiles**  
**Thème : Android Root Detection Bypass avec Frida et Objection**

---

## 1. Objectif du lab

Ce laboratoire a pour objectif de comprendre le fonctionnement d’une protection de type **Root Detection** dans une application Android, puis d’utiliser l’outil **Objection** afin d’analyser l’application dans un environnement de test.

L’application utilisée affiche un message d’erreur lorsqu’elle détecte que l’appareil Android est rooté.  
Le but est donc d’observer ce comportement, de lancer Objection, puis de tester le contournement de cette détection dans un cadre pédagogique.

---




## 3. Présentation du lab

Cette capture représente la page du laboratoire avec les différentes étapes à suivre : prérequis, installation d’Objection, préparation de l’appareil Android, lancement de l’application cible, validation du bypass et références utiles.

<img width="824" height="405" alt="pic1" src="https://github.com/user-attachments/assets/4925ad69-a6ef-426a-a914-c976a9c21380" />

---

## 4. Installation d’Objection

La première étape consiste à installer ou mettre à jour l’outil Objection avec Python et pip.

Commande utilisée :

```powershell
pip install --upgrade objection
```

Cette commande installe Objection ainsi que les dépendances nécessaires pour interagir avec une application Android pendant son exécution.

<img width="1058" height="224" alt="pic2" src="https://github.com/user-attachments/assets/d85cb467-81d3-4d99-b03f-6e9ae8a34fae" />

---

## 5. Vérification de l’installation

Après l’installation, il faut vérifier qu’Objection est correctement installé.

Commandes utilisées :

```powershell
objection --help
```

```powershell
objection version
```

La commande `objection --help` affiche la liste des options et commandes disponibles.  
La commande `objection version` permet de vérifier la version installée.

---

## 6. Lancement d’Objection sur l’application cible

Une fois l’application installée et lancée dans l’émulateur Android, on peut attacher Objection au package de l’application.

Commande utilisée :

```powershell
objection -n com.pwnsec.firestorm explore
```

Dans ce lab, Objection affiche un avertissement indiquant que la commande `explore` est dépréciée et qu’il est préférable d’utiliser :

```powershell
objection start
```

Après l’attachement, une session interactive s’ouvre et permet d’exécuter des commandes sur l’application cible.
<img width="394" height="798" alt="pic4" src="https://github.com/user-attachments/assets/46cd78e1-3609-4032-9f43-2d1beb81fe68" />


---

## 7. Observation de l’application Android

L’application cible utilisée dans ce lab s’appelle **Uncrackable1**.  
Elle contient un champ de saisie intitulé :

```text
Enter the Secret String
```

et un bouton :

```text
VERIFY
```

Cette étape permet de vérifier que l’application est bien lancée dans l’émulateur Android avant de tester la détection root.
<img width="1036" height="159" alt="pic5" src="https://github.com/user-attachments/assets/b4866697-a75f-4d41-82a1-1643fc738642" />

---

## 8. Détection du root par l’application

Lorsque l’application détecte que l’appareil Android est rooté, elle affiche le message suivant :

```text
Root detected!
This is unacceptable. The app is now going to exit.
```

Ce message indique que l’application bloque son fonctionnement lorsqu’elle détecte un environnement rooté.

<img width="306" height="654" alt="pic6" src="https://github.com/user-attachments/assets/ff534b77-a083-4231-89b3-83610119e751" />

---

## 9. Principe du bypass

Le bypass consiste à empêcher l’application de confirmer que l’environnement est rooté.  
Dans un environnement de laboratoire, Objection permet de tester certains contournements dynamiques.

Commande utilisée dans la session Objection :

```text
android root disable
```

Cette commande permet de désactiver certains contrôles de root détectés par Objection pendant l’exécution de l’application.

---

## 10. Résultat attendu

Après le lancement d’Objection et l’application du bypass, l’objectif est que l’application ne bloque plus immédiatement son exécution avec le message :

```text
Root detected!
```

Le lab permet donc de comprendre :

- comment une application Android détecte un appareil rooté ;
- comment Objection s’attache à une application Android ;
- comment tester dynamiquement une protection anti-root ;
- pourquoi les protections côté client ne sont pas suffisantes seules.

---

## 11. Importance de la sécurité mobile

La détection de root est une mesure de protection importante dans les applications mobiles, surtout lorsqu’elles manipulent des données sensibles.

Cependant, cette protection peut être contournée si elle est uniquement réalisée côté client.  
Pour renforcer la sécurité d’une application Android, il est recommandé d’utiliser plusieurs couches de protection :

- détection de root ;
- détection de Frida ;
- vérification d’intégrité de l’application ;
- obfuscation du code ;
- contrôle côté serveur ;
- protection des données sensibles ;
- journalisation des événements suspects.

---

## 12. Conclusion

Ce laboratoire montre comment analyser une application Android protégée par une détection root.  
À travers l’utilisation de Frida et Objection, on peut comprendre les limites des protections côté client et l’importance d’une approche de sécurité multicouche.

Ce travail a été réalisé uniquement dans un cadre pédagogique et dans un environnement de test contrôlé.

---

## Auteur

**Hamdi Maroua**  
**LAB 13 : Bypass de la Détection de Root Android avec Objection**  
**Cours : Sécurité des applications mobiles**
