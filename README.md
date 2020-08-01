# DiscordBBSearch
Recherches effectuées le 30/07/'20, j'ai pu distinguer plusieurs attributs pottentiellement exploitables, en provenance des IOTs utilisés par Discord.
## Prologue assez salé
External Obfuscated Cloudflare API Injected | src > cdn-cgi/bm/cv/2172558837/api.js<br/>
La reformation du fichier attendu a été corrompu, il a donc fait un Call inattendu sur le WAF ce qui a invoqué l'API globale.<br/></br>
<img src="https://media.discordapp.net/attachments/738135945701753409/738256958066262016/unknown.png?width=1525&height=890"/><br/>
## Analyse ampiative
Cloudflare résumé implémentation API Protection DDoS.<br/><br/>
<img src="https://media.discordapp.net/attachments/736536361258975253/738229995339513866/unknown.png?width=1838&height=338"/><br/><br/>
## Fonction Base64
Fonction base64 décodée - Webpack fichier root (potentiel chemin vers repos internes privés).<br/><br/>
<img src="https://media.discordapp.net/attachments/736536361258975253/738232859684372490/unknown.png"/><br/><br/>
## KeyChain - OBJ
Element-based computation (sûrement en rapport avec la keychain qui débloque les fonctions collectées).<br/><br/>
<img src="https://media.discordapp.net/attachments/736536361258975253/738233662033625239/unknown.png"/><br/><br/>
## Épilogue et conclusion
On peut sûrement utiliser le contrôleur webpack comme objet d'insertion de fichiers et mener le tout vers une LFI voire RFI qui pourrait nous faire remonter à exécuter du code arbitraire à distance > RCE. De plus que le contribwebpack a plusieurs fonctions complémentaires qui sont sûrement utilisés par Discord.<br/><br/>
<img src="https://media.discordapp.net/attachments/736536361258975253/738234703928229928/unknown.png"/>
