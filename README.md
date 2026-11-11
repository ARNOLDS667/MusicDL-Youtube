# 🎵 MusicDL

Télécharge l'application en cliquant ici 👉  [dernière release](https://github.com/ARNOLDS667/MusicDL-Youtube/releases), puis selectionne MusicDl-Setup-...exe

## ✨ Fonctionnalités

- 🔎 Recherche par nom (« artiste titre ») ou par lien : titre, **playlist**, **album** YouTube Music
- 🟢 **Import de playlists Spotify** : colle le lien, chaque titre est retrouvé sur YouTube Music (sans clé d'API)
- 🅴 **Tag « explicit »** : le badge E s'affiche dans iTunes / Apple Music (fichiers M4A)
- 🎯 Choix automatique de la version « officielle » (chaînes *Topic*), en évitant live, remix, karaoké…
- 🏷️ Tags complets : titre, artiste, album, année, **piste n/total**, **disque**, **genre**, **explicit**, **maison de disques**, **résumé de l'album**
- 🎤 Genre intelligent : `Rap Français`, `Rap Ivoirien`, `Rap US`… (genre via Deezer + pays de l'artiste via MusicBrainz)
- 💿 **Albums bien regroupés** pour qu'iTunes rassemble tous les titres
- 🖼️ Pochette carrée intégrée au fichier (HD via Deezer quand elle existe)
- 📝 Paroles intégrées (LRCLIB)
- ⚡ Téléchargements simultanés, annulation, file d'attente avec progression
- ♻️ Historique : les titres déjà téléchargés sont ignorés
- 🔄 Mise à jour automatique de yt-dlp (YouTube change souvent)
- 🎞️ ffmpeg fourni automatiquement si absent de ton système

## 📦 Installation

### Windows : installation en un clic

1. Va dans l'onglet **Releases** du dépôt et télécharge **`MusicDL-Setup-x.y.z.exe`**.
2. Double-clique dessus : l'installation se fait toute seule (sans droits administrateur, sans questions) et crée un raccourci sur le bureau.

> Windows peut afficher « Windows a protégé votre ordinateur » (SmartScreen), car l'installateur n'est pas signé numériquement. Clique sur **Informations complémentaires**, puis **Exécuter quand même**.

Tes réglages et ton historique sont enregistrés dans `%APPDATA%\MusicDL`, et la musique dans `Musique\MusicDL` (modifiable dans les réglages).



## 🚀 Utilisation

### L'application

- **À droite** : YouTube Music intégré (avec boutons précédent / suivant / actualiser / accueil). Cherche et écoute ce que tu veux.
- **À gauche** : un seul champ. Colle un **lien YouTube, YouTube Music ou Spotify** (titre, album, playlist), ou **tape simplement un titre**, puis **⬇ Télécharger**. Plusieurs liens collés d'un coup sont tous pris en compte.
- **📄 Importer** : charge un fichier `.csv` / `.txt` (export de playlist).
- **Options** : forcer un genre ou le tag explicit pour les prochains téléchargements.
- **File d'attente** : progression de chaque titre, annulation individuelle ou globale. Le **Journal** (replié) montre les détails.
- **🛠 Réparer**, **📂 Dossier**, **⚙ Réglages** (format, qualité, dossier, paroles…) en haut.

Pour récupérer le lien d'un titre dans YouTube Music : menu **⋮ > Partager > Copier le lien**, puis colle-le dans le champ.


## 🟢 Importer une playlist Spotify

Colle simplement le lien d'une playlist, d'un album ou d'un titre Spotify dans la zone de texte (ou en ligne de commande). MusicDL lit la liste des titres, puis retrouve chacun sur YouTube Music en choisissant la version dont la **durée** correspond le mieux. Les infos Spotify (titre, artistes, album, numéro de piste, explicit) sont prioritaires sur celles de YouTube.



**Limites à connaître**
- Seules les playlists **publiques** sont lisibles, sans compte ni clé. MusicDL lit la page de partage publique de Spotify (« Intégrer »), car l'API officielle exige désormais un compte Spotify Premium pour créer une application.
- Spotify ne donne qu'une partie des titres d'une longue playlist (environ 50 à 100). Dans ce cas, MusicDL te le signale : exporte la playlist en **CSV** (par exemple avec [Exportify](https://exportify.net)) puis utilise le bouton **📄 Importer** ou `--from-file`.
- Cette lecture n'est pas une API officielle : si Spotify modifie son site, l'import par lien peut cesser de fonctionner. L'import de fichier CSV, lui, reste fiable.
- Seules des **métadonnées** sont lues sur Spotify. L'audio vient toujours de YouTube Music.

**Formats de fichier acceptés**
- `.csv` : export Exportify, TuneMyMusic... (colonnes `Track Name`, `Artist Name(s)`, `Album Name`, `Release Date`, `Track Number`, `Explicit`, `Duration (ms)`, détectées automatiquement)
- `.txt` : un titre par ligne, au format `Artiste - Titre` (ou un lien YouTube / Spotify). Les lignes commençant par `#` sont ignorées.

## 🅴 Le badge « explicit » dans iTunes

MusicDL repère les titres explicites (via Spotify, Deezer et la recherche iTunes / Apple Music) et les marque :

| Format | Balise écrite | Badge dans iTunes / Apple Music |
|---|---|---|
| **M4A** | `rtng` = 1 (comme les fichiers vendus par iTunes) | ✅ affiché |
| MP3 | `ITUNESADVISORY` (personnalisé) | ❌ iTunes n'affiche pas ce badge pour les MP3 |
| FLAC | `ITUNESADVISORY` | ❌ non pris en charge par iTunes |

👉 **Pour voir le E dans iTunes, choisis le format M4A** (⚙ Réglages ou `--format m4a`). Si le badge n'apparaît pas pour un fichier déjà importé, supprime-le de ta bibliothèque iTunes puis réimporte-le : iTunes garde les anciennes informations en mémoire.

La détection est automatique : Spotify, puis Deezer, puis la recherche iTunes / Apple Music en secours. Elle n'est pas infaillible (un titre inconnu de ces catalogues ne sera pas marqué). Dans ce cas :

- coche **🅴 Explicit** avant de télécharger (ou `--explicit` en ligne de commande) pour forcer le tag ;
- ou répare un fichier existant avec **🛠 Réparer** (voir ci-dessous).

La ligne `sources : Deezer ✓ · iTunes ✗ …` affichée sous chaque titre te montre d'où viennent les infos. Tu peux désactiver la détection dans les réglages.

### 🛠 Réparer des fichiers déjà téléchargés

Genre, numéro de piste ou explicit manquants ? Sans retélécharger :

Dans l'interface : bouton **🛠 Réparer**. Les infos déjà présentes (genre, piste, pochette, paroles) sont conservées ; seules les manquantes sont ajoutées.

**Albums éparpillés dans iTunes ?** Sélectionne d'un coup tous les titres de l'album dans **🛠 Réparer** : l'interprète de l'album est corrigé et aligné sur tous les titres (un « Various Artists » choisi volontairement est conservé). Supprime ensuite l'album d'iTunes et réimporte-le.

## 💽 Maison de disques et résumé de l'album

Comme sur la page d'un album dans YouTube Music : MusicDL ajoute la maison de disques (ex. « Wati B / Sony Music France ») et un court résumé de l'album.

- **Maison de disques** : fournie directement par Deezer. Écrite dans `TPUB` (MP3), un tag `LABEL` (M4A, FLAC).
- **Résumé** : une recherche sur Wikipédia (français, puis anglais) retrouve l'article de l'album et en reprend le début, comme le fait YouTube Music lui-même. Écrit dans le commentaire du fichier (`COMM` en MP3, « Commentaire » en M4A/FLAC).
- Si rien n'est trouvé pour un titre (sortie trop récente, pas de page Wikipédia...), ces deux champs restent simplement vides : ça n'empêche jamais le téléchargement.
- Se désactive dans les réglages si tu préfères des téléchargements plus rapides et plus légers en requêtes.

## 🏷️ Comment le genre est déterminé

1. **Deezer** donne le genre de l'album (ex. « Rap/Hip Hop »).
2. **MusicBrainz** donne le pays de l'artiste.
3. Pour le rap et le R&B, les deux sont combinés : `Rap` + `CI` → **Rap Ivoirien**.

La table des pays se modifie dans `COUNTRY_ADJ` (`musicdl_core.py`). Si l'artiste n'est pas trouvé, le genre reste générique (`Rap`). Tu peux toujours forcer le genre avec `--genre` ou le champ « Genre » de l'interface.


## 🛠️ Dépannage

| Message | Solution |
|---|---|
| ⚠ YouTube a changé | `python musicdl.py --update` |
| 🌍 Vidéo bloquée dans ta région | Utilise un VPN |
| 🤖 YouTube limite les requêtes | Attends quelques minutes |
| 🎞 ffmpeg introuvable | `pip install imageio-ffmpeg` ou installe ffmpeg |
| Pas de genre / de numéro de piste | Deezer ou MusicBrainz n'ont pas reconnu le titre : utilise `--genre` |

## ⚖️ Avertissement légal

Cet outil est fourni **à des fins personnelles et éducatives**. Le téléchargement de contenu depuis YouTube peut aller à l'encontre de ses conditions d'utilisation et, selon ton pays, du droit d'auteur. Télécharge uniquement des contenus que tu as le droit de copier (tes propres créations, œuvres libres de droits, contenus sous licence ouverte, ou dans le cadre autorisé par la loi de ton pays). L'auteur décline toute responsabilité quant à l'usage qui en est fait.

## 🙏 Crédits

[yt-dlp](https://github.com/yt-dlp/yt-dlp) · [mutagen](https://github.com/quodlibet/mutagen) · [PyQt6](https://www.riverbankcomputing.com/software/pyqt/) · [CustomTkinter](https://github.com/TomSchimansky/CustomTkinter) · [Deezer API](https://developers.deezer.com) · [iTunes Search API](https://performance-partners.apple.com/search-api) · [MusicBrainz](https://musicbrainz.org) · [LRCLIB](https://lrclib.net) · 

## 📄 Licence

MIT, voir [LICENSE](LICENSE).
