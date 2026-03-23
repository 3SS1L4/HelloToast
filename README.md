# HelloToast

<div align="center">

> Application Android de démonstration — compteur interactif avec Toast

<video src="assets/record_toast_lab.mp4" width="300" autoplay loop muted playsinline></video>


<br/><br/>

![Android](https://img.shields.io/badge/Android-API%2021%2B-3DDC84?style=flat-square&logo=android&logoColor=white)
![Java](https://img.shields.io/badge/Java-8%2B-007396?style=flat-square&logo=openjdk&logoColor=white)
![Lab](https://img.shields.io/badge/Lab-Mobile%20Android-555?style=flat-square)
![Status](https://img.shields.io/badge/Statut-Complet-success?style=flat-square)

</div>

---

## Présentation

**HelloToast** est une application Android native développée dans le cadre d'un lab de développement mobile. Elle illustre les mécanismes fondamentaux d'une Activity Android : liaison entre le layout XML et la logique Java, gestion des interactions utilisateur, et mise à jour dynamique de l'interface.

L'application propose deux fonctionnalités :

- Afficher un **Toast** — un message temporaire qui apparaît en bas de l'écran
- **Incrémenter un compteur** — la valeur se met à jour en temps réel à chaque appui

---

## Architecture

```
┌─────────────────────────┐        ┌──────────────────────────────┐
│   activity_main.xml     │        │      MainActivity.java        │
│  ───────────────────    │        │  ──────────────────────────   │
│  TextView  text_count   │ ◄──────│  textCount.setText(count)     │
│  Button  button_toast   │ ──────►│  Toast.makeText(...).show()   │
│  Button  button_count   │ ──────►│  count++ → setText()          │
└─────────────────────────┘        └──────────────────────────────┘
         UI / Layout                        Logique / Événements
```

Le XML définit **ce qui est affiché**, le Java définit **ce qui se passe**. La communication entre les deux se fait via les identifiants : `android:id` dans le XML, `findViewById()` dans le Java.

---

## Structure du projet

```
HelloToast/
├── assets/
│   └── record_toast_lab.mp4                        ← démonstration visuelle
├── app/src/main/
│   ├── java/com/example/hellotoast/
│   │   └── MainActivity.java           ← logique de l'application
│   └── res/layout/
│       └── activity_main.xml           ← interface utilisateur
└── README.md
```

---

## Référence des fichiers

### `MainActivity.java`

| Élément | Description |
|---|---|
| `private int count` | Variable d'état — stocke la valeur du compteur |
| `private TextView textCount` | Référence Java vers le composant d'affichage |
| `onCreate()` | Point d'entrée appelé automatiquement au démarrage |
| `setContentView(R.layout.activity_main)` | Lie ce fichier Java au layout XML |
| `findViewById(R.id.xxx)` | Récupère un composant de l'écran par son identifiant |
| `setOnClickListener(v -> { ... })` | Installe un écouteur de clic sur un bouton |
| `Toast.makeText(this, "...", LENGTH_SHORT).show()` | Affiche un message temporaire (2 secondes) |
| `textCount.setText(String.valueOf(count))` | Met à jour le texte affiché dynamiquement |

### `activity_main.xml`

| Composant | `android:id` | Rôle |
|---|---|---|
| `LinearLayout` | — | Conteneur vertical centré, fond `#1A1A1A` |
| `TextView` | `text_count` | Affiche la valeur du compteur — mis à jour par Java |
| `Button` | `button_toast` | Déclenche l'affichage du message Toast |
| `Button` | `button_count` | Déclenche l'incrémentation du compteur |

---

## Concepts illustrés

| Concept | Implémentation |
|---|---|
| Liaison XML ↔ Java | `setContentView()` + `findViewById()` |
| Événements utilisateur | `setOnClickListener()` avec lambda `v -> {}` |
| Mise à jour de l'interface | `setText()` appelé à chaque clic |
| Feedback non intrusif | `Toast.makeText().show()` |
| État entre les interactions | Variable `count` maintenue dans la classe |

---

## Prérequis

| Outil | Version |
|---|---|
| Android Studio | Arctic Fox 2020.3.1+ |
| SDK Android | API 21 (Android 5.0+) |
| Java | 8+ |

---

## Installation

```bash
# Cloner le dépôt
git clone https://github.com/3SS1L4/HelloToast.git

# Ouvrir dans Android Studio
# File → Open → sélectionner le dossier HelloToast

# Lancer l'application
# Run → Run 'app'   ou   Shift + F10
```

---

## Auteur

AMSOU ISMAIL
