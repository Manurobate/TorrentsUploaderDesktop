# TorrentsUploaderDesktop

## 🇫🇷 Français

### Présentation
**TorrentsUploaderDesktop** est une application Windows Forms (.NET Framework 4.7.2) qui envoie automatiquement des fichiers `.torrent` vers des dossiers *watch* distants via **FTP explicite sécurisé (FTPES)**. L’objectif est de déposer en lot des torrents côté serveur pour déclencher leur prise en charge par un client torrent (Transmission, ruTorrent, etc.).

### Fonctionnalités principales
- Connexion à un serveur FTPES (hôte, utilisateur, mot de passe).
- Gestion de **4 catégories** de dossiers locaux/distants :
  - Films
  - Séries
  - TV
  - Divers
- Envoi en lot de tous les fichiers présents dans chaque dossier local configuré.
- Barre de progression pendant le transfert.
- Option pour supprimer les fichiers locaux après upload.
- Sauvegarde automatique de la configuration à la fermeture de l’application.

### Configuration
La configuration est stockée dans `App.config` (et persistée dans le fichier `.exe.config` à l’exécution) via les clés suivantes :
- `host`, `user`, `password`
- `localMovies`, `localSeries`, `localTV`, `localOther`
- `remoteMovies`, `remoteSeries`, `remoteTV`, `remoteOther`
- `deleteLocalFiles`

Valeurs par défaut notables :
- Dossiers locaux : `torrents\Films`, `torrents\Series`, `torrents\TV`, `torrents\Divers`
- Dossiers distants : `/.watch/Films`, `/.watch/Series`, `/.watch/TV`, `/.watch`

### Utilisation rapide
1. Ouvrir l’application.
2. Renseigner l’hôte FTPES, l’utilisateur et le mot de passe.
3. Vérifier/ajuster les chemins locaux et distants pour chaque catégorie.
4. Cocher/décocher la suppression des fichiers locaux après transfert.
5. Cliquer sur **Upload**.

### Développement
- Type de projet : Windows Forms (`WinExe`)
- Framework cible : `.NET Framework 4.7.2`
- Dépendance principale : `WinSCPnet.dll` (présente dans `lib/`)

Compilation (exemple, depuis Visual Studio Developer Command Prompt) :
```bash
msbuild TorrentsUploader.sln /p:Configuration=Release
```

### Limitations connues
- Le protocole utilisé est FTP avec sécurité explicite (`FTPES`) uniquement.
- Pas de validation avancée des chemins/fichiers avant envoi.
- Les identifiants sont sauvegardés dans la configuration locale de l’application.

---

## 🇬🇧 English

### Overview
**TorrentsUploaderDesktop** is a Windows Forms app (.NET Framework 4.7.2) that uploads `.torrent` files in batch to remote *watch* folders using **explicit FTPS (FTPES)**. The goal is to drop torrents on a server so a torrent client (Transmission, ruTorrent, etc.) can pick them up automatically.

### Main features
- Connects to an FTPES server (host, username, password).
- Handles **4 local/remote folder categories**:
  - Movies
  - Series
  - TV
  - Other
- Batch upload of all files found in each configured local folder.
- Progress bar during transfers.
- Optional local file deletion after successful upload.
- Automatic settings persistence when closing the app.

### Configuration
Configuration lives in `App.config` (and is persisted to the runtime `.exe.config`) using these keys:
- `host`, `user`, `password`
- `localMovies`, `localSeries`, `localTV`, `localOther`
- `remoteMovies`, `remoteSeries`, `remoteTV`, `remoteOther`
- `deleteLocalFiles`

Notable default values:
- Local folders: `torrents\Films`, `torrents\Series`, `torrents\TV`, `torrents\Divers`
- Remote folders: `/.watch/Films`, `/.watch/Series`, `/.watch/TV`, `/.watch`

### Quick start
1. Launch the app.
2. Fill in FTPES host, username, and password.
3. Review/adjust local and remote paths for each category.
4. Enable/disable deletion of local files after transfer.
5. Click **Upload**.

### Development
- Project type: Windows Forms (`WinExe`)
- Target framework: `.NET Framework 4.7.2`
- Main dependency: `WinSCPnet.dll` (included in `lib/`)

Build example (from Visual Studio Developer Command Prompt):
```bash
msbuild TorrentsUploader.sln /p:Configuration=Release
```

### Known limitations
- Only FTP with explicit security (`FTPES`) is supported.
- No advanced path/file validation before transfer.
- Credentials are stored in the local application configuration.
