# 🛢️ OilShock — Valorisation et analyse de stratégies sur options Brent

## 📌 Présentation du projet

**OilShock** est un outil interactif développé avec **Microsoft Excel et VBA**, destiné à la valorisation et à l'analyse de stratégies financières sur le pétrole Brent.

Réalisé en binôme dans le cadre d'un projet académique, cet outil combine des modèles de valorisation issus de la finance quantitative et des méthodes de simulation numérique afin d'étudier le comportement de différentes stratégies sur options.

L'objectif est de transformer des modèles mathématiques en un outil opérationnel, permettant à l'utilisateur de modifier les paramètres de marché, d'obtenir des valorisations et d'analyser les profils de gains et de pertes à l'échéance.

## 🎯 Objectifs

- Implémenter le modèle de valorisation **Black-76**.
- Développer une méthode de valorisation par **simulation de Monte-Carlo**.
- Étudier et comparer deux stratégies financières :
  - **Long Call** : achat d'une option d'achat.
  - **Bull Call Spread** : combinaison d'un achat et d'une vente d'options d'achat.
- Analyser les profils de gains et de pertes à l'échéance.
- Concevoir un tableau de bord interactif facilitant l'interprétation des résultats.

## ⚙️ Fonctionnalités principales

### 1. Tableau de bord interactif

L'interface permet à l'utilisateur de renseigner les principaux paramètres du marché et de la stratégie :

| Paramètre | Description |
|---|---|
| F0 | Prix initial du Brent |
| K1 | Prix d'exercice de l'option achetée |
| K2 | Prix d'exercice de l'option vendue |
| r | Taux sans risque |
| σ | Volatilité |
| T | Maturité en années |
| M | Nombre de simulations Monte-Carlo |

L'utilisateur peut sélectionner la stratégie à analyser et lancer les calculs directement depuis le tableau de bord.

### 2. Valorisation avec Black-76

Le modèle Black-76 est utilisé pour calculer le prix théorique des options sur contrats à terme.

Pour une option d'achat :

$$
C = e^{-rT}\left[F_0N(d_1)-KN(d_2)\right]
$$

Avec :

$$
d_1 = \frac{\ln(F_0/K)+\frac{1}{2}\sigma^2T}{\sigma\sqrt{T}}
$$

$$
d_2 = d_1-\sigma\sqrt{T}
$$

où :

- $F_0$ représente le prix initial du future ;
- $K$ représente le prix d'exercice ;
- $r$ représente le taux sans risque ;
- $\sigma$ représente la volatilité ;
- $T$ représente la maturité ;
- $N$ désigne la fonction de répartition de la loi normale centrée réduite.

### 3. Simulation de Monte-Carlo

Une seconde méthode de valorisation repose sur la simulation des trajectoires possibles du prix du Brent à l'échéance.

Le prix simulé est obtenu à partir de :

$$
F_T = F_0 \exp\left(-\frac{1}{2}\sigma^2T+\sigma\sqrt{T}Z\right)
$$

où Z suit une loi normale centrée réduite.
Pour chaque simulation, le programme :

1. Génère une variable aléatoire normale.
2. Calcule un prix simulé à l'échéance.
3. Détermine le payoff de la stratégie.
4. Répète l'opération sur le nombre de simulations choisi.
5. Calcule le payoff moyen actualisé.

Les résultats sont également enregistrés dans une feuille Excel dédiée aux simulations.

### 4. Analyse des stratégies

Deux stratégies sont étudiées :

**Long Call**

Le payoff à l'échéance est :

\[
Payoff=\max(F_T-K,0)
\]

Cette stratégie permet de bénéficier d'une hausse du prix du Brent, avec une perte maximale limitée à la prime payée.

**Bull Call Spread**

Cette stratégie consiste à acheter un Call de strike \(K_1\) et à vendre un Call de strike \(K_2\), avec \(K_1<K_2\).

Son payoff à l'échéance est :

\[
Payoff=\max(F_T-K_1,0)-\max(F_T-K_2,0)
\]

Elle permet de profiter d'une hausse modérée du sous-jacent, tout en limitant le gain potentiel et le coût initial de la stratégie.

### 5. Indicateurs et visualisations

Le tableau de bord affiche notamment :

- Le prix théorique obtenu avec Black-76.
- Le résultat du scénario étudié.
- La perte maximale.
- Le seuil de rentabilité.
- Le gain maximal.
- La comparaison des profils de gains et de pertes.
- L'écart entre les valorisations Black-76 et Monte-Carlo.
- L'erreur standard de la simulation.

Ces indicateurs permettent d'apprécier la performance et les caractéristiques de risque des stratégies étudiées.

## 🖥️ Technologies utilisées

| Technologie | Utilisation |
|---|---|
| Microsoft Excel | Interface et environnement de calcul |
| VBA | Automatisation et développement des fonctions |
| Black-76 | Valorisation théorique des options |
| Monte-Carlo | Valorisation numérique par simulation |
| Loi normale | Génération des variables aléatoires |

## 📂 Organisation du dépôt

```text
OilShock/
│
├── README.md
│
├── OilShock.xlsm
│
├── Documentation/
│   └── Documentation_Projet.pdf
│
├── Screenshots/
│   └── Dashboard.png
│
└── Presentation/
    └── Presentation_Projet.pdf
```

*Les noms et dossiers pourront être adaptés à l'organisation définitive du dépôt.*

## 🚀 Utilisation

1. Télécharger le fichier Excel `OilShock.xlsm`.
2. Ouvrir le fichier avec Microsoft Excel.
3. Autoriser l'exécution des macros VBA si nécessaire.
4. Renseigner les paramètres de marché et de la stratégie.
5. Sélectionner la stratégie à analyser.
6. Cliquer sur **Calculer la stratégie**.
7. Consulter les résultats et les graphiques générés dans le tableau de bord.

## 📊 Aperçu du tableau de bord

Le tableau de bord constitue l'interface principale du projet. Il centralise les paramètres, les résultats de valorisation et les visualisations permettant de comparer les stratégies.

![Tableau de bord OilShock](Screenshots/Dashboard.png)

## 🎓 Contexte académique

Ce projet a été réalisé en binôme dans le cadre de notre formation.

Il nous a permis de mobiliser et d'approfondir des compétences en :

- Finance de marché.
- Produits dérivés et options.
- Valorisation quantitative.
- Méthodes numériques et simulations stochastiques.
- Programmation VBA et automatisation sous Excel.
- Analyse du risque financier.

## 👥 Auteurs

Projet réalisé en binôme par :

- **OGAH Lamessi**
- **ADJAHOSSOU Maxence**

## ⚠️ Avertissement

Ce projet est réalisé dans un cadre exclusivement pédagogique. Les modèles et résultats présentés constituent des outils d'analyse et ne représentent pas des recommandations d'investissement.

---

⭐ Merci de consulter notre projet **OilShock** !
