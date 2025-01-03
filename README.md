La configuration des VLANs est essentielle pour segmenter un réseau en domaines logiques, isolant les trafics pour des groupes spécifiques (bureaux, départements). Pour cela, nous avons utilisé des équipements comme un routeur Cisco 2901 et un switch Cisco 2950-24, configurés via CLI. Chaque VLAN a été associé à un sous-réseau unique (par exemple, 192.168.10.0/24 pour VLAN 10 et 192.168.20.0/24 pour VLAN 20), évitant ainsi les conflits d'adresses IP. Les VLANs ont été créés sur le switch avec des ports affectés à chaque VLAN pour segmenter physiquement les connexions. Le routage inter-VLAN a été mis en place en configurant des sous-interfaces sur le routeur, utilisant l'encapsulation dot1Q pour permettre la communication entre les VLANs tout en maintenant leur isolation.

Ces configurations ont été sauvegardées et structurées pour une publication sur GitHub, permettant une collaboration et une documentation détaillée. Les scripts CLI pour le switch et le routeur, un fichier Packet Tracer pour la simulation, et un README documentant chaque étape ont été inclus. Le README décrit les objectifs, l'architecture réseau et les instructions détaillées pour reproduire ou modifier la configuration. Cette approche garantit une organisation claire, facilite le dépannage et encourage le partage de solutions réseau optimales avec d’autres administrateurs et collaborateurs. Le projet est maintenant disponible sur une plateforme collaborative, renforçant l’apprentissage et l’adoption des meilleures pratiques en gestion réseau.
 

Objectifs des Configurations VLAN

    Création de VLANs :
        Assigner différents VLANs à des bureaux ou départements spécifiques.
    Segmentation du réseau :
        Améliorer les performances et réduire les conflits réseau en isolant les segments.
    Routage inter-VLAN :
        Permettre la communication sécurisée entre VLANs via un routeur ou un switch de niveau 3.
    Documentation collaborative :
        Partager les configurations et étapes sur GitHub pour faciliter leur réutilisation, modification ou discussion.

Étapes de Préparation : Configuration et Mise en Ligne
1. Préparer les Configurations des Équipements

    Créez des scripts ou des commandes que vous avez exécutées sur vos équipements Cisco Packet Tracer.

Exemple de Configuration des VLANs (Sur le Switch)

# Création des VLANs
Switch(config)# vlan 10
Switch(config-vlan)# name Bureau1
Switch(config-vlan)# exit

Switch(config)# vlan 20
Switch(config-vlan)# name Bureau2
Switch(config-vlan)# exit

# Configuration des ports assignés aux VLANs
Switch(config)# interface FastEthernet0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
Switch(config-if)# exit

Switch(config)# interface FastEthernet0/2
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 20
Switch(config-if)# exit

# Configuration du Trunk pour la communication avec le routeur
Switch(config)# interface GigabitEthernet0/1
Switch(config-if)# switchport mode trunk
Switch(config-if)# exit

Configuration Routage Inter-VLAN (Sur le Routeur)

# Configuration des sous-interfaces
Router(config)# interface GigabitEthernet0/0.10
Router(config-subif)# encapsulation dot1Q 10
Router(config-subif)# ip address 192.168.10.1 255.255.255.0
Router(config-subif)# exit

Router(config)# interface GigabitEthernet0/0.20
Router(config-subif)# encapsulation dot1Q 20
Router(config-subif)# ip address 192.168.20.1 255.255.255.0
Router(config-subif)# exit

