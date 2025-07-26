<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Amplificador de Voz - Modo Clase</title>
    
    <!-- PWA Meta Tags -->
    <meta name="theme-color" content="#667eea">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="apple-mobile-web-app-title" content="Amplificador Voz">
    <meta name="mobile-web-app-capable" content="yes">
    
    <!-- Favicon inline -->
    <link rel="icon" type="image/svg+xml" href="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA1MTIgNTEyIj48cmVjdCB4PSIwIiB5PSIwIiB3aWR0aD0iNTEyIiBoZWlnaHQ9IjUxMiIgZmlsbD0iIzY2N2VlYSIvPjx0ZXh0IHg9IjI1NiIgeT0iMzAwIiBmb250LXNpemU9IjIwMCIgdGV4dC1hbmNob3I9Im1pZGRsZSIgZmlsbD0id2hpdGUiPvCfj6Q8L3RleHQ+PC9zdmc+">
    
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 20px;
            color: white;
            user-select: none;
        }

        .container {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            text-align: center;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
            max-width: 450px;
            width: 100%;
        }

        h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            font-weight: 300;
        }

        .subtitle {
            font-size: 1.2em;
            opacity: 0.9;
            margin-bottom: 30px;
            color: #FFE082;
        }

        .offline-ready {
            background: rgba(76, 175, 80, 0.2);
            border: 2px solid rgba(76, 175, 80, 0.5);
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 20px;
            font-size: 0.95em;
            animation: offlineGlow 3s ease-in-out infinite;
        }

        @keyframes offlineGlow {
            0%, 100% { box-shadow: 0 0 10px rgba(76, 175, 80, 0.3); }
            50% { box-shadow: 0 0 20px rgba(76, 175, 80, 0.5); }
        }

        .status {
            font-size: 1.3em;
            margin-bottom: 30px;
            padding: 20px;
            border-radius: 15px;
            background: rgba(255, 255, 255, 0.1);
            border: 2px solid rgba(255, 255, 255, 0.2);
            font-weight: 500;
        }

        .status.active {
            background: rgba(76, 175, 80, 0.3);
            border-color: rgba(76, 175, 80, 0.7);
            animation: activeGlow 2s ease-in-out infinite;
        }

        .status.error {
            background: rgba(244, 67, 54, 0.3);
            border-color: rgba(244, 67, 54, 0.7);
        }

        @keyframes activeGlow {
            0%, 100% { box-shadow: 0 0 20px rgba(76, 175, 80, 0.3); }
            50% { box-shadow: 0 0 30px rgba(76, 175, 80, 0.6); }
        }

        .controls {
            display: flex;
            flex-direction: column;
            gap: 20px;
            margin-bottom: 30px;
        }

        .btn {
            padding: 18px 35px;
            font-size: 1.3em;
            font-weight: 600;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            background: rgba(255, 255, 255, 0.2);
            color: white;
            border: 3px solid rgba(255, 255, 255, 0.3);
            text-transform: uppercase;
            letter-spacing: 1px;
            touch-action: manipulation;
        }

        .btn:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
        }

        .btn:active {
            transform: translateY(-1px);
        }

        .btn.primary {
            background: linear-gradient(45deg, #4CAF50, #45a049);
            border-color: #4CAF50;
            box-shadow: 0 4px 15px rgba(76, 175, 80, 0.4);
        }

        .btn.primary:hover {
            background: linear-gradient(45deg, #45a049, #3d8b40);
            box-shadow: 0 8px 25px rgba(76, 175, 80, 0.6);
        }

        .btn.danger {
            background: linear-gradient(45deg, #f44336, #d32f2f);
            border-color: #f44336;
            box-shadow: 0 4px 15px rgba(244, 67, 54, 0.4);
            animation: pulseRed 1.5s ease-in-out infinite;
        }

        .btn.danger:hover {
            background: linear-gradient(45deg, #d32f2f, #b71c1c);
        }

        @keyframes pulseRed {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        .volume-control {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 25px;
            margin: 20px 0;
        }

        .volume-control label {
            display: block;
            margin-bottom: 15px;
            font-size: 1.2em;
            font-weight: 600;
        }

        .volume-slider {
            width: 100%;
            height: 10px;
            border-radius: 5px;
            background: rgba(255, 255, 255, 0.3);
            outline: none;
            -webkit-appearance: none;
            margin: 10px 0;
        }

        .volume-slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 25px;
            height: 25px;
            border-radius: 50%;
            background: linear-gradient(45deg, #FFE082, #FFC107);
            cursor: pointer;
            box-shadow: 0 3px 8px rgba(0, 0, 0, 0.4);
        }

        .volume-slider::-moz-range-thumb {
            width: 25px;
            height: 25px;
            border-radius: 50%;
            background: linear-gradient(45deg, #FFE082, #FFC107);
            cursor: pointer;
            border: none;
            box-shadow: 0 3px 8px rgba(0, 0, 0, 0.4);
        }

        .volume-display {
            margin-top: 15px;
            font-size: 1.4em;
            font-weight: bold;
            color: #FFE082;
        }

        .info {
            font-size: 1em;
            opacity: 0.9;
            line-height: 1.6;
            background: rgba(255, 255, 255, 0.1);
            padding: 20px;
            border-radius: 15px;
            margin-top: 20px;
            text-align: left;
        }

        .info strong {
            color: #FFE082;
            font-size: 1.1em;
        }

        .microphone-icon {
            font-size: 5em;
            margin-bottom: 20px;
            opacity: 0.8;
            filter: drop-shadow(0 4px 8px rgba(0, 0, 0, 0.3));
        }

        .pulse {
            animation: pulse 1.5s infinite;
        }

        @keyframes pulse {
            0% { transform: scale(1); opacity: 0.8; }
            50% { transform: scale(1.15); opacity: 1; }
            100% { transform: scale(1); opacity: 0.8; }
        }

        .setup-section {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 25px;
            border: 2px solid rgba(255, 255, 255, 0.2);
        }

        .setup-title {
            font-size: 1.3em;
            font-weight: bold;
            margin-bottom: 15px;
            color: #FFE082;
        }

        .setup-steps {
            text-align: left;
            line-height: 1.5;
        }

        .setup-steps li {
            margin-bottom: 8px;
            list-style: none;
            position: relative;
            padding-left: 25px;
        }

        .setup-steps li:before {
            content: "✓";
            position: absolute;
            left: 0;
            color: #4CAF50;
            font-weight: bold;
        }

        .audio-level {
            width: 100%;
            height: 20px;
            background: rgba(255, 255, 255, 0.2);
            border-radius: 10px;
            overflow: hidden;
            margin: 15px 0;
        }

        .audio-level-bar {
            height: 100%;
            background: linear-gradient(90deg, #4CAF50, #8BC34A, #CDDC39, #FFC107, #FF5722);
            width: 0%;
            transition: width 0.1s ease;
            border-radius: 10px;
        }

        .install-section {
            background: rgba(33, 150, 243, 0.2);
            border: 2px solid rgba(33, 150, 243, 0.5);
            border-radius: 15px;
            padding: 15px;
            margin-bottom: 20px;
            font-size: 0.9em;
        }

        @media (max-width: 480px) {
            .container {
                padding: 20px;
                margin: 10px;
            }
            
            h1 {
                font-size: 2em;
            }
            
            .btn {
                font-size: 1.1em;
                padding: 15px 25px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="offline-ready">
            📡 <strong>MODO OFFLINE ACTIVADO</strong><br>
            ¡Funciona sin internet una vez cargado!
        </div>

        <div class="install-section">
            📱 <strong>Para usar siempre:</strong><br>
            • En Chrome: Menú → "Instalar aplicación"<br>
            • En Safari: Compartir → "Añadir a pantalla de inicio"<br>
            • Funciona 100% offline después de instalar
        </div>

        <div class="microphone-icon" id="micIcon">🎤</div>
        <h1>Amplificador de Voz</h1>
        <p class="subtitle">📚 Perfecto para dar clases sin afónica</p>
        
        <div class="setup-section">
            <div class="setup-title">🔧 Configuración Rápida</div>
            <ol class="setup-steps">
                <li>Conecta parlante externo (Bluetooth o cable)</li>
                <li>Mantén el teléfono cerca de tu boca</li>
                <li>Ajusta el volumen según tu aula</li>
                <li>¡Presiona INICIAR y a enseñar!</li>
            </ol>
        </div>
        
        <div class="status" id="status">
            🎯 Todo listo. Presiona INICIAR para amplificar tu voz
        </div>

        <div class="audio-level" id="audioLevelContainer" style="display: none;">
            <div class="audio-level-bar" id="audioLevelBar"></div>
        </div>

        <div class="controls">
            <button class="btn primary" id="startBtn" onclick="startAmplifier()">
                🚀 INICIAR AMPLIFICADOR
            </button>
            <button class="btn danger" id="stopBtn" onclick="stopAmplifier()" style="display: none;">
                ⏹️ DETENER
            </button>
        </div>

        <div class="volume-control">
            <label for="volumeSlider">🔊 Control de Volumen</label>
            <input type="range" id="volumeSlider" class="volume-slider" min="0" max="100" value="75">
            <div class="volume-display" id="volumeValue">75%</div>
        </div>

        <div class="info">
            <strong>💡 Consejos para mejores resultados:</strong><br><br>
            • <strong>Distancia ideal:</strong> 20-30 cm del teléfono<br>
            • <strong>Sin auriculares:</strong> Para evitar retroalimentación<br>
            • <strong>Parlante externo:</strong> Mejor calidad y volumen<br>
            • <strong>Prueba primero:</strong> Ajusta volumen antes de clase<br>
            • <strong>Modo avión + WiFi:</strong> Evita interrupciones por llamadas<br>
            • <strong>100% offline:</strong> No necesita internet después de cargar
        </div>
    </div>

    <script>
        // Variables de audio
        let audioContext;
        let microphone;
        let gainNode;
        let analyserNode;
        let isAmplifying = false;
        let animationId;
        let mediaStream;

        const statusEl = document.getElementById('status');
        const startBtn = document.getElementById('startBtn');
        const stopBtn = document.getElementById('stopBtn');
        const volumeSlider = document.getElementById('volumeSlider');
        const volumeValue = document.getElementById('volumeValue');
        const micIcon = document.getElementById('micIcon');
        const audioLevelContainer = document.getElementById('audioLevelContainer');
        const audioLevelBar = document.getElementById('audioLevelBar');

        // Configuración de audio
        const audioConfig = {
            audio: {
                echoCancellation: false,           
                noiseSuppression: false,          
                autoGainControl: false,           
                sampleRate: 44100,                
                channelCount: 1,                  
                latency: 0.01
            }
        };

        // Control de volumen
        volumeSlider.addEventListener('input', function() {
            const volume = parseInt(this.value);
            volumeValue.textContent = volume + '%';
            
            // Guardar configuración
            try {
                localStorage.setItem('amplifierVolume', volume);
            } catch (e) {}
            
            if (gainNode && audioContext) {
                const gain = Math.pow(volume / 100, 1.5);
                gainNode.gain.setTargetAtTime(gain, audioContext.currentTime, 0.01);
            }
        });

        // Visualizador de audio
        function updateAudioLevel() {
            if (!analyserNode || !isAmplifying) return;

            const bufferLength = analyserNode.frequencyBinCount;
            const dataArray = new Uint8Array(bufferLength);
            analyserNode.getByteFrequencyData(dataArray);

            let sum = 0;
            for (let i = 0; i < bufferLength; i++) {
                sum += dataArray[i] * dataArray[i];
            }
            const rms = Math.sqrt(sum / bufferLength);
            const percentage = Math.min((rms / 128) * 100, 100);

            audioLevelBar.style.width = percentage + '%';
            
            if (percentage > 80) {
                audioLevelBar.style.background = 'linear-gradient(90deg, #FF5722, #F44336)';
            } else if (percentage > 50) {
                audioLevelBar.style.background = 'linear-gradient(90deg, #FFC107, #FF9800)';
            } else {
                audioLevelBar.style.background = 'linear-gradient(90deg, #4CAF50, #8BC34A)';
            }

            animationId = requestAnimationFrame(updateAudioLevel);
        }

        // Función principal de inicio
        async function startAmplifier() {
            try {
                statusEl.textContent = '🔄 Iniciando amplificador...';
                statusEl.className = 'status';
                startBtn.disabled = true;

                if (!navigator.mediaDevices || !navigator.mediaDevices.getUserMedia) {
                    throw new Error('Tu navegador no soporta grabación de audio');
                }

                statusEl.textContent = '🎤 Solicitando acceso al micrófono...';
                mediaStream = await navigator.mediaDevices.getUserMedia(audioConfig);

                const AudioContext = window.AudioContext || window.webkitAudioContext;
                audioContext = new AudioContext({
                    latencyHint: 'interactive',
                    sampleRate: 44100
                });

                if (audioContext.state === 'suspended') {
                    await audioContext.resume();
                }

                microphone = audioContext.createMediaStreamSource(mediaStream);
                gainNode = audioContext.createGain();
                analyserNode = audioContext.createAnalyser();

                analyserNode.fftSize = 512;
                analyserNode.smoothingTimeConstant = 0.7;

                const currentVolume = parseInt(volumeSlider.value);
                const gain = Math.pow(currentVolume / 100, 1.5);
                gainNode.gain.setValueAtTime(gain, audioContext.currentTime);

                microphone.connect(gainNode);
                gainNode.connect(analyserNode);
                gainNode.connect(audioContext.destination);

                isAmplifying = true;
                statusEl.textContent = '🔴 ¡AMPLIFICANDO EN VIVO! Habla normalmente';
                statusEl.className = 'status active';
                startBtn.style.display = 'none';
                stopBtn.style.display = 'block';
                micIcon.className = 'pulse';
                micIcon.textContent = '🔴';
                audioLevelContainer.style.display = 'block';

                updateAudioLevel();
                console.log('✅ Amplificador iniciado correctamente');

            } catch (error) {
                console.error('❌ Error al iniciar amplificador:', error);
                handleStartError(error);
            }
        }

        function handleStartError(error) {
            let errorMessage = '❌ Error: ';
            
            if (error.name === 'NotAllowedError') {
                errorMessage += 'Necesitas permitir acceso al micrófono. Recarga y permite el acceso.';
            } else if (error.name === 'NotFoundError') {
                errorMessage += 'No se encontró micrófono. Verifica que tu dispositivo tenga micrófono.';
            } else if (error.name === 'NotSupportedError') {
                errorMessage += 'Tu navegador no soporta esta función. Usa Chrome o Firefox.';
            } else if (error.name === 'NotReadableError') {
                errorMessage += 'El micrófono está siendo usado por otra aplicación.';
            } else {
                errorMessage += error.message || 'No se pudo acceder al micrófono.';
            }
            
            statusEl.textContent = errorMessage;
            statusEl.className = 'status error';
            startBtn.disabled = false;
        }

        function stopAmplifier() {
            try {
                if (animationId) {
                    cancelAnimationFrame(animationId);
                    animationId = null;
                }

                if (mediaStream) {
                    mediaStream.getTracks().forEach(track => {
                        track.stop();
                    });
                    mediaStream = null;
                }

                if (audioContext && audioContext.state !== 'closed') {
                    audioContext.close();
                    audioContext = null;
                }

                microphone = null;
                gainNode = null;
                analyserNode = null;
                isAmplifying = false;

                statusEl.textContent = '✅ Amplificador detenido. Listo para reiniciar';
                statusEl.className = 'status';
                startBtn.style.display = 'block';
                startBtn.disabled = false;
                stopBtn.style.display = 'none';
                micIcon.className = '';
                micIcon.textContent = '🎤';
                audioLevelContainer.style.display = 'none';
                audioLevelBar.style.width = '0%';

                console.log('✅ Amplificador detenido correctamente');

            } catch (error) {
                console.error('Error al detener:', error);
            }
        }

        // Inicialización
        document.addEventListener('DOMContentLoaded', function() {
            try {
                const savedVolume = localStorage.getItem('amplifierVolume');
                if (savedVolume) {
                    volumeSlider.value = savedVolume;
                    volumeValue.textContent = savedVolume + '%';
                }
            } catch (e) {}
            
            console.log('📱 Amplificador de Voz cargado y listo');
        });

        window.addEventListener('beforeunload', e => {
            if (isAmplifying) {
                e.preventDefault();
                e.returnValue = '¿Seguro que quieres cerrar? El amplificador está activo.';
            }
        });
    </script>
</body>
</html>
