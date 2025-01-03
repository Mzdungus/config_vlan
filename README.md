La configuration des VLANs est essentielle pour segmenter un réseau en domaines logiques, isolant les trafics pour des groupes spécifiques (bureaux, départements). Pour cela, nous avons utilisé des équipements comme un routeur Cisco 2901 et un switch Cisco 2950-24, configurés via CLI. Chaque VLAN a été associé à un sous-réseau unique (par exemple, 192.168.10.0/24 pour VLAN 10 et 192.168.20.0/24 pour VLAN 20), évitant ainsi les conflits d'adresses IP. Les VLANs ont été créés sur le switch avec des ports affectés à chaque VLAN pour segmenter physiquement les connexions. Le routage inter-VLAN a été mis en place en configurant des sous-interfaces sur le routeur, utilisant l'encapsulation dot1Q pour permettre la communication entre les VLANs tout en maintenant leur isolation.

Ces configurations ont été sauvegardées et structurées pour une publication sur GitHub, permettant une collaboration et une documentation détaillée. Les scripts CLI pour le switch et le routeur, un fichier Packet Tracer pour la simulation, et un README documentant chaque étape ont été inclus. Le README décrit les objectifs, l'architecture réseau et les instructions détaillées pour reproduire ou modifier la configuration. Cette approche garantit une organisation claire, facilite le dépannage et encourage le partage de solutions réseau optimales avec d’autres administrateurs et collaborateurs. Le projet est maintenant disponible sur une plateforme collaborative, renforçant l’apprentissage et l’adoption des meilleures pratiques en gestion réseau.
 
 VLAN Configuration Project

**Objectifs**
1. Isoler les départements en créant des VLANs logiques.
2. Permettre la communication inter-VLAN via le routage inter-VLAN.
3. Documenter les configurations pour faciliter leur réutilisation.

## **Architecture Réseau**
- Routeur : Cisco 2901
- Switch : Cisco 2950-24
- Plages IP des VLANs :
  - VLAN 10 (Bureau1) : 192.168.10.0/24
  - VLAN 20 (Bureau2) : 192.168.20.0/24

## **Instructions**
### Étape 1 : Configuration des VLANs sur le switch
1. Connectez-vous au switch via CLI.
2. Créez les VLANs avec les commandes ci-dessous :
   ```bash
   vlan 10
   name Bureau1
   vlan 20
   name Bureau2
