# 🔧 Installation du Framework Hive

Cette page détaille toutes les étapes pour installer et exécuter localement le framework Hive dans un environnement de développement FiveM.

---

## ⚙️ Prérequis

Avant de commencer, assure-toi d’avoir installé :

- [FiveM FXServer](https://docs.fivem.net/docs/server-manual/setting-up-a-server/)
- [MariaDB](https://mariadb.org/) (ou un serveur MySQL compatible)
- Un éditeur de code (VSCode recommandé)

---

## 📦 Dépendances requises (ressources externes)

Les ressources suivantes doivent être installées dans `resources/` :

- [oxmysql](https://github.com/overextended/oxmysql/releases) *Télécharger la dernieres release*
- [bob74_ipl](https://github.com/DevSekai/bob74_ipl) *Télécharger mon fork, il possède certaines modifications essentiel au projet*


## 🧪 Installation locale

1. **Demande d'accés au framework** :

Ce framework étant privé et protégé, il n’est pas accessible via un dépôt GitHub public.
Si tu fais partie de l’équipe de développement, une version te sera transmise directement sous forme d’archive (escrow) contenant tous les fichiers nécessaires à son installation.

Pour toute demande d’accès ou de mise à jour, merci de contacter l’administrateur du projet.

2. **server.cfg** :

Vous devrez organiser votre server.cfg comme ci dessous
```cfg
# Only change the IP if you're using a server with multiple network interfaces, otherwise change the port only.
endpoint_add_tcp "0.0.0.0:30120"
endpoint_add_udp "0.0.0.0:30120"

set mysql_connection_string "mysql://root:MDPBDD@127.0.0.1:3306/NOMBDD?charset=utf8mb4"
set mysql_slow_query_warning 150
set mysql_debug true

# These resources will start by default.
ensure mapmanager
ensure chat
ensure spawnmanager
ensure sessionmanager
ensure basic-gamemode
ensure hardcap
ensure rconlog
ensure baseevents

# Dependencies
ensure [Deps] # OxMysql & Bob74ipl doivent être ensure avant le framework et ressource

# Hive
ensure Framework

# Vos ressources

# This allows players to use scripthook-based plugins such as the legacy Lambda Menu.
# Set this to 1 to allow scripthook. Do note that this does _not_ guarantee players won't be able to use external plugins.
sv_scriptHookAllowed 0

# Uncomment this and set a password to enable RCON. Make sure to change the password - it should look like set rcon_password "YOURPASSWORD"

# Set your server's hostname. This is not usually shown anywhere in listings.
sv_hostname "Hive"

# Set your server's Project Name
sets sv_projectName "Hive"

# Set your server's Project Description
sets sv_projectDesc "Hive advanced roleplay server"

# Set Game Build (https://docs.fivem.net/docs/server-manual/server-commands/#sv_enforcegamebuild-build)
sv_enforceGameBuild 3407 # Essentiels pour avoir les derniers ajout de GTA V


# Remove the `#` from the below line if you want your server to be listed as 'private' in the server browser.
# Do not edit it if you *do not* want your server listed as 'private'.
# Check the following url for more detailed information about this:
# https://docs.fivem.net/docs/server-manual/server-commands/#sv_master1-newvalue
#sv_master1 ""

# enable OneSync (required for server-side state awareness)
set onesync on

# Server player slot limit (see https://fivem.net/server-hosting for limits)
sv_maxclients 48

# Steam Web API key, if you want to use Steam authentication (https://steamcommunity.com/dev/apikey)
# -> replace "" with the key
set steam_webApiKey ""

# License key for your server (https://portal.cfx.re)
sv_licenseKey "YOUR_LICENSE_KEY" # Celle que vous m'aurez communiquer lors de la demande d'acces au framework
```