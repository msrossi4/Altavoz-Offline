<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Amplificador de Voz - Para Clases</title>
    
    <meta name="theme-color" content="#667eea">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="apple-mobile-web-app-title" content="Amplificador Voz">
    <meta name="mobile-web-app-capable" content="yes">
    
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

        .https-warning, .offline-ready, .install-section, .output-device-tip, .setup-section, .device-selection { 
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 20px;
            font-size: 0.9em;
            text-align: left;
        }

        .https-warning {
            background: rgba(255, 152, 0, 0.2);
            border: 2px solid rgba(255, 152, 0, 0.5);
            display: none;
        }

        .offline-ready {
            background: rgba(76, 175, 80, 0.2);
            border: 2px solid rgba(76, 175, 80, 0.5);
            animation: offlineGlow 3s ease-in-out infinite;
        }

        @keyframes offlineGlow {
            0%, 100% { box-shadow: 0 0 10px rgba(76, 175, 80, 0.3); }
            50% { box-shadow: 0 0 20px rgba(76, 175, 80, 0.5); }
        }

        .install-section {
            background: rgba(33, 150, 243, 0.2);
            border: 2px solid rgba(33, 150, 243, 0.5);
        }
        
        .output-device-tip {
            background: rgba(255, 193, 7, 0.2);
            border: 2px solid rgba(255, 193, 7, 0.5);
            font-size: 1em;
            display: none;
        }

        .device-selection {
            background: rgba(156, 39, 176, 0.2);
            border: 2px solid rgba(156, 39, 176, 0.5);
            text-align: center;
        }

        .device-select {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border-radius: 8px;
            border: 1px solid rgba(255, 255, 255, 0.3);
            background: rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 1em;
        }

        .device-select option {
            background: #333;
            color: white;
        }

        .status {
            font-size: 1.3em;
            margin-bottom: 30px;
            padding: 20px;
            border-radius: 15px;
            background: rgba(255, 255, 255, 0.1);
            border: 2px solid rgba(255, 255, 255, 0.2);
            font-weight: 500;
            transition: background 0.3s ease, border-color 0.3s ease;
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

        .btn.secondary {
            background: linear-gradient(45deg, #9C27B0, #7B1FA2);
            border-color: #9C27B0;
            box-shadow: 0 4px 15px rgba(156, 39, 176, 0.4);
            font-size: 1.1em;
            padding: 12px 25px;
        }

        .volume-control, .delay-control {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 25px;
            margin: 20px 0;
        }

        .volume-control label, .delay-control label {
            display: block;
            margin-bottom: 15px;
            font-size: 1.2em;
            font-weight: 600;
        }

        .volume-slider, .delay-slider {
            width: 100%;
            height: 10px;
            border-radius: 5px;
            background: rgba(255, 255, 255, 0.3);
            outline: none;
            -webkit-appearance: none;
            margin: 10px 0;
            cursor: grab;
        }

        .volume-slider::-webkit-slider-thumb, .delay-slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 25px;
            height: 25px;
            border-radius: 50%;
            background: linear-gradient(45deg, #FFE082, #FFC107);
            cursor: grab;
            box-shadow: 0 3px 8px rgba(0, 0, 0, 0.4);
        }

        .delay-slider::-webkit-slider-thumb {
            background: linear-gradient(45deg, #9C27B0, #E91E63);
        }

        .volume-display {
            margin-top: 15px;
            font-size: 1.4em;
            font-weight: bold;
            color: #FFE082;
        }

        .delay-display {
            margin-top: 10px;
            font-size: 1.1em;
            font-weight: bold;
            color: #E1BEE7;
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
            transition: transform 0.3s ease, opacity 0.3s ease;
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
            text-align: left;
        }

        .setup-title {
            font-size: 1.3em;
            font-weight: bold;
            margin-bottom: 15px;
            color: #FFE082;
            text-align: center;
        }

        .setup-steps {
            list-style: none;
        }

        .setup-steps li {
            margin-bottom: 8px;
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
            border: 1px solid rgba(255, 255, 255, 0.3);
        }

        .audio-level-bar {
            height: 100%;
            background: linear-gradient(90deg, #4CAF50, #8BC34A, #CDDC39, #FFC107, #FF5722);
            width: 0%;
            transition: width 0.1s ease, background 0.3s ease;
            border-radius: 10px;
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
        <div class="https-warning" id="httpsWarning">
            ⚠️ <strong>ATENCIÓN:</strong> Necesitas **HTTPS** para usar el micrófono.<br>
            Sube el archivo a un servidor HTTPS o usa localhost con certificado.
        </div>

        <div class="offline-ready" id="offlineReady">
            📡 <strong>MODO OFFLINE ACTIVADO</strong><br>
            ¡Funciona sin internet una vez cargado!
        </div>

        <div class="install-section" id="installSection">
            📱 <strong>Para usar siempre:</strong><br>
            • En Chrome: Menú → "Instalar aplicación"<br>
            • En Safari: Compartir → "Añadir a pantalla de inicio"<br>
            • Funciona 100% offline después de instalar.
        </div>

        <div class="device-selection">
            <strong>🎧 Dispositivos de Audio</strong><br>
            <button class="btn secondary" id="refreshDevicesBtn" onclick="refreshDevices()">
                🔄 Actualizar Dispositivos
            </button>
            <select id="microphoneSelect" class="device-select">
                <option value="">Seleccionar micrófono...</option>
            </select>
        </div>
        
        <div class="output-device-tip" id="outputDeviceTip">
            🔊 <strong>CONFIGURACIÓN DE SALIDA</strong><br><br>
            <strong>PASO IMPORTANTE:</strong> Ve a la configuración de sonido de tu dispositivo y selecciona tu <strong>parlante Bluetooth</strong> como dispositivo de salida predeterminado.<br><br>
            <strong>En Android:</strong> Configuración → Sonido → Dispositivo de salida<br>
            <strong>En iOS:</strong> Centro de Control → Presiona el ícono de AirPlay<br>
            <strong>En PC:</strong> Configuración → Sistema → Sonido → Elegir dispositivo de salida
        </div>

        <div class="microphone-icon" id="micIcon">🎤</div>
        <h1>Amplificador de Voz</h1>
        <p class="subtitle">📚 Ideal para dar clases sin forzar la voz</p>
        
        <div class="setup-section">
            <div class="setup-title">🔧 Configuración Recomendada</div>
            <ol class="setup-steps">
                <li><strong>CONECTA tu parlante Bluetooth</strong> y configúralo como salida principal en tu dispositivo</li>
                <li><strong>USA auriculares con micrófono</strong> o micrófono externo para entrada</li>
                <li>Selecciona el micrófono correcto en el menú de arriba</li>
                <li>Mantén el micrófono cerca de tu boca (20-30cm)</li>
                <li>¡Presiona <strong>INICIAR</strong> y ajusta el volumen gradualmente!</li>
            </ol>
        </div>
        
        <div class="status" id="status">
            🎯 Todo listo. Presiona <strong>INICIAR</strong> para amplificar tu voz.
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
            <label for="volumeSlider">🔊 Control de Volumen (Hasta 300%)</label>
            <input type="range" id="volumeSlider" class="volume-slider" min="0" max="300" value="150">
            <div class="volume-display" id="volumeValue">150%</div>
        </div>

        <div class="delay-control">
            <label for="delaySlider">⏱️ Retardo Anti-Feedback (ms)</label>
            <input type="range" id="delaySlider" class="delay-slider" min="0" max="100" value="20">
            <div class="delay-display" id="delayValue">20ms</div>
        </div>

        <div class="info">
            <strong>💡 Consejos IMPORTANTES:</strong><br><br>
            • <strong>VOLUMEN HASTA 300%:</strong> Máxima potencia, úsalo con cuidado<br>
            • <strong>CONFIGURACIÓN IDEAL:</strong> Auriculares como entrada + parlante Bluetooth como salida<br>
            • <strong>SELECCIÓN DE MICRÓFONO:</strong> Usa el menú de arriba para elegir el dispositivo correcto<br>
            • <strong>SEPARACIÓN FÍSICA:</strong> Mantén el parlante lo más lejos posible del micrófono<br>
            • <strong>RETARDO AUMENTADO:</strong> Hasta 100ms para evitar feedback en configuraciones complejas<br>
            • <strong>PRUEBA SIEMPRE:</strong> Ajusta antes de usar en clase para evitar acoples<br>
            • <strong>100% OFFLINE:</strong> Funciona sin internet una vez cargado
        </div>
    </div>

    <script>
        // Variables globales
        let audioContext;
        let microphone;
        let gainNode;
        let analyserNode;
        let delayNode;
        let compressorNode;
        let isAmplifying = false;
        let animationId;
        let mediaStream;
        let selectedDeviceId = null;

        // Referencias DOM
        const statusEl = document.getElementById('status');
        const startBtn = document.getElementById('startBtn');
        const stopBtn = document.getElementById('stopBtn');
        const volumeSlider = document.getElementById('volumeSlider');
        const volumeValue = document.getElementById('volumeValue');
        const delaySlider = document.getElementById('delaySlider');
        const delayValue = document.getElementById('delayValue');
        const micIcon = document.getElementById('micIcon');
        const audioLevelContainer = document.getElementById('audioLevelContainer');
        const audioLevelBar = document.getElementById('audioLevelBar');
        const httpsWarning = document.getElementById('httpsWarning');
        const outputDeviceTip = document.getElementById('outputDeviceTip');
        const microphoneSelect = document.getElementById('microphoneSelect');

        // Verificar HTTPS
        if (location.protocol !== 'https:' && location.hostname !== 'localhost') {
            httpsWarning.style.display = 'block';
        }

        // Configuración de audio optimizada
        const getAudioConfig = () => ({
            audio: {
                deviceId: selectedDeviceId ? { exact: selectedDeviceId } : undefined,
                echoCancellation: false,
                noiseSuppression: false,
                autoGainControl: false,
                sampleRate: 48000, // Aumentado para mejor calidad
                channelCount: 1,
                latency: 0.01
            }
        });

        // Listar dispositivos de entrada
        async function refreshDevices() {
            try {
                // Solicitar permisos primero
                await navigator.mediaDevices.getUserMedia({ audio: true });
                
                const devices = await navigator.mediaDevices.enumerateDevices();
                const audioInputs = devices.filter(device => device.kind === 'audioinput');
                
                microphoneSelect.innerHTML = '<option value="">Micrófono predeterminado</option>';
                
                audioInputs.forEach(device => {
                    const option = document.createElement('option');
                    option.value = device.deviceId;
                    option.textContent = device.label || `Micrófono ${audioInputs.indexOf(device) + 1}`;
                    microphoneSelect.appendChild(option);
                });

                statusEl.textContent = `✅ ${audioInputs.length} dispositivos de entrada encontrados`;
                statusEl.className = 'status active';
                
                setTimeout(() => {
                    if (!isAmplifying) {
                        statusEl.textContent = '🎯 Todo listo. Presiona INICIAR para amplificar tu voz.';
                        statusEl.className = 'status';
                    }
                }, 2000);

            } catch (error) {
                console.error('Error al listar dispositivos:', error);
                statusEl.textContent = '❌ Error al acceder a dispositivos de audio';
                statusEl.className = 'status error';
            }
        }

        // Manejar selección de dispositivo
        microphoneSelect.addEventListener('change', function() {
            selectedDeviceId = this.value || null;
            try {
                localStorage.setItem('selectedMicrophone', selectedDeviceId || '');
            } catch(e) {}
        });

        // Control de volumen mejorado
        volumeSlider.addEventListener('input', function() {
            const volume = parseInt(this.value);
            volumeValue.textContent = volume + '%';
            
            try {
                localStorage.setItem('amplifierVolume', volume);
            } catch (e) {}
            
            if (gainNode && audioContext) {
                // Ganancia más agresiva para volúmenes altos
                const gain = Math.pow(volume / 100, 1.1) * 1.5;
                gainNode.gain.setTargetAtTime(gain, audioContext.currentTime, 0.02);
            }
        });

        // Control de retardo
        delaySlider.addEventListener('input', function() {
            const delay = parseInt(this.value);
            delayValue.textContent = delay + 'ms';
            
            try {
                localStorage.setItem('amplifierDelay', delay);
            } catch (e) {}
            
            if (delayNode && audioContext) {
                delayNode.delayTime.setTargetAtTime(delay / 1000, audioContext.currentTime, 0.01);
            }
        });

        // Visualizador de audio mejorado
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
            const percentage = Math.min((rms / 100) * 100, 100);

            audioLevelBar.style.width = percentage + '%';
            
            if (percentage > 95) {
                audioLevelBar.style.background = 'linear-gradient(90deg, #FF1744, #D50000)';
                statusEl.textContent = '🚨 NIVEL CRÍTICO - Reduce volumen inmediatamente';
                statusEl.className = 'status error';
            } else if (percentage > 85) {
                audioLevelBar.style.background = 'linear-gradient(90deg, #FF5722, #BF360C)';
                statusEl.textContent = '⚠️ NIVEL ALTO - Cuidado con el feedback';
                statusEl.className = 'status error';
            } else if (percentage > 60) {
                audioLevelBar.style.background = 'linear-gradient(90deg, #FF9800, #F57C00)';
                if (statusEl.className === 'status error') {
                    statusEl.textContent = '🔴 ¡AMPLIFICANDO EN VIVO! Habla normalmente';
                    statusEl.className = 'status active';
                }
            } else if (percentage > 20) {
                audioLevelBar.style.background = 'linear-gradient(90deg, #4CAF50, #388E3C)';
                if (statusEl.className === 'status error') {
                    statusEl.textContent = '🔴 ¡AMPLIFICANDO EN VIVO! Habla normalmente';
                    statusEl.className = 'status active';
                }
            } else {
                audioLevelBar.style.background = 'linear-gradient(90deg, #2196F3, #1976D2)';
            }

            animationId = requestAnimationFrame(updateAudioLevel);
        }

        // Función de inicio mejorada
        async function startAmplifier() {
            try {
                statusEl.textContent = '🔄 Iniciando amplificador avanzado...';
                statusEl.className = 'status';
                startBtn.disabled = true;
                outputDeviceTip.style.display = 'block';

                if (!navigator.mediaDevices || !navigator.mediaDevices.getUserMedia) {
                    throw new Error('Tu navegador no soporta grabación de audio');
                }

                if (location.protocol !== 'https:' && location.hostname !== 'localhost') {
                    throw new Error('Necesitas HTTPS para usar el micrófono');
                }

                statusEl.textContent = '🎤 Accediendo al micrófono seleccionado...';
                
                const audioConfig = getAudioConfig();
                mediaStream = await navigator.mediaDevices.getUserMedia(audioConfig);

                const AudioContext = window.AudioContext || window.webkitAudioContext;
                audioContext = new AudioContext({
                    latencyHint: 'interactive',
                    sampleRate: 48000
                });

                if (audioContext.state === 'suspended') {
                    await audioContext.resume();
                }

                // Crear cadena de procesamiento mejorada
                microphone = audioContext.createMediaStreamSource(mediaStream);
                
                // Compresor para evitar distorsión
                compressorNode = audioContext.createDynamicsCompressor();
                compressorNode.threshold.setValueAtTime(-50, audioContext.currentTime);
                compressorNode.knee.setValueAtTime(40, audioContext.currentTime);
                compressorNode.ratio.setValueAtTime(12, audioContext.currentTime);
                compressorNode.attack.setValueAtTime(0.003, audioContext.currentTime);
                compressorNode.release.setValueAtTime(0.25, audioContext.currentTime);

                gainNode = audioContext.createGain();
                analyserNode = audioContext.createAnalyser();
                delayNode = audioContext.createDelay(0.2); // Hasta 200ms

                // Configurar analizador
                analyserNode.fftSize = 4096;
                analyserNode.smoothingTimeConstant = 0.9;

                // Configurar valores iniciales
                const currentVolume = parseInt(volumeSlider.value);
                const gain = Math.pow(currentVolume / 100, 1.1) * 1.5;
                gainNode.gain.setValueAtTime(gain, audioContext.currentTime);

                const currentDelay = parseInt(delaySlider.value);
                delayNode.delayTime.setValueAtTime(currentDelay / 1000, audioContext.currentTime);

                // Conectar cadena de procesamiento:
                // Micrófono -> Compresor -> Retardo -> Ganancia -> Analizador -> Salida
                microphone.connect(compressorNode);
                compressorNode.connect(delayNode);
                delayNode.connect(gainNode);
                gainNode.connect(analyserNode);
                gainNode.connect(audioContext.destination);

                isAmplifying = true;
                statusEl.textContent = '🔴 ¡AMPLIFICANDO CON PROCESAMIENTO AVANZADO!';
                statusEl.className = 'status active';
                startBtn.style.display = 'none';
                stopBtn.style.display = 'block';
                micIcon.className = 'microphone-icon pulse';
                micIcon.textContent = '🔴';
                audioLevelContainer.style.display = 'block
