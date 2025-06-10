# 🎵 GUIDE AUDIO BRUTALISTE 🎵

## Système Audio Actuel

La page intègre actuellement un **générateur de synthwave** créé avec la Web Audio API qui produit :
- 🎹 **Mélodie synthwave** (oscillateur sawtooth)
- 🎸 **Ligne de basse** (oscillateur square)
- 🔊 **Effets sonores** interactifs (hover, click)
- 🎛️ **Contrôles brutaux** (play, pause, mute, volume)

## 🎶 Ajouter de la Vraie Musique

### Option 1 : Musique Libre de Droits (Recommandée)

#### Sources Gratuites :
1. **Blue Fox Music** - "Neon City" (Synthwave gratuit)
   - URL: https://bluefoxmusic.com/royalty-free-music/neon-city/
   - Format: MP3 320kbps
   - Attribution requise

2. **OpenGameArt** - "Synth Wave by Alex"
   - URL: https://opengameart.org/content/synth-wave-by-alex
   - Licence: CC0 (domaine public)
   - Pas d'attribution requise

3. **Freesound.org** - Recherche "synthwave loop"
   - Licence: Creative Commons
   - Variété de pistes courtes

### Option 2 : Intégration Rapide

```html
<!-- Remplacer le système actuel par : -->
<audio id="bgMusic" loop>
    <source src="synthwave-track.mp3" type="audio/mpeg">
    <source src="synthwave-track.ogg" type="audio/ogg">
</audio>
```

```javascript
// Remplacer la fonction createSynthwave() par :
function playRealMusic() {
    const audio = document.getElementById('bgMusic');
    audio.volume = 0.3;
    audio.play();
}
```

### Option 3 : YouTube Embed (Caché)

```html
<!-- Lecteur YouTube invisible -->
<iframe id="ytPlayer" width="0" height="0" 
        src="https://www.youtube.com/embed/VIDEO_ID?autoplay=1&loop=1&playlist=VIDEO_ID&controls=0"
        style="display: none;">
</iframe>
```

## 🎵 Recommandations Musicales

### Style Synthwave/Retrowave :
- **Tempo** : 120-140 BPM
- **Tonalité** : Mineure (Am, Dm, Em)
- **Instruments** : Synthés analogiques, boîte à rythmes
- **Ambiance** : Nostalgique, cyberpunk, années 80

### Pistes Recommandées :
1. **"Neon Nights"** - Style Miami Vice
2. **"Cyber Dreams"** - Ambiance Blade Runner
3. **"Retro Drive"** - Énergie arcade
4. **"Digital Sunset"** - Mélancolie synthétique

## 🔧 Instructions d'Intégration

### Étape 1 : Télécharger la Musique
```bash
# Créer un dossier audio
mkdir audio
cd audio

# Télécharger votre piste (exemple)
wget "URL_DE_LA_PISTE" -O synthwave-bg.mp3
```

### Étape 2 : Modifier le HTML
```html
<!-- Ajouter après <body> -->
<audio id="bgMusic" preload="auto" loop>
    <source src="audio/synthwave-bg.mp3" type="audio/mpeg">
    <source src="audio/synthwave-bg.ogg" type="audio/ogg">
</audio>
```

### Étape 3 : Modifier le JavaScript
```javascript
// Remplacer la fonction createSynthwave() par :
function createSynthwave() {
    const audio = document.getElementById('bgMusic');
    audio.volume = gainNode.gain.value;
    audio.play().catch(e => console.log('Autoplay bloqué:', e));
}

// Ajouter le contrôle de volume :
document.getElementById('volumeSlider').addEventListener('input', (e) => {
    const audio = document.getElementById('bgMusic');
    if (audio && !isMuted) {
        audio.volume = e.target.value / 100;
    }
});
```

## 🎨 Personnalisation Avancée

### Visualiseur Audio (Optionnel)
```javascript
// Ajouter un analyseur de fréquences
const analyser = audioContext.createAnalyser();
audio.connect(analyser);

// Synchroniser les animations avec la musique
function syncVisuals() {
    const dataArray = new Uint8Array(analyser.frequencyBinCount);
    analyser.getByteFrequencyData(dataArray);
    
    // Modifier les couleurs selon les basses
    const bassLevel = dataArray[0];
    document.body.style.filter = `hue-rotate(${bassLevel}deg)`;
}
```

### Effets Audio Contextuels
```javascript
// Sons différents selon les actions
const sounds = {
    yannick: 'audio/yannick-sound.mp3',
    michel: 'audio/michel-sound.mp3',
    donation: 'audio/cash-sound.mp3'
};
```

## 📝 Licences et Attribution

### Si vous utilisez de la musique libre :
```html
<!-- Ajouter dans le footer -->
<p style="font-size: 8px; opacity: 0.7;">
    Musique: "Nom de la piste" par Artiste - 
    <a href="URL_SOURCE">Source</a>
</p>
```

### Formats Recommandés :
- **MP3** : Compatibilité universelle
- **OGG** : Meilleure qualité, moins de support
- **WAV** : Qualité maximale, fichiers lourds

## 🚀 Déploiement

1. **Tester localement** avec un serveur HTTP
2. **Vérifier l'autoplay** sur mobile
3. **Optimiser la taille** des fichiers audio
4. **Prévoir un fallback** si l'audio échoue

---

**Note** : Le système actuel fonctionne parfaitement et crée une ambiance synthwave authentique. L'ajout de vraie musique est optionnel mais recommandé pour une expérience plus immersive !

🎮 **BRUTAL AUDIO SYSTEM ACTIVATED** 🎮 