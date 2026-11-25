# Son propre serveur RustDesk dans un conteneur LXD — présentation

Diaporama [reveal.js](https://revealjs.com/) tiré du tutoriel « Installer un serveur RustDesk dans un conteneur LXD » (blog [labo.hacktech.dev](https://labo.hacktech.dev/), dépôt [HackTechDev/didacticiel_rustdesk](https://github.com/HackTechDev/didacticiel_rustdesk)).

## Lancer la présentation

```bash
./runServer.sh
```

Puis ouvrir <http://127.0.0.1:40779> dans le navigateur. Les fichiers de reveal.js déjà compilés (`dist/`) sont fournis : aucune installation Node n'est nécessaire.

## Contenu

| Fichier | Rôle |
|---|---|
| `index.html` | Le diaporama (slides et notes d'orateur) |
| `assets/rustdesk.css` | Le style propre à la présentation (surcharge le thème `black`) |
| `assets/rustdesk/` | Captures d'écran du client RustDesk (PC et Android) |

Déroulé : ouverture, comprendre (hbbs/hbbr, LXD), le réseau (DNAT, `nat=true`, pare-feu), installer, les clients, démo (contrôle du portable depuis un smartphone Android), dépanner, exploiter (sauvegarde, mise à jour, sécurité), conclusion, puis des slides de réserve.

## Naviguer

| Touche | Action |
|---|---|
| ← → | Partie précédente / suivante |
| ↑ ↓ | Détail d'une partie (slides verticales) |
| **S** | Vue orateur (notes, slide suivante, chronomètre) |
| **F** | Plein écran |
| Échap | Vue d'ensemble de toutes les slides |
| Alt + clic | Zoom sur une capture |

## Afficher les notes d'orateur

Appuyer sur la touche **S** pendant la présentation. Une **fenêtre séparée** s'ouvre (la « vue orateur ») avec :

- la slide en cours et la suivante ;
- les notes de la slide en cours ;
- l'heure et un chronomètre (cliquer dessus pour le remettre à zéro).

Les deux fenêtres restent synchronisées : on peut avancer avec les flèches dans l'une ou l'autre.

**En salle, avec un projecteur :**

1. Brancher le projecteur en mode **écran étendu**, pas en recopie.
2. Mettre la fenêtre de la présentation sur le projecteur, en plein écran avec **F**.
3. Garder la vue orateur sur l'écran du portable : vous seul voyez les notes.

**Si rien ne s'ouvre** : le navigateur a sans doute bloqué la fenêtre surgissante. Autoriser les pop-ups pour `127.0.0.1:40779` (icône dans la barre d'adresse), puis réappuyer sur **S**.

**Pour répéter seul** : ajouter `?showNotes=true` à l'adresse (<http://127.0.0.1:40779/?showNotes=true>). Les notes s'affichent alors en bas de chaque slide. Le public les verrait aussi : ce mode n'est donc pas fait pour la séance.

> Astuce : `?fragments=false` affiche tous les éléments d'une slide d'un coup, sans cliquer (pratique pour relire).

---

## À propos de reveal.js

<p align="center">
  <a href="https://revealjs.com">
  <img src="https://hakim-static.s3.amazonaws.com/reveal-js/logo/v1/reveal-black-text-sticker.png" alt="reveal.js" width="500">
  </a>
  <br><br>
  <a href="https://github.com/hakimel/reveal.js/actions"><img src="https://github.com/hakimel/reveal.js/actions/workflows/test.yml/badge.svg"></a>
  <a href="https://slides.com/"><img src="https://static.slid.es/images/slides-github-banner-320x40.png?1" alt="Slides" width="160" height="20"></a>
</p>

reveal.js is an open source HTML presentation framework. It enables anyone with a web browser to create beautiful presentations for free. Check out the live demo at [revealjs.com](https://revealjs.com/).

The framework comes with a powerful feature set including [nested slides](https://revealjs.com/vertical-slides/), [Markdown support](https://revealjs.com/markdown/), [Auto-Animate](https://revealjs.com/auto-animate/), [PDF export](https://revealjs.com/pdf-export/), [speaker notes](https://revealjs.com/speaker-view/), [LaTeX typesetting](https://revealjs.com/math/), [syntax highlighted code](https://revealjs.com/code/) and an [extensive API](https://revealjs.com/api/).

---

Want to create reveal.js presentation in a graphical editor? Try <https://slides.com>. It's made by the same people behind reveal.js.

---

### Getting started

- 🚀 [Install reveal.js](https://revealjs.com/installation)
- 👀 [View the demo presentation](https://revealjs.com/demo)
- 📖 [Read the documentation](https://revealjs.com/markup/)
- 🖌 [Try the visual editor for reveal.js at Slides.com](https://slides.com/)
- 🎬 [Watch the reveal.js video course (paid)](https://revealjs.com/course)

---

<div align="center">
  MIT licensed | Copyright © 2011-2026 Hakim El Hattab, https://hakim.se
</div>
