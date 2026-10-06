# Viabilidad técnica

> Fase A · Investigación. Fecha de consulta de todas las fuentes: **2026-10-06**. Precios en USD salvo indicación. Desde el entorno de investigación muchas webs oficiales (Google, Unity, Supabase, Photon, LiveKit, Agora, Daily, Cloudflare, Firebase, Blender, Meshy) estaban bloqueadas: en esos casos se cita el fragmento obtenido vía buscador o el repositorio de GitHub, y lo que no se ha podido leer queda como **no verificado**. Hechos y hipótesis van separados.

## Resumen

1. Todo lo que pide el brief es viable con librerías abiertas de licencia permisiva (MIT/Apache): MediaPipe para manos, sensores nativos para lanzar/sacudir, Colyseus o Cloudflare Durable Objects para salas con entrada y salida en caliente, WebRTC/LiveKit para voz.
2. Lo frágil no es la técnica sino el contexto: la cámara de gestos y el soplido funcionan en demo y se degradan en un bar (luz, ruido, móvil en la mano); hay que diseñarlos como momentos cortos, con calibración y con alternativa (grito, golpecito, sacudida).
3. Usar el micro como mecánica y tener chat de voz a la vez es un conflicto real: los SDK de voz procesan el audio (cancelación de eco, supresión de ruido) y un soplido es justo lo que suprimen. Recomendación: voz solo en modo remoto, y en ese modo sustituir "soplar" por otra entrada.
4. Motor, recomendación provisional en dos opciones: **Godot 4** (todo texto, MIT, APK ligero, sensores nativos, plugin de MediaPipe) o **web + Capacitor** (su experiencia, APK aún más ligero, pero rendimiento de WebView y cámara en WebView sin verificar). Unity queda tercero (solo si el concepto es 3D o necesita Vivox); Unreal, descartado.
5. Coste en el MVP: entre 0 y ~40 USD/mes sin voz; la voz es la única partida que escala mal por minutos (salvo Vivox, gratis hasta 5.000 usuarios concurrentes pero ligado a Unity). Hathora ha cerrado (mayo 2026) y Twilio Video cierra en diciembre de 2026: ni los consideréis.

---

## 1. Librerías y repos públicos por capacidad

Leyenda de licencia: MIT/Apache/BSD/ISC = OK para app comercial; **GPL/AGPL = RIESGO** (obliga a liberar el código del juego o a comprar licencia comercial).

### 1.1 Detección de manos y dedos

| Opción | Enlace | Licencia | Madurez | iOS / Android / motores | Rendimiento gama media | Coste |
|---|---|---|---|---|---|---|
| MediaPipe Tasks: Hand Landmarker y Gesture Recognizer | [github.com/google-ai-edge/mediapipe](https://github.com/google-ai-edge/mediapipe) | Apache-2.0 | 37,2k estrellas; release v1.0.0 (la página de releases no muestra el año; npm `@mediapipe/tasks-vision` va por 1.0.1, Apache-2.0: [registry.npmjs.org](https://registry.npmjs.org/@mediapipe/tasks-vision)) | Android (SDK ≥ 24), iOS, web (WASM), Python. Unity vía [MediaPipeUnityPlugin](https://github.com/homuler/MediaPipeUnityPlugin) (MIT, 2,5k, envuelve MediaPipe 0.10.22, sin WebGL). Godot vía [GDMP](https://github.com/j20001970/GDMP) (MIT, 132 estrellas, v0.6 del 16-09-2026, Android/iOS/Linux/Web). React Native: VisionCamera + TFLite (abajo) | Dato oficial: Hand Landmarker (full) **17,12 ms CPU / 12,27 ms GPU en Pixel 6** ([doc oficial, vía buscador](https://ai.google.dev/edge/mediapipe/solutions/vision/hand_landmarker)). Hipótesis: en gama media 2024-2026 (Snapdragon 6xx/7xx, Dimensity 7xx) 30-60 ms por frame con cámara incluida, es decir, 15-25 FPS de detección; calor y batería notables si dura más de un minuto | 0 |
| LiteRT (antes TensorFlow Lite) | [github.com/google-ai-edge/LiteRT](https://github.com/google-ai-edge/LiteRT) | Apache-2.0 | 3,5k estrellas; renombrado el 04-09-2024 ([blog Google](https://developers.googleblog.com/tensorflow-lite-is-now-litert/)) | Android (CPU/GPU/NPU), iOS (CPU/Metal), web | Es el runtime que usa MediaPipe por debajo; solo tiene sentido si entrenáis vuestro propio modelo de gestos | 0 |
| ML Kit (Google) | [github.com/googlesamples/mlkit](https://github.com/googlesamples/mlkit) | SDK propietario gratuito | Mantenido por Google | Android, iOS nativo | **No tiene API de manos**: el README oficial lista barcode, caras, etiquetado, objetos, texto (+ lenguaje natural y GenAI). Existe Pose Detection (cuerpo), pero no sirve para dedos | 0 |
| Apple Vision `VNDetectHumanHandPoseRequest` | [developer.apple.com](https://developer.apple.com/documentation/vision/vndetecthumanhandposerequest) | Propietaria, incluida en iOS | iOS 14+ | **Solo iOS**: 21 puntos por mano, `maximumHandCount` configurable ([doc Apple vía buscador](https://developer.apple.com/documentation/vision/vndetecthumanhandposerequest)) | FPS en iPhone: no verificado | 0 |
| OpenCV | [github.com/opencv/opencv](https://github.com/opencv/opencv) | Apache-2.0 (desde 4.5.0; antes BSD-3) ([opencv.org](https://opencv.org/license/)) | 91,1k estrellas | Android, iOS, Unity (asset de pago), web (opencv.js) | No trae detector de manos listo: habría que combinarlo con un modelo; para nosotros no merece la pena | 0 |
| Ultralytics YOLO (pose) | [github.com/ultralytics/ultralytics](https://github.com/ultralytics/ultralytics) | **AGPL-3.0 = RIESGO** (o licencia Enterprise de pago) | 62,2k estrellas | Exporta a ONNX/CoreML/TFLite | Sus modelos pose son de cuerpo (COCO-Pose), no de manos. Descartar | Enterprise: no verificado |
| TF.js `hand-pose-detection` | [github.com/tensorflow/tfjs-models](https://github.com/tensorflow/tfjs-models/tree/master/hand-pose-detection) | Licencia no mostrada en la página consultada (no verificado) | 14,8k estrellas (repo) | Web; runtimes `tfjs` y `mediapipe` | Es el mismo modelo MediaPipe Hands; preferible usar `@mediapipe/tasks-vision` directamente | 0 |
| React Native: VisionCamera + fast-tflite + react-native-mediapipe | [VisionCamera](https://github.com/mrousavy/react-native-vision-camera) · [fast-tflite](https://github.com/mrousavy/react-native-fast-tflite) · [react-native-mediapipe](https://github.com/cdiddy77/react-native-mediapipe) | MIT / MIT / MIT | 9,6k (V5) / 1,2k / 80 estrellas | iOS, Android | Frame processors en JS worklets con delegados GPU/CoreML/NNAPI; react-native-mediapipe está centrado en detección de objetos, no en manos | 0 |

**Qué gestos son fiables.** El Gesture Recognizer de MediaPipe clasifica 7 gestos predefinidos + "ninguno": puño cerrado, palma abierta, índice arriba, pulgar abajo, pulgar arriba, victoria y "I love you" ([model card oficial, PDF](https://storage.googleapis.com/mediapipe-assets/gesture_recognizer/model_card_hand_gesture_classification_with_faireness_2022.pdf)). Contar dedos (1-5) se hace con reglas sobre los 21 puntos y es fiable con la mano abierta de frente a 30-60 cm. La misma model card declara fuera de alcance los gestos a dos manos y los gestos con movimiento (saludar), y avisa de que **no se ha probado en móviles de gama baja, poca luz ni desenfoque de movimiento**: justo las condiciones de un bar. Hipótesis de diseño: usar la cámara en ventanas de 2-3 s ("enseña un número"), con el móvil quieto, nunca como entrada continua.

### 1.2 Detección de soplido con ruido ambiente

No existe una librería madura y multiplataforma de "blow detection"; lo que hay son técnicas pequeñas y repos de demostración.

| Opción | Enlace | Licencia | Madurez | Plataformas | Técnica | Coste |
|---|---|---|---|---|---|---|
| Web Audio API (AnalyserNode) a medida | [whistlerr (npm)](https://www.npmjs.com/package/whistlerr) describe la banda 500-5.000 Hz para soplido/silbido | Propia | Sois vosotros | Web, Capacitor, Expo (con módulo) | RMS + espectro | 0 |
| blowawish | [registry.npmjs.org/blowawish](https://registry.npmjs.org/blowawish) | ISC | 1.0.10; umbral de intensidad 0-1, sin espectro | Web | Solo volumen: inútil en un bar | 0 |
| JS-Breathing-Detection | [github.com/Breathinglabs/JS-Breathing-Detection](https://github.com/Breathinglabs/JS-Breathing-Detection) | MIT | 29 estrellas, 2 commits | Web | Respiración por micro | 0 |
| UnityMicBlowDetection | [github.com/eriseven/UnityMicBlowDetection](https://github.com/eriseven/UnityMicBlowDetection) | MIT | 0 estrellas, 13 commits | Unity | Demo | 0 |
| PandaSuite "Blow sensor" | [docs.pandasuite.com](https://docs.pandasuite.com/essentials/components/blow-sensor/) | Propietario (no-code) | Producto comercial | iOS/Android nativo, no web | **Saturación del micro** (móvil pegado a la boca) | De pago, no aplicable |
| Receta clásica nativa | [Foro Solar2D](https://forums.solar2d.com/t/detect-microphone-volume-blowing-into-microphone/285743) | — | — | iOS: AVAudioRecorder + filtro paso bajo; Android: PCM + FFT | El soplido da un espectro **ancho y plano** (sin armónicos); se mide la desviación típica del espectro | 0 |

**Fiabilidad en un bar (análisis, hipótesis).** Un umbral de volumen absoluto no funciona: el ruido de fondo de un bar ya supera el umbral. Lo que sí funciona razonablemente: (1) **calibración rápida** de 1-2 s del ruido ambiente al empezar la ronda y detección por **delta relativo**; (2) **planitud espectral**: el soplido es ruido ancho sin tono, mientras que voces y música tienen armónicos; (3) **proximidad**: soplar a 2-3 cm del micro satura el canal de forma inconfundible (es lo que usa PandaSuite). Combinando las tres, "soplar pegado al móvil" es fiable incluso con ruido; "soplar a 20 cm" no lo es. Alternativas por orden de robustez en bar: golpecitos en el móvil (acelerómetro, no micro), sacudir, gritar (volumen relativo con calibración: cada móvil detecta al que tiene más cerca), soplar.

**Conflicto con el chat de voz.** En presencial no hay chat de voz, así que el micro queda libre para la mecánica. En remoto el conflicto es real:

- Hecho: en Android, la fuente `VOICE_COMMUNICATION` aplica cancelación de eco, control automático de ganancia y supresión de ruido, y `UNPROCESSED`/`MIC` no (documentación de `MediaRecorder.AudioSource`; la página no se ha podido leer hoy desde este entorno, **no verificado**). Hecho conocido, no verificado hoy: en iOS hay una única `AVAudioSession` por app y el modo `.voiceChat` activa el procesado de voz. WebRTC (y cualquier SDK sobre él) toma el micro con ese procesado por defecto; en web los constraints `noiseSuppression`/`autoGainControl`/`echoCancellation` se pueden pedir a `false` (MDN bloqueada hoy, **no verificado**).
- Consecuencia: un soplido es ruido ancho de banda, exactamente lo que la supresión de ruido elimina. Detectar soplido sobre el stream de voz procesado es poco fiable, y abrir una segunda captura "cruda" en paralelo no está garantizado en ninguna de las dos plataformas (hipótesis a probar).
- Recomendación: en modo remoto, la mecánica de micro pasa a ser **"grito/volumen"** (sobrevive al procesado) o se sustituye por sacudida/golpecito; y mientras dura la mecánica se silencia la transmisión de voz (ducking). Si la voz va por Discord/WhatsApp (app externa), nuestra app pedirá el micro con la llamada en segundo plano: en iOS eso puede interrumpir la llamada (riesgo a probar en dispositivo, hipótesis).

### 1.3 Giroscopio y acelerómetro

| Opción | Enlace | Licencia | Madurez | Plataformas | Notas de rendimiento/permisos | Coste |
|---|---|---|---|---|---|---|
| Android `SensorManager` | [developer.android.com](https://developer.android.com/develop/sensors-and-location/sensors/sensors_motion) | SO | Estable | Android | **Sin permiso** para acelerómetro/giroscopio. Desde Android 12 la frecuencia está limitada (200 Hz requiere `HIGH_SAMPLING_RATE_SENSORS`). Tipos útiles: `LINEAR_ACCELERATION` (sin gravedad), `ROTATION_VECTOR` | 0 |
| iOS CoreMotion | [developer.apple.com/documentation/coremotion](https://developer.apple.com/documentation/coremotion) | SO | Estable | iOS | Sin diálogo de permiso para movimiento en app nativa (sí hace falta `NSMotionUsageDescription` si se usa CMMotionActivity; no verificado hoy) | 0 |
| Web `DeviceMotionEvent` / `DeviceOrientationEvent` | [MDN requestPermission](https://developer.mozilla.org/en-US/docs/Web/API/DeviceOrientationEvent/requestPermission_static) · [yal.cc](https://yal.cc/js-device-motion/) · [Foro Apple](https://developer.apple.com/forums/thread/128376) | Estándar | Estable | Safari iOS 13+, Chrome Android | iOS 13+: `requestPermission()` **solo desde un gesto del usuario y solo en HTTPS**; `touchstart` no cuenta como gesto. **En WKWebView (Capacitor) no existe `requestPermission`: hay acceso directo** | 0 |
| Capacitor Motion | [github.com/ionic-team/capacitor-plugins/motion](https://github.com/ionic-team/capacitor-plugins/tree/main/motion) | MIT | Oficial | iOS, Android, web | Envuelve las Web APIs anteriores (`accel`, `orientation`) | 0 |
| Expo `expo-sensors` | [github.com/expo/expo/packages/expo-sensors](https://github.com/expo/expo/tree/main/packages/expo-sensors) | MIT (repo Expo) | Oficial, SDK 57 | iOS, Android | Accelerometer, Gyroscope, DeviceMotion, Magnetometer, Barometer, Pedometer, luz | 0 |
| Godot `Input.get_accelerometer/get_gyroscope/get_gravity/get_magnetometer` | [Input.xml (fuente)](https://github.com/godotengine/godot/blob/master/doc/classes/Input.xml) | MIT | 4.7.2 | **Solo Android e iOS** (en web/editor devuelve cero); en Android hay que activar `input_devices/sensors/*` en ProjectSettings | 0 |
| Unity Input System (`Gyroscope`, `Accelerometer`, `AttitudeSensor`) | docs.unity3d.com | Unity Companion | Estable | iOS, Android | Documentación no accesible hoy: **no verificado** | 0 |
| Librerías "shake": shake.js, Square Seismic | [shake.js](https://github.com/alexgibson/shake.js) · [seismic](https://github.com/square/seismic) | MIT (no verificado) / Apache-2.0 | **Ambas archivadas** (29-12-2020 y 26-11-2024) | Web / Android | Son 100 líneas: mejor escribir la nuestra | 0 |

**Calibración entre móviles (hipótesis de ingeniería).** Las unidades están estandarizadas (m/s², rad/s), pero varían la frecuencia de muestreo (web ~60 Hz, Android hasta 200 Hz, iOS hasta 100 Hz), los ejes (web alpha/beta/gamma frente a CoreMotion/Android) y el ruido. Para "lanzar": usar aceleración lineal (sin gravedad), detectar pico de módulo por encima de un umbral relativo a 1 s de calibración en reposo, y mandar al servidor solo el evento (dirección + intensidad normalizada 0-1), nunca el stream. Para "mover la vista": `ROTATION_VECTOR`/attitude con suavizado; en web funciona, pero con 60 Hz y latencia de WebView.

### 1.4 Multijugador por salas con entrada y salida en caliente

**Autoritativo frente a P2P, para nosotros.** Las trampas no importan, pero sí dos cosas: que nadie sea imprescindible y que una desconexión no rompa la ronda. En P2P (malla WebRTC o "un cliente es host", que es el modelo de Playroom y de Godot high-level por defecto) el estado vive en un móvil: si ese móvil se va, hay que migrar el host, lo más frágil que existe. Con una **sala autoritativa ligera** (Colyseus, Durable Objects, Nakama) el estado vive en el servidor, el que entra recibe el estado actual, el que se va simplemente desaparece y el que se reconecta vuelve a su asiento. Para 2-6 jugadores y rondas cortas, el servidor es trivial y la latencia europea (hipótesis: 20-60 ms RTT desde España a Frankfurt/París/Londres por Wi-Fi o 4G/5G, no medido) sobra. Conclusión: **autoritativo, pero "tonto"**: valida poco, replica estado y gestiona presencia.

| Opción | Enlace | Licencia | Madurez | Clientes | Reconexión y presencia | Coste a 0 / 1.000 / 10.000 salas·mes (ver supuestos en §5) |
|---|---|---|---|---|---|---|
| **Colyseus** | [github.com/colyseus/colyseus](https://github.com/colyseus/colyseus) | MIT | 7,3k estrellas; release 0.18 (25 de agosto; GitHub no muestra el año, interpretado 2026) | JS/TS, React, **Unity, Godot**, GameMaker, Defold, Construct, Haxe, C | "Reconnection support out of the box" (`allowReconnection`), salas con filtrado y cola | Self-host: VPS 5-20 USD (hipótesis). Colyseus Cloud **desde 15 USD/mes**, sin límite de CCU ni ancho de banda ([docs.colyseus.io, vía buscador](https://docs.colyseus.io/cloud/pricing-billing)) → 0 (local) / 15 / 15-60 |
| **Nakama** | [github.com/heroiclabs/nakama](https://github.com/heroiclabs/nakama) | Apache-2.0 | 13,5k; v3.41.0 (18-09-2026) | .NET/Unity, JS, Java, Unreal, **Godot**, Defold, Swift | Match handlers (Go/TS/Lua), presencia, parties, matchmaker | Self-host gratis (Go + Postgres). Heroic Cloud: por núcleos de CPU, sin límite de CCU; **precio base no verificado** ([heroiclabs.com/pricing](https://heroiclabs.com/pricing)); Satori desde 1.800 USD/mes (no es necesario). Más pesado de operar que Colyseus para 2 personas |
| **Supabase Realtime** | [github.com/supabase/realtime](https://github.com/supabase/realtime) | Apache-2.0 | 7,7k | JS (y cualquier WebSocket) | Presence y Broadcast integrados; **sin estado de sala en servidor** (hay que llevarlo en Postgres o en un cliente) y el README avisa: "the server does not guarantee that every message will be delivered" | Límites verificados en [docs (repo)](https://github.com/supabase/supabase/blob/master/apps/docs/content/guides/realtime/limits.mdx): Free 200 conexiones, 100 msg/s, 256 KB; Pro 500 conexiones, 500 msg/s. Planes 0 / 25 / 599 USD y cuotas de 2 M (Free) y 5 M (Pro) mensajes/mes (fuente secundaria [jetadmin.io](https://www.jetadmin.io/blog/supabase-pricing-2026-guide-to-plans-limits-and-real-world-costs/)). **Cada mensaje se cuenta por destinatario** (verificado en docs). Exceso por paquetes de 1 M mensajes: precio no verificado |
| **PartyKit / Cloudflare Durable Objects** | [partykit/partykit](https://github.com/partykit/partykit) · [cloudflare/partyserver](https://github.com/cloudflare/partyserver) | MIT / ISC | 5,7k / 1,3k; PartyKit es de Cloudflare ([blog](https://blog.cloudflare.com/cloudflare-acquires-partykit)) y el desarrollo pasó a `partyserver` | JS/TS (WebSocket desde cualquier motor) | Un Durable Object por sala = estado en servidor con WebSocket Hibernation; reconexión por id de sala | Plan gratuito DO: 100.000 peticiones/día y 313.000 GB-s/día; almacenamiento SQLite se cobra desde enero 2026 solo en plan de pago ([changelog, vía buscador](https://developers.cloudflare.com/changelog/2025-12-12-durable-objects-sqlite-storage-billing)). Workers Paid 5 USD/mes + uso (no verificado hoy) → 0 / 5 / 5-30 (hipótesis) |
| Photon Fusion / PUN | [doc.photonengine.com/photon/v1/pricing](https://doc.photonengine.com/photon/v1/pricing) (vía buscador) | Propietaria | Muy maduro (Unity) | Unity (Fusion/PUN); Realtime SDK para otros | PlayerTTL/reconexión: no verificado hoy | 20 CCU gratis (desarrollo); **100 CCU gratis** para una app comercial Fusion/Quantum; Fusion 500 CCU 125 USD/mes, 1.000 CCU 250. PUN: 100 CCU 95 USD/12 meses → 0 / 0 / 0-125 |
| Unity Netcode for GameObjects + Relay + Lobby | [NGO](https://github.com/Unity-Technologies/com.unity.netcode.gameobjects) · [unity.com/pricing](https://unity.com/products/gaming-services/pricing) (vía buscador) | NGO **MIT** (LICENSE.md verificado) | 2,3k | Unity | Host-cliente por defecto (migración de host no incluida) | Relay: **50 CCU medios/mes gratis**, luego 0,16 USD/CCU; Lobby: 10 GiB/mes gratis, 0,09 USD/GiB → 0 / 0 / 0 (28 CCU medios en el escenario de 10.000 salas) |
| Godot high-level multiplayer + servidor propio | [godot-docs](https://github.com/godotengine/godot-docs/blob/master/tutorials/networking/high_level_multiplayer.rst) | MIT | 4.7 | Godot | Peers ENet, WebSocket, WebRTC; autoridad por nodo; servidor dedicado headless | Un Godot headless en VPS: 5-20 USD (hipótesis). Hay que escribir reconexión y persistencia a mano |
| Socket.IO | [github.com/socketio/socket.io](https://github.com/socketio/socket.io) | MIT | 63,2k | JS; clientes nativos de terceros | Sin concepto de sala con estado; todo a mano | VPS 5-20 USD. Solo si queréis control total |
| Liveblocks | [liveblocks.io/pricing](https://liveblocks.io/pricing.md) (vía buscador) | Propietaria | Orientado a colaboración, no a juegos | JS | Presence y storage CRDT | Free: 500 salas activas/mes, MAU ilimitados; Pro 30 USD/mes + 0,03 USD/sala; Team 600 → 0 / 30-45 / 300+. **No merece la pena**: cobra por sala |
| Firebase Realtime Database | firebase.google.com/pricing | Propietaria | Muy maduro | iOS, Android, web, Unity | Presence con `onDisconnect` | Página bloqueada hoy: **no verificado** (de memoria: Spark 100 conexiones simultáneas; Blaze por GB). Latencia y modelo de datos poco adecuados a rondas rápidas |
| Hathora | — | — | **Cerrado el 05-05-2026** tras la compra por Fireworks AI ([crux](https://crux.supercraft.host/blog/hathora-shut-down-where-to-go-after-may-2026/), [TechSpot](https://www.techspot.com/news/111969-stormgate-servers-go-dark-following-ai-focused-hosting.html), vía buscador) | — | — | Descartado |
| **Playroom Kit** | [npm playroomkit](https://registry.npmjs.org/playroomkit) · [joinplayroom.com](https://joinplayroom.com) | SDK ISC (npm); servicio propietario | 0.0.97 (sigue en 0.0.x); dependencias React 17-18; SDK de Discord Embedded App opcional | JS/React (Unity y Godot: no verificado hoy) | Lobby, matchmaking, estado global y por jugador, RPC. Modelo "stream mode" (pantalla + móviles como mandos) o "joined" | Freemium, de pago **desde 10 USD/mes** (fuente secundaria, página de precios bloqueada). Ideal para **prototipo web en días**; para producto, dependencia de un servicio pequeño en versión 0.0.x |
| **Rune** (fue Dusk en 2024-2025) | [github.com/rune/rune](https://github.com/rune/rune) · [npm rune-sdk](https://registry.npmjs.org/rune-sdk) | SDK MIT | 425 estrellas; `rune-sdk` 6.0.8 (`dusk-games-sdk` quedó en 4.21.18); 8 M USD de inversión ([techleap](https://finder.techleap.nl/news/feed/dusk-raises-8m-for-game-platform)) | JS/TS, React, Svelte, Three.js, PixiJS, Phaser | Predict-rollback, voz y chat incluidos; **los juegos solo se ejecutan dentro de la app Rune** (10 M instalaciones) | Gratis. Monetización: Rune no muestra anuncios ni cobra; paga un "creator fund" por retención, compartidos y horas jugadas (mínimo 100 h/mes y 5 % de retorno; 1 USD = 10.000 créditos) ([making-money.md](https://github.com/rune/rune/blob/staging/docs/docs/publishing/making-money.md)). **Incompatible con el innegociable "app propia en las tiendas"**: solo como laboratorio de prototipos |

Opciones que no merecen la pena para dos personas: Nakama en Heroic Cloud (pensado para estudios), Liveblocks (cobra por sala), Firebase RTDB (modelo de datos y coste por descarga), Socket.IO desde cero (reinventar Colyseus), Hathora (cerrado).

### 1.5 Chat de voz para el modo remoto

| Opción | Enlace | Licencia | iOS / Android / motores | Precio | Notas |
|---|---|---|---|---|---|
| WebRTC puro (malla P2P) | Estándar W3C/IETF | BSD (libwebrtc) | Web/Capacitor nativo del WebView; Godot `WebRTCPeerConnection`; Unity vía paquetes | 0 + STUN/TURN (un `coturn` en VPS: 5 USD, hipótesis) | Con 2-6 participantes la malla funciona; sin moderación ni grabación. Toma el micro con procesado de voz |
| **LiveKit** | [github.com/livekit/livekit](https://github.com/livekit/livekit) | Apache-2.0 | SDKs iOS, Android, Unity, Flutter, React Native, JS; **no Godot** | Self-host: binario único/Docker. Cloud: 99,99 % y 19+ regiones; **precios no verificados** (web bloqueada) | 21,3k estrellas; v1.13.7 (14 de septiembre; año no mostrado). SFU: escala y permite moderación server-side |
| Agora | agora.io/pricing | Propietaria | iOS, Android, Unity, web, Flutter, RN | **No verificado** (de memoria: 10.000 min gratis/mes; audio ~0,99 USD/1.000 min) | Muy maduro; coste por minuto |
| Vivox (Unity) | [unity.com/pricing](https://unity.com/products/gaming-services/pricing) · [support.unity.com, vía buscador](https://support.unity.com/hc/en-us/articles/31045802890260) | Propietaria | Unity (también SDKs nativos/Unreal: no verificado) | **Gratis hasta 5.000 usuarios concurrentes pico**; después 2.000 USD por cada 5.000 PCU | Cobra por concurrencia, no por minutos: para un indie es voz gratis. Gran argumento a favor de Unity si la voz es central |
| Photon Voice | photonengine.com | Propietaria | Unity | **No verificado** | Atado a Photon |
| Daily | daily.co/pricing | Propietaria | Web, iOS, Android, RN, Flutter | **No verificado** | Por minuto de participante |
| Twilio Video | [mirrorfly](https://www.mirrorfly.com/blog/twilio-programmable-video-shut-down/) (vía buscador) | — | — | — | **Fin de vida: 05-12-2026**, sin nuevos clientes. Descartado |
| Discord / WhatsApp externos | — | — | Todo | 0 | "Abrid una llamada y jugad". Sin coste, sin moderación propia, y el micro lo tiene la otra app (ver §1.2). Discord Social SDK (voz integrada gratuita): **no verificado hoy** |

**Moderación.** Cualquier voz en app propia con desconocidos obliga a reporte, bloqueo y política (lo tratará el doc de publicación). Entre amigos (salas por código, sin matchmaking público) el riesgo es bajo. Recomendación MVP: **sin voz integrada**; el modo remoto empieza con "usad Discord/WhatsApp" y se mide cuánta gente juega en remoto antes de pagar la integración.

### 1.6 Clip automático de los últimos segundos

| Opción | Enlace | Licencia | Plataformas | Permisos y privacidad | Coste |
|---|---|---|---|---|---|
| ReplayKit (`RPScreenRecorder.startCapture`) | [developer.apple.com/documentation/replaykit](https://developer.apple.com/documentation/replaykit) | SO | iOS 11+ | Página no legible hoy (**no verificado**). Comportamiento conocido: diálogo de consentimiento del sistema la primera vez por sesión; graba solo la propia app; entrega sample buffers que se pueden guardar en un búfer circular de N segundos | 0 |
| MediaProjection | [developer.android.com](https://developer.android.com/media/grow/media-projection) (verificado) | SO | Android 5+ | **Consentimiento del usuario antes de cada sesión** de captura; en Android 14+ foreground service de tipo `mediaProjection` y opción de compartir solo la app; en Android 15 QPR1+ un chip permanente en la barra de estado. Para un clip "automático" es fricción y sospecha | 0 |
| VideoKit (sucesor de NatCorder) | [github.com/videokit-ai/videokit](https://github.com/videokit-ai/videokit) | Repo Apache-2.0; requiere clave de acceso de videokit.ai | Unity: Android 24+, iOS 14+, macOS, Windows, WebGL (Unity 6) | Graba pantalla, cámara y micro, exporta MP4/GIF y comparte | Precios: **no verificado** (web bloqueada) |
| Unity Recorder | docs.unity3d.com | Unity | Solo Editor (no en builds; no verificado hoy) | — | Descartado para runtime |
| Grabar la cámara frontal | APIs de cámara de cada plataforma | SO | Todas | Permiso de cámara + sale la cara: consentimiento explícito y riesgo RGPD/menores. Muy potente para TikTok, muy delicado | 0 |
| **Replay desde el estado del juego** | Propio | — | Todas | **Sin grabar pantalla ni cámara**: el servidor ya tiene los eventos de la ronda; el cliente los re-renderiza en vertical con la "pantalla de culpable" y exporta vídeo (en Godot/Unity con captura de viewport a vídeo; en web con `MediaRecorder` sobre canvas). Sin permisos, sin caras | 0 |

Recomendación: el clip del MVP se genera **desde el estado**, no grabando. Grabar cámara queda como opción opt-in posterior.

---

## 2. Primera comparativa de motores

| Criterio | Unity 6 | Godot 4.7 | Unreal 5 | Web + Capacitor (Next.js/React o Svelte + PixiJS/Phaser/Three) | Expo / React Native | Flutter + Flame |
|---|---|---|---|---|---|---|
| Trabajo con Claude Code | Escenas YAML y C# son texto, pero **el Editor es imprescindible** (prefabs, import de assets). Unity lanzó su MCP oficial en beta el 11-05-2026, solo Unity 6 y con suscripción Unity AI ([gamedev.net](https://gamedev.net/news/4376-unity-ai-open-beta-how-to-get-started-with-mcp/)); el comunitario [unity-mcp](https://github.com/CoplayDev/unity-mcp) (MIT, 14,7k, v10.0.0 del 30-06-2026) | **Todo texto**: `.tscn`, `.tres`, GDScript, `project.godot`. [godot-mcp](https://github.com/Coding-Solo/godot-mcp) (MIT, 6,0k) lanza el editor, ejecuta y lee la consola. Limitación: el agente no ve el juego en ejecución ([summerengine](https://www.summerengine.com/blog/claude-for-godot)) | **Blueprints binarios**: opaco para un agente. C++ sí, pero compila lento | Todo texto, el entorno donde Claude Code rinde mejor y donde vosotros ya trabajáis | Todo texto | Dart, todo texto |
| Peso app vacía | Foros: APK vacío ~10-20 MB; un proyecto 2D real citado: 87-96 MB ([discussions.unity.com](https://discussions.unity.com/t/android-the-package-size-increased-by-10-when-using-unity-6/1539185)); fuente secundaria | Foro: APK vacío **~19 MB**, ~13 MB recortando módulos ([forum.godotengine.org](https://forum.godotengine.org/t/absurd-file-size-increase-when-my-project-is-exported-to-apk/130000)); secundaria | Decenas de MB como mínimo (no verificado) | Foro: Android **~3 MB**; en iOS el bundle de build es grande pero la tienda lo optimiza ([forum.ionicframework.com](https://forum.ionicframework.com/t/capacitor-app-size-compared-to-cordova/213063)); secundaria | No verificado (de memoria: 20-30 MB) | No verificado |
| Rendimiento gama media | Excelente | Muy bueno en 2D; Vulkan/GLES3 según dispositivo | Excesivo para esto | **Riesgo**: animación a 60 fps en WebView depende del dispositivo; PixiJS/Phaser WebGL van bien en Chrome Android moderno (hipótesis, no medido) | Bueno para UI; juego fluido requiere Skia/Reanimated | Bueno |
| Crossplay, sensores, cámara, MediaPipe | Nativo; MediaPipeUnityPlugin (MIT) | Sensores solo Android/iOS (verificado); cámara: `CameraServer` en Android/iOS/Linux/macOS, **no web** (verificado en fuente); MediaPipe vía GDMP | Nativo | Sensores por Web API (sin permiso en WKWebView); cámara por `getUserMedia` en WebView (iOS 14.3+, no verificado hoy); MediaPipe web por WASM: **rendimiento en WebView no verificado** | VisionCamera + fast-tflite (MIT) | Plugins de la comunidad |
| Multijugador / voz / compras / anuncios | NGO (MIT) + Relay/Lobby; Colyseus y Nakama; Photon. **Vivox gratis hasta 5.000 PCU**. Unity IAP, RevenueCat, AdMob, LevelPlay | Colyseus y Nakama con SDK Godot; high-level propio. Voz: sin SDK LiveKit/Agora oficial (WebRTC a mano). IAP: [godot-google-play-billing](https://github.com/godotengine/godot-google-play-billing) (MIT, Godot 4.2+) y [godot-ios-plugins](https://github.com/godotengine/godot-ios-plugins) (MIT, InAppStore). Ads: [poingstudios AdMob](https://github.com/poingstudios/godot-admob-plugin) (MIT, 631 estrellas, Godot 4.5+, rewarded) | Todo, pero sobredimensionado | Colyseus/PartyKit/Supabase en JS; voz WebRTC/LiveKit JS; [@revenuecat/purchases-capacitor](https://github.com/RevenueCat/purchases-capacitor) (MIT) y [@capacitor-community/admob](https://github.com/capacitor-community/admob) (MIT, v8.2.0, banner/interstitial/rewarded) | Mismos backends; react-native-purchases y react-native-google-mobile-ads (existen; no verificados hoy) | Ecosistema pequeño |
| Curva para vuestro perfil | Media-alta: C#, Editor, pipeline de assets | **Media**: GDScript se parece a Python; nodos y señales se aprenden en días | Alta | **Baja**: es lo que ya hacéis | Baja-media | Media (Dart) |
| Licencia y coste | Personal gratis hasta 200.000 USD de ingresos/financiación; Pro 2.310 USD/año por asiento desde el 12-01-2026; Runtime Fee cancelada en septiembre de 2024 ([unity.com, vía buscador](https://unity.com/pricing-updates)) | **MIT**, 0 | 5 % de regalías sobre ingresos brutos acumulados por encima de 1 M USD; 3,5 % si se lanza en Epic Games Store desde el 01-01-2025 ([unrealengine.com/faq, vía buscador](https://www.unrealengine.com/en-US/faq)) | MIT (Capacitor 8.5.2 del 11-09-2026; Phaser 4.2.1, PixiJS 8, three.js: todos MIT) | MIT (Expo SDK 57) | BSD-3 (no verificado hoy) / Flame MIT |
| Riesgos propios | Editor obligatorio, builds pesadas, telemetría/licencia cambiante | Comunidad móvil menor que Unity; plugins nativos mantenidos por pocos (GDMP: 132 estrellas) | Peso, equipo de 2, Blueprints | 60 fps en WebView, cámara+ML en WebView, grabación de pantalla requiere plugin nativo, PWA en iOS muy limitada (sin grabación, sensores con gesto) | Capa RN sin motor de juego; "juice" a mano | Comunidad pequeña para party games |

**Recomendación provisional (ordenada).**

1. **Godot 4** si el concepto es físico y "con juice" (lanzar, globos, partículas, pantalla de culpable animada), 2D o 2.5D. Todo en texto para Claude Code, MIT, 13-19 MB, sensores y cámara nativos, GDMP para MediaPipe, SDKs de Colyseus y Nakama, IAP y AdMob con plugins MIT. Lo que pierde: voz (no hay SDK de LiveKit/Agora; WebRTC a mano o voz externa) y un ecosistema móvil más pequeño.
2. **Web + Capacitor** (Next.js o Svelte + PixiJS o Phaser) si el concepto es de interfaz (palabras, cartas, temporizadores, símbolos) con animación moderada. Es vuestra experiencia, el APK más ligero y la ruta continua desde el prototipo. Antes de elegirla hay que medir dos riesgos en un Android de gama media real: 60 fps sostenidos en WebView y MediaPipe web en WebView.
3. Unity solo si el concepto es 3D o la voz integrada es central (Vivox gratis). Unreal, Flutter/Flame y Expo: no para este equipo y este juego.

La decisión final depende del concepto y del estilo visual (2D/2.5D/3D) de las Fases B y C.

| Si el concepto necesita… | Motor más adecuado |
|---|---|
| Físicas, partículas, "lanzar" con giroscopio y reacciones en pantalla | Godot 4 |
| Cámara con gestos como mecánica frecuente | Godot (GDMP) o Unity (MediaPipeUnityPlugin); en web solo si la medición en WebView es buena |
| Interfaz, texto, cartas, temporizadores, símbolos | Web + Capacitor |
| 3D o 2.5D con modelos | Godot 4 (ligero) o Unity (si hace falta más herramienta) |
| Voz integrada desde el día uno | Unity + Vivox (gratis hasta 5.000 PCU) o web/Godot + LiveKit self-host |
| Prototipo en una semana para validar diversión | PWA web (sin motor) |
| Clip automático sin permisos | Cualquiera, generándolo desde el estado; en web con `MediaRecorder` sobre canvas |

---

## 3. Blender: solo para assets

Blender (GPL, gratis; última versión etiquetada **5.2.2**, 14-09-2026, según [tags del espejo en GitHub](https://github.com/blender/blender/tags)) no es un motor ni debe serlo aquí. Aporta: en **2D**, Grease Pencil para animación de personajes con cámara y luz reales (útil para una mascota con "volumen"); en **2.5D**, render de sprites desde modelos low-poly (cámara ortográfica, 8 direcciones) que luego se usan como atlas en Godot o PixiJS; en **3D**, modelado, rig y exportación glTF directa a Godot/Unity/three.js. Su coste real es tiempo de aprendizaje: para dos personas sin artista, rinde más como "exportador" de lo que generan otras herramientas que como herramienta principal.

Alternativas más rápidas (precios **no verificados** hoy, webs bloqueadas; los modelos de precio se citan de memoria):

| Necesidad | Herramienta | Nota |
|---|---|---|
| Píxel-art y sprites animados | Aseprite (pago único, código visible), Krita (GPL, gratis) | Licencia GPL de la herramienta no afecta a los assets |
| UI y pantallas | Figma (plan gratuito) | Exporta SVG a Godot/web directamente |
| 2.5D/3D rápido para web | Spline (plan gratuito; exporta a web y glTF) | Buen encaje con three.js |
| Generación de sprites con IA | Midjourney, Scenario, Layer.ai, o modelos locales | Revisad la licencia comercial de cada uno y la política de las tiendas sobre contenido generado; coherencia de estilo entre sprites es el problema real |
| Modelos 3D con IA | Meshy, Tripo (créditos mensuales, plan gratuito limitado) | Topología sucia: pasar por Blender para limpiar y reducir polígonos |

---

## 4. Arquitectura mínima para el prototipo (no para el producto)

Objetivo: validar la diversión en 1-2 semanas con gente que nunca haya jugado, con lo que ya sabéis hacer.

- **Cliente:** PWA con Next.js (o Vite + React/Svelte), un `<canvas>` con PixiJS si hace falta animación, pantalla vertical, unión por código de 4 letras o QR. Sin tienda, sin instalación: se abre un enlace.
- **Salas:** dos opciones equivalentes en velocidad. (a) **Supabase Realtime** (Broadcast + Presence) con el estado de la ronda en una tabla y un cliente "director" elegido por orden de llegada (aceptable en prototipo, no en producto). (b) **Playroom Kit** o un **Durable Object/PartyKit** con el estado en servidor: diez líneas más y ya tenéis entrada/salida en caliente real. Recomendación: (b) con PartyKit/partyserver, porque el prototipo de salas se reaprovecha.
- **Sensores:** `DeviceMotionEvent` con el botón "activar movimiento" (gesto obligatorio en iOS, HTTPS obligatorio). Sirve para validar lanzar y sacudir.
- **Cámara:** `@mediapipe/tasks-vision` en el navegador funciona en Safari y Chrome; válido para probar si "enseñar un número" tiene gracia, aunque el rendimiento no sea el final.
- **Micro:** Web Audio API con calibración de 2 s; suficiente para probar grito/soplido en un bar de verdad.

Lo que **no** se puede validar con esta pila: fricción real de descarga e instalación (es el centro del doc de mercado), rendimiento final de cámara y animación en WebView empaquetado, voz integrada, clip con `MediaRecorder` en iOS (parcial), permisos de tienda, compras y anuncios, comportamiento al bloquear la pantalla o cambiar de app a mitad de ronda.

---

## 5. Costes mensuales estimados en el MVP

Supuestos (hipótesis): una sala = una sesión de ~30 min con 4 jugadores de media; 1.000 salas/mes ≈ 2.000 horas-jugador y picos de 10-30 usuarios concurrentes; 10.000 salas/mes ≈ 20.000 horas-jugador, ~28 CCU medios y picos de 100-300. Mensajes de estado: 2-10 por segundo y sala, contados **por destinatario** en Supabase. Cuentas de desarrollador: en el doc de publicación.

| Partida | 0 salas (desarrollo) | 1.000 salas/mes | 10.000 salas/mes | Fuente |
|---|---|---|---|---|
| Salas: Colyseus Cloud | 0 (local) | 15 USD | 15-60 USD (hipótesis: 1-2 servidores) | [docs.colyseus.io](https://docs.colyseus.io/cloud/pricing-billing) vía buscador |
| Salas: Cloudflare Durable Objects | 0 | 0-5 USD | 5-30 USD (hipótesis) | [changelog Cloudflare](https://developers.cloudflare.com/changelog/2025-12-12-durable-objects-sqlite-storage-billing) vía buscador; plan de pago no verificado |
| Salas: Supabase Realtime | 0 | 25 USD (Pro) + exceso: con 5 msg/s × 5 destinatarios × 1.800 s ≈ 45.000 mensajes por sala → **45 M/mes**, muy por encima de los 5 M incluidos; precio del exceso no verificado | Inviable por mensajes salvo diseño de muy baja frecuencia (1 msg/s → 9 M/mes) | [limits.mdx](https://github.com/supabase/supabase/blob/master/apps/docs/content/guides/realtime/limits.mdx); cuotas vía [jetadmin](https://www.jetadmin.io/blog/supabase-pricing-2026-guide-to-plans-limits-and-real-world-costs/) |
| Salas: Photon Fusion (Unity) | 0 | 0 (≤ 100 CCU) | 0-125 USD (500 CCU) | [doc.photonengine.com](https://doc.photonengine.com/photon/v1/pricing) vía buscador |
| Salas: Unity Relay + Lobby | 0 | 0 | 0 (≤ 50 CCU medios) | [unity.com/pricing](https://unity.com/products/gaming-services/pricing) vía buscador |
| Voz: Vivox (Unity) | 0 | 0 | 0 (≤ 5.000 PCU) | [support.unity.com](https://support.unity.com/hc/en-us/articles/31045802890260) vía buscador |
| Voz: LiveKit self-host | 0 | 5-20 USD VPS (hipótesis) | 20-80 USD VPS + tráfico (hipótesis) | Precios Cloud no verificados |
| Voz: Agora/Daily por minuto | 0 | 120.000 min de participante: 0-120 USD (hipótesis sobre ~1 USD/1.000 min, **no verificado**) | 1,2 M min: ~1.200 USD (misma hipótesis) | No verificado |
| Voz: Discord/WhatsApp externos | 0 | 0 | 0 | — |
| Hosting web/API (Vercel/Cloudflare Pages) | 0 | 0-20 USD | 20 USD | No verificado hoy |
| Motor | 0 (Godot MIT / Unity Personal / web MIT) | 0 | 0 | Verificado (§2) |

Lectura: sin voz integrada, el MVP cuesta **0-40 USD/mes** hasta 10.000 salas. La voz por minutos es la única línea que puede superar los 1.000 USD/mes; la alternativa gratuita real es Vivox (Unity) o LiveKit en un VPS.

---

## 6. Implicaciones para nuestro juego

1. **Diseñad los sensores como momentos, no como control continuo.** Cámara en ventanas de 2-3 s con gestos del catálogo de MediaPipe (número de dedos, pulgar, puño, palma, victoria), móvil quieto; nada de gestos a dos manos ni con movimiento. Y siempre con alternativa táctil para quien no quiera dar permiso de cámara.
2. **"Soplar" solo pegado al móvil y con calibración**; en un bar la mecánica robusta es grito relativo o golpecito/sacudida (acelerómetro, sin micro). En modo remoto con voz, soplar queda descartado por el procesado de audio.
3. **Sala autoritativa ligera** (Colyseus o Durable Objects) desde el prototipo: resuelve de serie los cuatro puntos de "entrar y salir" del brief. Ningún modelo donde un móvil sea host.
4. **Voz fuera del MVP**: remoto con Discord/WhatsApp y métrica de uso; si el remoto crece, LiveKit self-host (Godot/web) o Vivox (Unity).
5. **El clip de TikTok se genera desde el estado**, en vertical, sin grabar pantalla ni cámara: sin diálogos de permiso, sin caras, sin RGPD. Grabar la cámara, solo opt-in y más adelante.
6. **Motor: Godot 4 o web + Capacitor**, a decidir tras el concepto y el estilo visual; antes de decidir, una tarde de medición en un Android de gama media (fps en WebView, MediaPipe en WebView, APK real de Godot con y sin módulos).
7. **Peso objetivo del invitado:** < 20 MB en Android (alcanzable con Godot recortado o con Capacitor); evita cualquier motor que arranque en 50 MB.
8. **Arquitectura que no cierre el futuro:** eventos de ronda en servidor (sirven para replay, analítica y modo por equipos), compras validadas en servidor ("paga el anfitrión" = desbloqueo por sala, no por usuario), anuncios recompensados solo entre partidas.

### No verificado en esta consulta (webs bloqueadas desde el entorno)

Precios de LiveKit Cloud, Agora, Daily, Photon Voice, Heroic Cloud (base), Firebase RTDB, Cloudflare Workers Paid, VideoKit, Meshy, Tripo, Spline, Aseprite; exceso de mensajes/conexiones de Supabase; texto oficial de ReplayKit y de `MediaRecorder.AudioSource`; constraints de audio de getUserMedia (MDN/W3C); `getUserMedia` en WKWebView; Discord Social SDK; Unity Input System; soporte Unity/Godot de Playroom; FPS de Apple Vision; año exacto de las releases de Colyseus 0.18, LiveKit 1.13.7 y MediaPipe 1.0.0 (GitHub lo omite cuando es el año en curso); cifras de peso de APK (solo fuentes de foro).
