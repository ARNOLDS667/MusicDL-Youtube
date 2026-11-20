# 🎵 Darkyout

Télécharge l'application en cliquant ici 👉  [dernière release](https://github.com/ARNOLDS667/MusicDL-Youtube/releases), puis selectionne MusicDl-Setup-...exe
> Anciennement **MusicDL**. Même moteur, nouvelle interface sombre avec **lecteur intégré** et prise en charge de **SoundCloud**.

Télécharge de la musique depuis **YouTube**, **YouTube Music**, **SoundCloud** et **Spotify** (playlists, métadonnées) en **MP3, M4A ou FLAC**, avec tout ce qu'il faut pour une bibliothèque propre : pochette, artiste, album, année, **genre**, **numéro de piste** et **paroles**. 
Application de bureau (interface sombre + lecteur), ou ligne de commande.

## ✨ Fonctionnalités

- ☁️ **SoundCloud** : colle un lien de titre, de playlist (`/sets/`) ou de profil d'artiste, ou cherche directement sur SoundCloud depuis la barre de recherche
- ▶️ **Lecteur intégré** (style Spotify / Apple Music) : pochette, forme d'onde cliquable, précédent / suivant, aléatoire, répétition, volume, **paroles synchronisées** (`.lrc`) et mini-lecteur toujours visible
- ❤️ Favoris, titres récents, vitesse / taille / progression du téléchargement en direct

- 🔎 Recherche par nom (« artiste titre ») ou par lien : titre, **playlist**, **album** YouTube Music
- 🔍 **Recherche intégrée avec vignettes** : plusieurs résultats à comparer (pochette, artiste, durée) sans ouvrir YouTube Music, utile pour éviter le VPN sur l'usage courant
- 📝 **Paroles synchronisées** (`.lrc`) en plus de celles intégrées au fichier, quand elles existent
- 💿 **Playlist `.m3u`** générée automatiquement pour un album ou une playlist téléchargé
- ✏️ **Éditeur de tags manuel** : corrige genre, album, pochette, maison de disques... à la main, en complément de la détection automatique
- 🆕 **Vérification des mises à jour** : Darkyout lui-même et yt-dlp (celui-ci se met à jour automatiquement, même dans l'application installée)
- 🔁 **File d'attente persistante** : reprise automatique des téléchargements après un plantage ou une fermeture imprévue
- 🟢 **Import de playlists Spotify** : colle le lien, chaque titre est retrouvé sur YouTube Music (sans clé d'API)
- 🅴 **Tag « explicit »** : le badge E s'affiche dans iTunes / Apple Music (fichiers M4A)
- 🎯 Choix automatique de la version « officielle » (chaînes *Topic*), en évitant live, remix, karaoké…
- 🏷️ Tags complets : titre, artiste, album, année, **piste n/total**, **disque**, **genre**, **explicit**, **maison de disques**, **résumé de l'album**
- 🎤 Genre intelligent : `Rap Français`, `Rap Ivoirien`, `Rap US`… (genre via Deezer + pays de l'artiste via MusicBrainz)
- 💿 **Albums bien regroupés** : l'interprète de l'album est l'artiste principal (« KRM »), jamais la liste des invités (« KRM, TRK. »), pour qu'iTunes rassemble tous les titres
- 🖼️ Pochette carrée intégrée au fichier (HD via Deezer quand elle existe)
- 📝 Paroles intégrées (LRCLIB)
- ⚡ Téléchargements simultanés, annulation, file d'attente avec progression
- ♻️ Historique : les titres déjà téléchargés sont ignorés
- 🔄 Mise à jour automatique de yt-dlp (YouTube change souvent)
- 🎞️ ffmpeg fourni automatiquement si absent de ton système

## 📦 Installation

### Windows : installation en un clic

1. Va dans l'onglet **Releases** du dépôt et télécharge **`Darkyout-Setup-x.y.z.exe`**.
2. Double-clique dessus : l'installation se fait toute seule (sans droits administrateur, sans questions) et crée un raccourci sur le bureau.

> Windows peut afficher « Windows a protégé votre ordinateur » (SmartScreen), car l'installateur n'est pas signé numériquement. Clique sur **Informations complémentaires**, puis **Exécuter quand même**.

Tes réglages et ton historique sont enregistrés dans `%APPDATA%\Darkyout`, et la musique dans `Musique\Darkyout` (modifiable dans les réglages).


## 🚀 Utilisation

### L'application

- **Barre de recherche (en haut)** : colle un **lien YouTube, YouTube Music, SoundCloud ou Spotify** (titre, album, playlist) puis **Entrée** pour télécharger, ou tape un titre pour voir les résultats (pochette, artiste, durée) et choisis **YouTube** ou **SoundCloud** comme source. Plusieurs liens collés d'un coup sont tous pris en compte.
- **Downloads** : dernier titre téléchargé (forme d'onde, format, débit), barre de téléchargement (vitesse, taille), dossier de destination (**Choisir un dossier**), sources prises en charge (cliquer sur une carte règle la source de recherche) et titres précédents.
- **Player** : toute ta bibliothèque (le dossier de téléchargement), lecture, file, volume et paroles. Un clic sur la forme d'onde déplace la lecture.
- **Menu « D » (en haut à droite)** : réglages (format, qualité, dossier, genre forcé, tag explicit), import CSV / TXT, éditeur de tags, réparation de fichiers.
- **Cloche** : journal détaillé des opérations.

Logos : les cartes **Spotify / YouTube / SoundCloud** utilisent des icônes neutres. Pour afficher les logos officiels, dépose `spotify.png`, `youtube.png` et `soundcloud.png` dans `assets/brands/` (respecte leurs chartes graphiques).



## 🟢 Importer une playlist Spotify

Colle simplement le lien d'une playlist, d'un album ou d'un titre Spotify dans la zone de texte (ou en ligne de commande). Darkyout lit la liste des titres, puis retrouve chacun sur YouTube Music en choisissant la version dont la **durée** correspond le mieux. Les infos Spotify (titre, artistes, album, numéro de piste, explicit) sont prioritaires sur celles de YouTube.

**Limites à connaître**
- Seules les playlists **publiques** sont lisibles, sans compte ni clé. Darkyout lit la page de partage publique de Spotify (« Intégrer »), car l'API officielle exige désormais un compte Spotify Premium pour créer une application.
- Spotify ne donne qu'une partie des titres d'une longue playlist (environ 50 à 100). Dans ce cas, Darkyout te le signale : exporte la playlist en **CSV** (par exemple avec [Exportify](https://exportify.net)) puis utilise le bouton **📄 Importer** ou `--from-file`.
- Cette lecture n'est pas une API officielle : si Spotify modifie son site, l'import par lien peut cesser de fonctionner. L'import de fichier CSV, lui, reste fiable.
- Seules des **métadonnées** sont lues sur Spotify. L'audio vient toujours de YouTube Music.

**Formats de fichier acceptés**
- `.csv` : export Exportify, TuneMyMusic... (colonnes `Track Name`, `Artist Name(s)`, `Album Name`, `Release Date`, `Track Number`, `Explicit`, `Duration (ms)`, détectées automatiquement)
- `.txt` : un titre par ligne, au format `Artiste - Titre` (ou un lien YouTube / Spotify). Les lignes commençant par `#` sont ignorées.



### 🛠 Réparer des fichiers déjà téléchargés

Genre, numéro de piste ou explicit manquants ? Sans retélécharger :

Dans l'interface : bouton **🛠 Réparer**. Les infos déjà présentes (genre, piste, pochette, paroles) sont conservées ; seules les manquantes sont ajoutées.

**Albums éparpillés dans iTunes ?** Sélectionne d'un coup tous les titres de l'album dans **🛠 Réparer** : l'interprète de l'album est corrigé et aligné sur tous les titres (un « Various Artists » choisi volontairement est conservé). Supprime ensuite l'album d'iTunes et réimporte-le.

## 🔍 Recherche intégrée (sans ouvrir YouTube Music)

Tape un titre (pas un lien) dans la barre du haut puis appuie sur **Entrée** : Darkyout affiche plusieurs résultats avec leur pochette, l'artiste et la durée, directement dans l'application (page de résultats, avec le choix **YouTube** / **SoundCloud**). Sur YouTube, c'est une recherche `youtube.com` classique, généralement accessible même quand `music.youtube.com` est bloqué dans ta région — ça réduit le besoin de VPN pour l'usage courant. Clique sur **Télécharger** à côté du résultat choisi.

## 📝 Paroles synchronisées (.lrc)

En plus des paroles intégrées au fichier, Darkyout enregistre un fichier `.lrc` à côté du morceau quand LRCLIB propose une version synchronisée (texte qui défile au bon moment). Lu par VLC, foobar2000 et la plupart des lecteurs qui affichent les paroles. Si seul le texte brut existe, seul le tag intégré est écrit (pas de fichier `.lrc`).

## 💿 Playlist .m3u automatique

Télécharger un album ou une playlist crée aussi un fichier `.m3u` du même nom dans `Downloads/`, qui liste les morceaux dans l'ordre. Pratique pour les retrouver et les lire à la suite, puisque tout reste dans un seul dossier.

## 🔁 File d'attente persistante

Si l'application se ferme ou plante pendant des téléchargements (coupure de courant, plantage), ils reprennent automatiquement au prochain lancement : Darkyout s'en souvient via un petit fichier dans son dossier de données. Les téléchargements déjà terminés, en erreur ou annulés ne sont jamais repris.

## 💽 Maison de disques et résumé de l'album

Comme sur la page d'un album dans YouTube Music : Darkyout ajoute la maison de disques (ex. « Wati B / Sony Music France ») et un court résumé de l'album.

- **Maison de disques** : fournie directement par Deezer. Écrite dans `TPUB` (MP3), un tag `LABEL` (M4A, FLAC).
- **Résumé** : une recherche sur Wikipédia (français, puis anglais) retrouve l'article de l'album et en reprend le début, comme le fait YouTube Music lui-même. Écrit dans le commentaire du fichier (`COMM` en MP3, « Commentaire » en M4A/FLAC).
- Si rien n'est trouvé pour un titre (sortie trop récente, pas de page Wikipédia...), ces deux champs restent simplement vides : ça n'empêche jamais le téléchargement.
- Se désactive dans les réglages si tu préfères des téléchargements plus rapides et plus légers en requêtes.

## ✏️ Éditeur de tags manuel

Bouton **✏ Éditer** : choisis un fichier déjà téléchargé et corrige directement titre, artiste, album, interprète de l'album, année, genre, maison de disques, numéros de piste/disque, explicit, pochette (changer ou supprimer), description et paroles. Utile quand la détection automatique se trompe ou ne trouve rien pour un titre précis. Les champs non modifiés restent inchangés.

## 🆕 Mises à jour

Darkyout vérifie une fois par jour (désactivable dans les réglages) :
- **yt-dlp** : téléchargé et prêt à l'emploi au prochain démarrage, **y compris dans l'application installée** — pas besoin d'attendre une nouvelle version de Darkyout quand YouTube change quelque chose.
- **Darkyout** : si une nouvelle version est publiée sur GitHub, une bannière apparaît avec un lien direct vers la page de téléchargement.

Pour activer la vérification de Darkyout, renseigne `GITHUB_REPO = "ton-compte/ton-dépôt"` en haut de `darkyout_core.py` (le dépôt **public**, celui où tu publies les Releases).

## 🌍 Pas de VPN intégré

Darkyout n'embarque pas de VPN ni de serveur relais : ça demanderait une infrastructure payante à faire tourner en continu. Si YouTube Music est limité dans ton pays, deux pistes gratuites :
- La **recherche intégrée** (🔍) passe par `youtube.com`, pas `music.youtube.com` : si seul ce dernier est restreint chez toi, elle peut suffire sans VPN.
- Sinon, [ProtonVPN](https://protonvpn.com) a une offre gratuite sans limite de temps ni de volume de données (juste un choix de pays restreint), une alternative aux VPN gratuits habituels limités en données.


## 🛠️ Dépannage

| Message | Solution |
|---|---|
| ⚠ YouTube a changé | `python darkyout.py --update` |
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

