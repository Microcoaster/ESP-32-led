# Journal des modifications

Tous les changements notables de ce projet seront documentés dans ce fichier.

## [1.0.0] - 05-10-2025

- Version initiale du module ESP32 de contrôle LED

### Ajouté

- Module ESP32 simple pour contrôler 2 LEDs
- Gestionnaire WiFi automatique avec portail captif
- Communication WebSocket pour recevoir des commandes
- Indicateurs LED pour l'état de position (gauche/droite)
- Code optimisé et simplifié pour les tests

### Fonctionnalités

- Connexion WiFi automatique ou configuration via portail web
- Réception de commandes WebSocket pour simuler des changements de position
- Allumage des LEDs selon la position (D2 pour gauche, D4 pour droite)
- Monitoring et télémétrie de l'état du module

[1.0.0]: https://github.com/Microcoaster/ESP-32-led/releases/tag/v1.0.0