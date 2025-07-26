<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Amplificador de Voz - Modo Clase</title>
    
    <meta name="theme-color" content="#667eea">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="apple-mobile-web-app-title" content="Amplificador Voz">
    <meta name="mobile-web-app-capable" content="yes">
    
    <link rel="icon" type="image/svg+xml" href="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA1MTIgNTEyIj48cmVjdCB4PSIwIiB5PSIwIiB3aWR0aD0iNTEyIiBoZWlnaHQ9IjUxMiIgZmlsbD0iIzY2N2VlYSIvPjx0ZXh0IHg9IjI1NiIgeT0iMzAwIiBmb250LXNpemU9IjIwMCIgdGV4dC1hbmNob3I9Im1pZGRsZSIgZmlsbD0id2hpdGUiPvCfj6Q8L3RleHQ+PC9zdmc+">
    
    <style>
        /* Reset y estilos base */
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
            user-select: none; /* Previene selección de texto accidental */
        }

        /* Contenedor principal */
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

        /* Títulos y subtítulos */
        h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            font-weight: 300;
        }

        .subtitle {
            font-size: 1.2em;
            opacity: 0.9;
            margin-bottom: 30px;
            color: #FFE082; /* Tono amarillo para subtítulo */
        }

        /* Mensajes de advertencia/información */
        .https-warning, .offline-ready, .install-section {
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 20px;
            font-size: 0.9em;
        }

        .https-warning {
            background: rgba(255, 152, 0, 0.2);
            border: 2px solid rgba(255, 152, 0, 0.5);
            display: none; /* Oculto por defecto, se muestra con JS */
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

        /* Estado del amplificador */
        .status {
            font-size: 1.3em;
            margin-bottom: 30px;
            padding: 20px;
            border-radius: 15px;
            background: rgba(255, 255, 255, 0.1);
            border: 2px solid rgba(255, 255, 255, 0.2);
            font-weight: 500;
            transition: background 0.3s ease, border-color 0.3s ease; /* Transición para cambios de estado */
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

        /* Controles de botones */
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
            touch-action: manipulation; /* Mejora respuesta táctil */
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
            animation: pulseRed 1.5s ease-in-out infinite; /* Animación para botón de detener */
        }

        .btn.danger:hover {
            background: linear-gradient(45deg, #d32f2f, #b71c1c);
        }

        @keyframes pulseRed {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        /* Controles deslizantes (sliders) */
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
            -webkit-appearance: none; /* Para personalizar en WebKit/Chrome */
            margin: 10px 0;
            cursor: grab; /* Cursor de arrastre */
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

        .volume-slider::-moz-range-thumb, .delay-slider::-moz-range-thumb {
            width: 25px;
            height: 25px;
            border-radius: 50%;
            background: linear-gradient(45deg, #FFE082, #FFC107);
            cursor: grab;
            border: none;
            box-shadow: 0 3px 8px rgba(0, 0, 0, 0.4);
        }

        .delay-slider::-webkit-slider-thumb, .delay-slider::-moz-range-thumb {
            background: linear-gradient(45deg, #9C27B0, #E91E63); /* Color diferente para el delay */
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
            color: #E1BEE7; /* Tono de púrpura para delay */
        }

        /* Sección de información y configuración inicial */
        .info {
            font-
