# 🎯 Utiliser le format “Given-When-Then” pour découvrir et valider les exigences

---

- https://mambo.io/blog/acceptance-criteria
- https://www.ebgconsulting.com/blog/using-given-when-then-to-discover-and-validate-requirements-2/
  
## 📌 Introduction

Le format **Given-When-Then (GWT)**, popularisé par **Behavior-Driven Development (BDD)**, est un outil puissant pour **capturer les exigences** métier, techniques ou fonctionnelles d’un système de manière **claire, testable et collaborative**. Il permet de structurer des **scénarios** à partir de **User Stories**, tout en intégrant les **règles métiers** et les **conditions préalables (preconditions)**. Ce format favorise la **communication entre les parties prenantes** (métier, développeurs, testeurs).

---

## 🧩 Structure de base

| Élément   | Description                                                             |
| --------- | ----------------------------------------------------------------------- |
| **Given** | Le contexte initial ou l’état du système avant l’action                 |
| **When**  | L’événement déclencheur ou l’action de l’utilisateur                    |
| **Then**  | Le résultat attendu (sortie, changement d’état, règle métier appliquée) |

---

## 💡 Exemple Complet avec : Application bancaire - Virement

### 🧾 **User Story**

> **En tant que** client de la banque,
> **Je veux** effectuer un virement bancaire entre mes comptes,
> **Afin de** pouvoir transférer de l'argent facilement et rapidement.

---

### 📜 **Règles Métier**

1. Le solde du compte source doit être suffisant.
2. Le montant minimum du virement est de 1 €.
3. Le virement entre comptes du même client est instantané.
4. L'utilisateur doit être authentifié.

---

### 🔁 **Condition préalable (Precondition)**

* Le client est connecté à son espace client.
* Le client possède au moins deux comptes bancaires actifs.
* Le compte source a un solde supérieur ou égal au montant du virement.

---

### ✅ **Scénario 1 : Virement réussi**

**Given** que le client est connecté et possède deux comptes avec un solde suffisant,
**When** il saisit un montant de 100 € et valide le virement,
**Then** le montant est débité du compte source et crédité sur le compte destinataire immédiatement,
**And** une confirmation de virement s’affiche.

---

### ❌ **Scénario 2 : Solde insuffisant**

**Given** que le client est connecté et que le compte source a un solde de 50 €,
**When** il essaie de faire un virement de 100 €,
**Then** un message d’erreur s’affiche : “Solde insuffisant”,
**And** le virement n’est pas effectué.

---

### ❌ **Scénario 3 : Utilisateur non authentifié**

**Given** que l’utilisateur n’est pas connecté,
**When** il tente d’accéder à la page de virement,
**Then** il est redirigé vers la page de connexion.

---

### ❌ **Scénario 4 : Montant inférieur à 1 €**

**Given** que le client est connecté et tente un virement de 0,50 €,
**When** il valide l’opération,
**Then** un message d’erreur s’affiche : “Le montant minimum est de 1 €.”

---

## 🧭 Processus en 4 étapes pour découvrir les exigences avec GWT

| Étape | Activité                                                | Résultat attendu               |
| ----- | ------------------------------------------------------- | ------------------------------ |
| 1️⃣   | Identifier les **User Stories** avec le métier          | Liste d’intentions utilisateur |
| 2️⃣   | Éliciter les **règles métiers** liées à chaque story    | Contraintes et validations     |
| 3️⃣   | Définir les **scénarios en GWT**                        | Cas normaux et cas d'erreurs   |
| 4️⃣   | Discuter les **conditions préalables** (états initiaux) | Cas d’entrée valides           |

---

## 🛠️ Bonnes pratiques

* 🧠 Impliquer toutes les parties (PO, développeurs, QA, métier)
* 🎯 Se concentrer sur la **valeur métier**
* 🔍 Couvrir les **cas d’usage, limites, erreurs**
* 🧪 Utiliser ces scénarios comme **base pour les tests automatisés**
* 💬 Revue des scénarios régulièrement avec le métier

---

## 📦 Autres exemples (multi-domaines)

### 🎫 **Application de billetterie**

> **Story** : En tant qu’utilisateur, je veux réserver un billet pour un concert.

* **Given** que l’événement est disponible et qu’il reste des places,
* **When** je sélectionne une place et valide le paiement,
* **Then** je reçois un e-ticket par e-mail.

---

### 🚚 **Application de livraison**

> **Story** : En tant que livreur, je veux marquer une commande comme livrée.

* **Given** que je suis assigné à cette commande,
* **When** je scanne le QR code chez le client,
* **Then** le statut passe à “Livrée” et une notification est envoyée au client.

---

## 🧾 Résumé

| Élément                 | Exemple clé                               |
| ----------------------- | ----------------------------------------- |
| **User Story**          | Transférer de l’argent entre mes comptes  |
| **Règle métier**        | Solde suffisant, montant minimal = 1 €    |
| **Condition préalable** | Client connecté, comptes actifs           |
| **Given-When-Then**     | Décrit les scénarios de succès et d’échec |

---

## 📚 Ressources utiles

* 🟡 [Cucumber](https://cucumber.io/) pour écrire des tests en GWT (BDD)
* 🟢 [SpecFlow](https://specflow.org/) pour .NET
* 🔵 [Behave](https://behave.readthedocs.io/) pour Python
* 📘 Livre : *Specification by Example* – Gojko Adzic

---

## ✅ Conclusion

Le format **Given-When-Then** est un outil **structurant, clair et testable** pour découvrir, valider et documenter les exigences d’un système. Il permet de **relier naturellement les besoins métier, les règles de gestion, et les comportements attendus**, tout en préparant le terrain à la **validation automatique via les tests**. C’est une méthode agile incontournable dans les projets modernes.

---

