<div align="center">

<img src="docs/banniere.png" alt="Banc LED, version d'essai du Switch Track" width="100%">

</div>


Module ESP32 simple pour contrôler 2 LEDs via WiFi et WebSocket - Parfait pour les tests et l'expérimentation

---

## 🚀 À propos

Ce projet est un module ESP32 minimaliste conçu pour contrôler 2 LEDs et tester les communications WiFi/WebSocket. Il simule un système de changement d'état (position gauche/droite) avec des indicateurs visuels.

### Stack technique

- **Hardware**: ESP32 DevKit
- **Framework**: Arduino (PlatformIO)
- **Communication**: WebSocket + WiFi
- **Filesystem**: LittleFS
- **Langage**: C++ (Arduino)

---

## 📦 Installation

### Prérequis

- [Visual Studio Code](https://code.visualstudio.com/)
- [PlatformIO Extension](https://platformio.org/install/ide?install=vscode)
- ESP32 DevKit board

### Installation du projet

1. Clonez ce repository :
```bash
git clone https://github.com/Microcoaster/ESP-32-led.git
cd ESP-32-led
```

2. Ouvrez le projet dans VS Code

3. Installez les dépendances PlatformIO :
```bash
pio install
```

---

## ⚙️ Configuration

### Branchements matériels

Connectez sur votre ESP32 :

- **LED Gauche** : D2 ──► Résistance 220Ω ──► (+) LED ──► GND
- **LED Droite** : D4 ──► Résistance 220Ω ──► (+) LED ──► GND

### Configuration WiFi

Au premier démarrage, l'ESP32 crée un point d'accès WiFi :
- **SSID**: `WifiManager-MicroCoaster`
- **Mot de passe**: `123456789`
- **IP**: `192.168.4.1`

Connectez-vous et configurez votre WiFi domestique.

---

## 🚀 Usage

### Téléversement

1. **Effacer la flash** :
   ```bash
   pio run --target erase --environment esp32dev
   ```

2. **Téléverser le programme** :
   ```bash
   pio run --target upload --environment esp32dev
   ```

3. **Téléverser le filesystem** :
   ```bash
   pio run --target uploadfs --environment esp32dev
   ```

### Test du module

1. Ouvrez le moniteur série :
   ```bash
   pio device monitor
   ```

2. Vérifiez que :
   - La LED sur D2 s'allume (position initiale "gauche")
   - L'ESP32 se connecte au WiFi configuré
   - Le message "✅ Initialisation terminée" apparaît

### Commandes WebSocket

Envoyez des commandes JSON au module via WebSocket :

```json
{
  "type": "command",
  "data": {
    "command": "switch_left"
  }
}
```

Commandes disponibles :
- `switch_left` / `left` : Allume LED gauche
- `switch_right` / `right` : Allume LED droite
- `get_position` : Retourne la position actuelle

---

## 🔧 Développement

### Structure du projet

```
ESP-32-led/
├── src/
│   └── main.cpp          # Code principal
├── data/
│   ├── index.html        # Interface WiFi
│   └── ...               # Fichiers web
├── include/
├── lib/
├── platformio.ini        # Configuration PlatformIO
└── partitions_custom.csv # Schéma de partition
```

### Logs et debug

Le module affiche des informations détaillées sur le port série :
- Connexion WiFi
- État des LEDs
- Messages WebSocket reçus
- Télémétrie

---

## 📄 Licence

Ce projet est sous licence propriétaire MicroCoaster.
Voir le fichier `LICENCE` pour plus de détails.

---

## ⚠️ Statut du projet

✅ **Version stable 1.0.0**
- Module fonctionnel pour tests
- Code optimisé et simplifié
- Documentation complète

---

## 🔗 Liens utiles

- [Documentation ESP32](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/)
- [PlatformIO](https://docs.platformio.org/)
- [WebSocket Protocol](https://tools.ietf.org/html/rfc6455)
