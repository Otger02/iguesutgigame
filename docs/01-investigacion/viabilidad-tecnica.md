# Viabilidad técnica

> Fase A · Investigación. Fecha de consulta de todas las fuentes: **2026-10-06**. Precios en USD. Muchas webs oficiales (Google, Unity, Supabase, Photon, LiveKit, Agora, Cloudflare, Firebase, Blender) estaban bloqueadas desde el entorno de investigación: se cita entonces el fragmento obtenido "vía buscador" o el repositorio de GitHub, y lo que no se ha podido leer queda como **no verificado**. Hechos e hipótesis van separados.

## Resumen

1. Todo lo que pide el brief es viable con librerías abiertas de licencia permisiva (MIT/Apache): MediaPipe para manos, sensores nativos para lanzar y sacudir, Colyseus o Cloudflare Durable Objects para salas con entrada y salida en caliente, WebRTC/LiveKit para voz.
2. Lo frágil no es la técnica sino el contexto: la cámara de gestos y el soplido funcionan en demo y se degradan en un bar (luz, ruido, móvil en la mano); hay que diseñarlos como momentos cortos, con calibración y con alternativa (grito, golpecito, sacudida).
3. Usar el micro como mecánica y tener chat de voz a la vez es un conflicto real: los SDK de voz procesan el audio (cancelación de eco, supresión de ruido) y un soplido es justo lo que suprimen. Recomendación: voz solo en modo remoto y, en ese modo, sustituir "soplar" por otra entrada.
4. Motor, recomendación provisional: **Godot 4** (todo texto, MIT, APK ligero, sensores nativos, plugin de MediaPipe) o **web + Capacitor** (vuestra experiencia, APK aún más ligero, pero rendimiento de WebView y cámara en WebView sin verificar). Unity, tercero (solo si es 3D o la voz integrada es central); Unreal, descartado.
5. Coste del MVP: 0-40 USD/mes sin voz; la voz es la única partida que escala mal por minutos (salvo Vivox, gratis hasta 5.000 usuarios concurrentes, pero ligado a Unity). Hathora cerró en mayo de 2026 y Twilio Video cierra en diciembre de 2026: ni los consideréis.

---

## 1. Librerías y repos públicos por capacidad

Licencias: MIT/Apache/BSD/ISC = OK para app comercial; **GPL/AGPL = RIESGO** (obliga a liberar el código del juego o a pagar licencia comercial).

### 1.1 Detección de manos y dedos

| Opción | Enlace | Licencia | Madurez | iOS / Android / motores | Rendimiento gama media | Coste |
|---|---|---|---|---|---|---|
| MediaPipe Tasks (Hand Landmarker, Gesture Recognizer) | [github.com/google-ai-edge/mediapipe](https://github.com/google-ai-edge/mediapipe) | Apache-2.0 | 37,2k estrellas; release v1.0.0 (GitHub no muestra el año); npm `@mediapipe/tasks-vision` 1.0.1 Apache-2.0 ([registry.npmjs.org](https://registry.npmjs.org/@mediapipe/tasks-vision)) | Android (SDK ≥ 24), iOS, web (WASM). Unity: [MediaPipeUnityPlugin](https://github.com/homuler/MediaPipeUnityPlugin) (MIT, 2,5k, MediaPipe 0.10.22, sin WebGL). Godot: [GDMP](https://github.com/j20001970/GDMP) (MIT, 132 estrellas, v0.6 del 16-09-2026, Android/iOS/Linux/Web) | Oficial: Hand Landmarker (full) **17,12 ms CPU / 12,27 ms GPU en Pixel 6** ([doc, vía buscador](https://ai.google.dev/edge/mediapipe/solutions/vision/hand_landmarker)). Hipótesis: en gama media 30-60 ms por frame con cámara, 15-25 FPS; calor y batería notables pasado un minuto | 0 |
| LiteRT (ex TensorFlow Lite) | [github.com/google-ai-edge/LiteRT](https://github.com/google-ai-edge/LiteRT) | Apache-2.0 | 3,5k; renombrado el 04-09-2024 ([blog Google](https://developers.googleblog.com/tensorflow-lite-is-now-litert/)) | Android, iOS, web | Es el runtime que usa MediaPipe; solo si entrenáis un modelo propio | 0 |
| ML Kit (Google) | [github.com/googlesamples/mlkit](https://github.com/googlesamples/mlkit) | Propietario gratuito | Google | Android, iOS nativo | **No tiene API de manos**: el README lista barcode, caras, etiquetado, objetos, texto (+ lenguaje y GenAI). Pose Detection es de cuerpo, no de dedos | 0 |
| Apple Vision `VNDetectHumanHandPoseRequest` | [developer.apple.com](https://developer.apple.com/documentation/vision/vndetecthumanhandposerequest) | Incluida en iOS | iOS 14+ | **Solo iOS**: 21 puntos por mano, `maximumHandCount` (vía buscador) | FPS: no verificado | 0 |
| OpenCV | [github.com/opencv/opencv](https://github.com/opencv/opencv) | Apache-2.0 desde 4.5.0 ([opencv.org](https://opencv.org/license/)) | 91,1k | Android, iOS, web | Sin detector de manos listo; no merece la pena | 0 |
| Ultralytics YOLO | [github.com/ultralytics/ultralytics](https://github.com/ultralytics/ultralytics) | **AGPL-3.0 = RIESGO** | 62,2k | CoreML/TFLite | Pose de cuerpo, no de manos. Descartar | Enterprise: no verificado |
| React Native: VisionCamera + fast-tflite | [VisionCamera](https://github.com/mrousavy/react-native-vision-camera) · [fast-tflite](https://github.com/mrousavy/react-native-fast-tflite) · [react-native-mediapipe](https://github.com/cdiddy77/react-native-mediapipe) | MIT / MIT / MIT | 9,6k (V5) / 1,2k / 80 | iOS, Android | Frame processors con delegados GPU/CoreML/NNAPI; react-native-mediapipe solo objetos | 0 |

**Qué gestos son fiables.** El Gesture Recognizer clasifica 7 gestos + "ninguno": puño cerrado, palma abierta, índice arriba, pulgar abajo, pulgar arriba, victoria y "I love you" ([model card oficial, PDF](https://storage.googleapis.com/mediapipe-assets/gesture_recognizer/model_card_hand_gesture_classification_with_faireness_2022.pdf)). Contar dedos (1-5) se hace con reglas sobre los 21 puntos y es fiable con la mano abierta de frente a 30-60 cm. La model card declara fuera de alcance los gestos a dos manos y con movimiento, y avisa de que **no se ha probado en móviles de gama baja, poca luz ni desenfoque**: las condiciones de un bar. Hipótesis de diseño: cámara en ventanas de 2-3 s ("enseña un número"), móvil quieto, nunca como entrada continua.

### 1.2 Detección de soplido con ruido ambiente

No existe una librería madura y multiplataforma; hay técnicas y repos de demostración.

| Opción | Enlace | Licencia | Madurez | Plataformas | Técnica | Coste |
|---|---|---|---|---|---|---|
| Web Audio API (AnalyserNode) a medida | [whistlerr (npm)](https://www.npmjs.com/package/whistlerr) describe la banda 500-5.000 Hz | Propia | Sois vosotros | Web, Capacitor, Expo | RMS + espectro | 0 |
| blowawish | [registry.npmjs.org/blowawish](https://registry.npmjs.org/blowawish) | ISC | 1.0.10; umbral 0-1, sin espectro | Web | Solo volumen: inútil en un bar | 0 |
| JS-Breathing-Detection | [Breathinglabs](https://github.com/Breathinglabs/JS-Breathing-Detection) | MIT | 29 estrellas, 2 commits | Web | Respiración por micro | 0 |
| UnityMicBlowDetection | [eriseven](https://github.com/eriseven/UnityMicBlowDetection) | MIT | 0 estrellas | Unity | Demo | 0 |
| PandaSuite "Blow sensor" | [docs.pandasuite.com](https://docs.pandasuite.com/essentials/components/blow-sensor/) | Propietario no-code | Comercial | iOS/Android nativo, no web | **Saturación del micro** (móvil pegado a la boca) | No aplicable |
| Receta nativa clásica | [Foro Solar2D](https://forums.solar2d.com/t/detect-microphone-volume-blowing-into-microphone/285743) | — | — | iOS: AVAudioRecorder + paso bajo; Android: PCM + FFT | Soplido = espectro **ancho y plano**; se mide la desviación típica del espectro | 0 |

**Fiabilidad en un bar (hipótesis).** Un umbral absoluto no sirve: el ruido de fondo ya lo supera. Funciona razonablemente combinar: (1) **calibración** de 1-2 s del ambiente al empezar la ronda y detección por delta relativo; (2) **planitud espectral**: el soplido es ruido ancho sin tono, voces y música tienen armónicos; (3) **proximidad**: soplar a 2-3 cm satura el canal de forma inconfundible (lo que usa PandaSuite). "Soplar pegado al móvil" es fiable con ruido; "soplar a 20 cm", no. Alternativas por robustez: golpecitos (acelerómetro, sin micro), sacudir, gritar (volumen relativo calibrado: cada móvil detecta al más cercano), soplar.

**Conflicto con el chat de voz.** En presencial no hay voz: el micro queda libre. En remoto el conflicto es real:

- Hecho conocido, **no verificado hoy** (páginas bloqueadas): en Android la fuente `VOICE_COMMUNICATION` aplica cancelación de eco, ganancia automática y supresión de ruido (`MIC`/`UNPROCESSED` no); en iOS hay una única `AVAudioSession` por app y el modo `.voiceChat` activa el procesado. WebRTC toma el micro así; en web los constraints `noiseSuppression`/`autoGainControl`/`echoCancellation` pueden pedirse a `false`.
- Consecuencia: un soplido es ruido ancho, justo lo que la supresión elimina. Detectarlo sobre el stream de voz es poco fiable, y una segunda captura "cruda" en paralelo no está garantizada (a probar).
- Recomendación: en remoto, la mecánica pasa a **grito/volumen** (sobrevive al procesado) o a sacudida/golpecito, silenciando la voz mientras dura (ducking). Si la voz va por Discord/WhatsApp, nuestra app pedirá el micro con la llamada en segundo plano: en iOS puede interrumpirla (riesgo a probar).

### 1.3 Giroscopio y acelerómetro

| Opción | Enlace | Licencia | Plataformas | Permisos y rendimiento | Coste |
|---|---|---|---|---|---|
| Android `SensorManager` | [developer.android.com](https://developer.android.com/develop/sensors-and-location/sensors/sensors_motion) (verificado) | SO | Android | **Sin permiso**. Desde Android 12 frecuencia limitada (200 Hz exige `HIGH_SAMPLING_RATE_SENSORS`). Útiles: `LINEAR_ACCELERATION`, `ROTATION_VECTOR` | 0 |
| iOS CoreMotion | [developer.apple.com](https://developer.apple.com/documentation/coremotion) | SO | iOS | Sin diálogo de permiso para movimiento (no verificado hoy) | 0 |
| Web `DeviceMotionEvent`/`DeviceOrientationEvent` | [MDN](https://developer.mozilla.org/en-US/docs/Web/API/DeviceOrientationEvent/requestPermission_static) · [yal.cc](https://yal.cc/js-device-motion/) · [Foro Apple](https://developer.apple.com/forums/thread/128376) (vía buscador) | Estándar | Safari iOS 13+, Chrome Android | iOS 13+: `requestPermission()` **solo desde un gesto del usuario y en HTTPS** (`touchstart` no vale). **En WKWebView (Capacitor) no existe `requestPermission`: acceso directo** | 0 |
| Capacitor Motion | [capacitor-plugins/motion](https://github.com/ionic-team/capacitor-plugins/tree/main/motion) | MIT | iOS, Android, web | Envuelve las Web APIs (`accel`, `orientation`) | 0 |
| Expo `expo-sensors` | [expo-sensors](https://github.com/expo/expo/tree/main/packages/expo-sensors) | MIT (Expo) | iOS, Android | Accelerometer, Gyroscope, DeviceMotion, Magnetometer, Barometer, Pedometer | 0 |
| Godot `Input.get_accelerometer/get_gyroscope/get_gravity/get_magnetometer` | [Input.xml](https://github.com/godotengine/godot/blob/master/doc/classes/Input.xml) (verificado) | MIT | **Solo Android e iOS** (cero en web/editor); activar `input_devices/sensors/*` en Android | 0 |
| Unity Input System (`Gyroscope`, `Accelerometer`, `AttitudeSensor`) | docs.unity3d.com | Unity | iOS, Android | **No verificado** (docs bloqueadas) | 0 |
| shake.js / Square Seismic | [shake.js](https://github.com/alexgibson/shake.js) · [seismic](https://github.com/square/seismic) | MIT (no verificado) / Apache-2.0 | Web / Android | **Ambas archivadas** (29-12-2020 y 26-11-2024). Son 100 líneas: escribid la vuestra | 0 |

**Calibración entre móviles (hipótesis).** Unidades estandarizadas (m/s², rad/s), pero varían frecuencia (web ~60 Hz, Android hasta 200 Hz, iOS hasta 100 Hz), ejes y ruido. Para "lanzar": aceleración lineal sin gravedad, pico de módulo sobre un umbral relativo a 1 s de reposo, y mandar al servidor solo el evento (dirección + intensidad 0-1), nunca el stream. Para "mover la vista": `ROTATION_VECTOR`/attitude con suavizado; en web funciona a 60 Hz con la latencia del WebView.

### 1.4 Multijugador por salas con entrada y salida en caliente

**Autoritativo frente a P2P.** Las trampas no importan; sí que nadie sea imprescindible y que una desconexión no rompa la ronda. En P2P (malla WebRTC o "un cliente es host", el modelo de Playroom y del high-level de Godot por defecto) el estado vive en un móvil: si se va, hay que migrar el host, lo más frágil que existe. Con una **sala autoritativa ligera** (Colyseus, Durable Objects, Nakama) el estado vive en el servidor: el que entra lo recibe, el que se va desaparece, el que se reconecta vuelve a su asiento. Para 2-6 jugadores el servidor es trivial y la latencia europea sobra (hipótesis, no medida: 20-60 ms RTT desde España a Frankfurt/París/Londres). Conclusión: **autoritativo pero "tonto"**: replica estado y presencia, valida poco.

Supuestos de coste (hipótesis): sala = ~30 min con 4 jugadores; 1.000 salas/mes ≈ picos de 10-30 CCU; 10.000 salas/mes ≈ 28 CCU medios y picos de 100-300.

| Opción | Enlace | Licencia | Madurez | Clientes | Reconexión y presencia | Coste a 0 / 1.000 / 10.000 salas·mes |
|---|---|---|---|---|---|---|
| **Colyseus** | [github.com/colyseus/colyseus](https://github.com/colyseus/colyseus) | MIT | 7,3k; release 0.18 (25 de agosto, año no mostrado) | JS/TS, React, **Unity, Godot**, GameMaker, Defold, Construct, Haxe, C | "Reconnection support out of the box" (`allowReconnection`) | Self-host: VPS 5-20 (hipótesis). Colyseus Cloud **desde 15 USD/mes**, sin límite de CCU ni ancho de banda ([docs.colyseus.io](https://docs.colyseus.io/cloud/pricing-billing), vía buscador) → 0 / 15 / 15-60 |
| **Nakama** | [github.com/heroiclabs/nakama](https://github.com/heroiclabs/nakama) | Apache-2.0 | 13,5k; v3.41.0 (18-09-2026) | .NET/Unity, JS, Java, Unreal, **Godot**, Defold, Swift | Match handlers (Go/TS/Lua), presencia, parties | Self-host gratis (Go + Postgres). Heroic Cloud por núcleos, sin límite de CCU; **precio base no verificado** ([heroiclabs.com/pricing](https://heroiclabs.com/pricing)). Más pesado de operar para 2 personas |
| **Supabase Realtime** | [github.com/supabase/realtime](https://github.com/supabase/realtime) | Apache-2.0 | 7,7k | JS (y cualquier WebSocket) | Presence y Broadcast; **sin estado de sala en servidor** (Postgres o un cliente); el README avisa: no garantiza la entrega de todos los mensajes | Límites verificados en [limits.mdx](https://github.com/supabase/supabase/blob/master/apps/docs/content/guides/realtime/limits.mdx): Free 200 conexiones, 100 msg/s, 256 KB; Pro 500 conexiones, 500 msg/s. Planes 0 / 25 / 599 USD y 2 M (Free) / 5 M (Pro) mensajes/mes (secundaria: [jetadmin](https://www.jetadmin.io/blog/supabase-pricing-2026-guide-to-plans-limits-and-real-world-costs/)). **Cada mensaje cuenta por destinatario** (verificado): 5 msg/s × 5 destinatarios × 1.800 s ≈ 45.000 por sala → 45 M/mes con 1.000 salas, 9× la cuota Pro. Exceso: no verificado |
| **PartyKit / Cloudflare Durable Objects** | [partykit/partykit](https://github.com/partykit/partykit) · [cloudflare/partyserver](https://github.com/cloudflare/partyserver) | MIT / ISC | 5,7k / 1,3k; PartyKit es de Cloudflare ([blog](https://blog.cloudflare.com/cloudflare-acquires-partykit)), desarrollo en `partyserver` | JS/TS (WebSocket desde cualquier motor) | Un Durable Object por sala = estado en servidor con WebSocket Hibernation | Plan gratis: 100.000 peticiones/día y 313.000 GB-s/día; SQLite de pago desde enero 2026 solo en plan de pago ([changelog](https://developers.cloudflare.com/changelog/2025-12-12-durable-objects-sqlite-storage-billing), vía buscador). Workers Paid 5 USD/mes (no verificado) → 0 / 5 / 5-30 |
| Photon Fusion / PUN | [doc.photonengine.com](https://doc.photonengine.com/photon/v1/pricing) (vía buscador) | Propietaria | Muy maduro (Unity) | Unity; Realtime SDK para otros | Reconexión (PlayerTTL): no verificado | 20 CCU gratis (desarrollo); **100 CCU gratis** para una app comercial Fusion/Quantum; Fusion 500 CCU 125 USD/mes, 1.000 CCU 250. PUN: 100 CCU 95 USD/12 meses → 0 / 0 / 0-125 |
| Unity NGO + Relay + Lobby | [NGO](https://github.com/Unity-Technologies/com.unity.netcode.gameobjects) · [unity.com/pricing](https://unity.com/products/gaming-services/pricing) (vía buscador) | NGO **MIT** (verificado) | 2,3k | Unity | Host-cliente por defecto, sin migración de host | Relay: **50 CCU medios/mes gratis**, luego 0,16 USD/CCU; Lobby 10 GiB/mes gratis, 0,09 USD/GiB → 0 / 0 / 0 |
| Godot high-level + servidor propio | [godot-docs](https://github.com/godotengine/godot-docs/blob/master/tutorials/networking/high_level_multiplayer.rst) | MIT | 4.7 | Godot | Peers ENet/WebSocket/WebRTC; autoridad por nodo; servidor headless | VPS 5-20 (hipótesis). Reconexión a mano |
| Socket.IO | [github.com/socketio/socket.io](https://github.com/socketio/socket.io) | MIT | 63,2k | JS | Sin salas con estado | VPS. Reinventar Colyseus: no |
| Liveblocks | [liveblocks.io/pricing](https://liveblocks.io/pricing.md) (vía buscador) | Propietaria | Colaboración, no juegos | JS | Presence, CRDT | Free 500 salas activas/mes; Pro 30 USD + 0,03/sala → 0 / 30-45 / 300+. **Cobra por sala: no** |
| Firebase Realtime Database | firebase.google.com/pricing | Propietaria | Maduro | iOS, Android, web, Unity | `onDisconnect` | **No verificado** (bloqueada). Coste por GB y modelo poco adecuados a rondas rápidas |
| Hathora | — | — | **Cerrado el 05-05-2026** tras la compra por Fireworks AI ([crux](https://crux.supercraft.host/blog/hathora-shut-down-where-to-go-after-may-2026/), [TechSpot](https://www.techspot.com/news/111969-stormgate-servers-go-dark-following-ai-focused-hosting.html), vía buscador) | — | — | Descartado |
| **Playroom Kit** | [npm playroomkit](https://registry.npmjs.org/playroomkit) · [joinplayroom.com](https://joinplayroom.com) | SDK ISC; servicio propietario | 0.0.97 (sigue en 0.0.x); React 17-18; SDK Discord Embedded opcional | JS/React (Unity y Godot: no verificado) | Lobby, matchmaking, estado global y por jugador, RPC; modo "stream" o "joined" | Freemium **desde 10 USD/mes** (secundaria, web bloqueada). Ideal para **prototipo en días**; para producto, dependencia de un servicio pequeño en 0.0.x |
| **Rune** (fue Dusk en 2024-2025) | [github.com/rune/rune](https://github.com/rune/rune) · [npm rune-sdk](https://registry.npmjs.org/rune-sdk) | SDK MIT | 425 estrellas; `rune-sdk` 6.0.8 (`dusk-games-sdk` quedó en 4.21.18); 8 M USD de inversión ([techleap](https://finder.techleap.nl/news/feed/dusk-raises-8m-for-game-platform)) | JS/TS, React, Svelte, Three.js, PixiJS, Phaser | Predict-rollback, voz y chat incluidos; **los juegos solo corren dentro de la app Rune** (10 M instalaciones) | Gratis; sin anuncios ni cobros: un "creator fund" paga por retención y horas (mínimo 100 h/mes y 5 % de retorno) ([making-money.md](https://github.com/rune/rune/blob/staging/docs/docs/publishing/making-money.md)). **Incompatible con "app propia en las tiendas"**: solo como laboratorio |

### 1.5 Chat de voz para el modo remoto

| Opción | Enlace | Licencia | Plataformas | Precio | Notas |
|---|---|---|---|---|---|
| WebRTC puro (malla P2P) | Estándar | BSD (libwebrtc) | WebView, Godot `WebRTCPeerConnection`, Unity (paquetes) | 0 + TURN (`coturn` en VPS, 5 USD, hipótesis) | Con 2-6 funciona; sin moderación. Toma el micro con procesado de voz |
| **LiveKit** | [github.com/livekit/livekit](https://github.com/livekit/livekit) | Apache-2.0 | iOS, Android, Unity, Flutter, RN, JS; **no Godot** | Self-host: binario/Docker. Cloud: **precios no verificados** | 21,3k; v1.13.7 (14 de septiembre, año no mostrado). SFU con moderación server-side |
| Agora | agora.io/pricing | Propietaria | iOS, Android, Unity, web, Flutter, RN | **No verificado** (de memoria: 10.000 min gratis/mes; audio ~0,99 USD/1.000 min) | Por minuto |
| Vivox (Unity) | [support.unity.com](https://support.unity.com/hc/en-us/articles/31045802890260) (vía buscador) | Propietaria | Unity (nativo/Unreal: no verificado) | **Gratis hasta 5.000 usuarios concurrentes pico**; después 2.000 USD por cada 5.000 PCU | Por concurrencia, no por minutos: para un indie es voz gratis. Gran argumento pro-Unity si la voz es central |
| Photon Voice | photonengine.com | Propietaria | Unity | **No verificado** | Atado a Photon |
| Daily | daily.co/pricing | Propietaria | Web, iOS, Android, RN, Flutter | **No verificado** | Por minuto |
| Twilio Video | [mirrorfly](https://www.mirrorfly.com/blog/twilio-programmable-video-shut-down/) (vía buscador) | — | — | — | **Fin de vida 05-12-2026**, sin nuevos clientes. Descartado |
| Discord / WhatsApp externos | — | — | Todo | 0 | "Abrid una llamada y jugad". Sin moderación propia y el micro lo tiene la otra app (§1.2). Discord Social SDK (voz integrada gratuita): **no verificado** |

**Moderación.** Voz con desconocidos obliga a reporte, bloqueo y política (doc de publicación). Entre amigos (salas por código, sin matchmaking público) el riesgo es bajo. MVP: **sin voz integrada**; el remoto empieza con "usad Discord/WhatsApp" y se mide cuánta gente juega en remoto antes de pagar la integración.

### 1.6 Clip automático de los últimos segundos

| Opción | Enlace | Plataformas | Permisos y privacidad | Coste |
|---|---|---|---|---|
| ReplayKit (`RPScreenRecorder.startCapture`) | [developer.apple.com](https://developer.apple.com/documentation/replaykit) | iOS 11+ | Página no legible hoy (**no verificado**). Conocido: consentimiento del sistema por sesión; graba solo la propia app; entrega sample buffers (búfer circular posible) | 0 |
| MediaProjection | [developer.android.com](https://developer.android.com/media/grow/media-projection) (verificado) | Android 5+ | **Consentimiento antes de cada sesión**; Android 14+: foreground service `mediaProjection` y opción de compartir solo la app; Android 15 QPR1+: chip permanente en la barra de estado. Para un clip "automático" es fricción y sospecha | 0 |
| VideoKit (sucesor de NatCorder) | [github.com/videokit-ai/videokit](https://github.com/videokit-ai/videokit) | Unity: Android 24+, iOS 14+, WebGL (Unity 6) | Repo Apache-2.0 pero exige clave de videokit.ai; graba pantalla, cámara y micro, exporta MP4/GIF | **No verificado** |
| Unity Recorder | docs.unity3d.com | Solo Editor (no verificado hoy) | — | Descartado |
| Grabar la cámara frontal | APIs de cámara | Todas | Permiso + sale la cara: consentimiento explícito, RGPD, menores. Potente para TikTok, delicado | 0 |
| **Replay desde el estado del juego** | Propio | Todas | **Sin grabar nada**: el servidor tiene los eventos de la ronda; el cliente los re-renderiza en vertical con la "pantalla de culpable" y exporta vídeo (viewport a vídeo en Godot/Unity; `MediaRecorder` sobre canvas en web). Sin permisos, sin caras | 0 |

Recomendación: el clip del MVP se genera **desde el estado**. Grabar cámara, solo opt-in y después.

---

## 2. Primera comparativa de motores

| Criterio | Unity 6 | Godot 4.7 | Unreal 5 | Web + Capacitor (Next.js/Svelte + PixiJS/Phaser/Three) | Expo / RN | Flutter + Flame |
|---|---|---|---|---|---|---|
| Trabajo con Claude Code | Escenas YAML y C# son texto, pero **el Editor es imprescindible**. MCP oficial en beta desde el 11-05-2026, solo Unity 6 y con suscripción Unity AI ([gamedev.net](https://gamedev.net/news/4376-unity-ai-open-beta-how-to-get-started-with-mcp/)); comunitario [unity-mcp](https://github.com/CoplayDev/unity-mcp) (MIT, 14,7k, v10.0.0 del 30-06-2026) | **Todo texto**: `.tscn`, `.tres`, GDScript. [godot-mcp](https://github.com/Coding-Solo/godot-mcp) (MIT, 6,0k) lanza, ejecuta y lee la consola; el agente no ve el juego en ejecución ([summerengine](https://www.summerengine.com/blog/claude-for-godot)) | **Blueprints binarios**: opaco; C++ compila lento | Todo texto, donde Claude Code rinde mejor y donde ya trabajáis | Todo texto | Dart, texto |
| Peso app vacía | Foros: APK vacío ~10-20 MB; un 2D real citado: 87-96 MB ([discussions.unity.com](https://discussions.unity.com/t/android-the-package-size-increased-by-10-when-using-unity-6/1539185)) | Foro: **~19 MB**, ~13 MB recortando módulos ([forum.godotengine.org](https://forum.godotengine.org/t/absurd-file-size-increase-when-my-project-is-exported-to-apk/130000)) | Decenas de MB (no verificado) | Foro: Android **~3 MB**; en iOS el bundle de build es grande y la tienda lo optimiza ([forum.ionicframework.com](https://forum.ionicframework.com/t/capacitor-app-size-compared-to-cordova/213063)) | No verificado | No verificado |
| Rendimiento gama media | Excelente | Muy bueno en 2D | Excesivo | **Riesgo**: 60 fps en WebView según dispositivo; PixiJS/Phaser WebGL van bien en Chrome Android moderno (hipótesis) | Bueno en UI; "juice" a mano | Bueno |
| Crossplay, sensores, cámara, MediaPipe | Nativo; MediaPipeUnityPlugin (MIT) | Sensores solo Android/iOS (verificado); `CameraServer` en Android/iOS/Linux/macOS, **no web** (verificado); MediaPipe vía GDMP | Nativo | Sensores por Web API (sin permiso en WKWebView); cámara por `getUserMedia` (iOS 14.3+, no verificado); MediaPipe WASM: **rendimiento en WebView no verificado** | VisionCamera + fast-tflite | Plugins comunidad |
| Multijugador / voz / compras / anuncios | NGO (MIT), Relay/Lobby, Colyseus, Nakama, Photon. **Vivox gratis ≤ 5.000 PCU**. Unity IAP, RevenueCat, AdMob | Colyseus y Nakama con SDK Godot. Voz: sin SDK LiveKit/Agora (WebRTC a mano). IAP: [godot-google-play-billing](https://github.com/godotengine/godot-google-play-billing) (MIT, Godot 4.2+), [godot-ios-plugins](https://github.com/godotengine/godot-ios-plugins) (MIT, InAppStore). Ads: [poingstudios AdMob](https://github.com/poingstudios/godot-admob-plugin) (MIT, 631, Godot 4.5+, rewarded) | Todo, sobredimensionado | Colyseus/PartyKit en JS; LiveKit JS; [purchases-capacitor](https://github.com/RevenueCat/purchases-capacitor) (MIT); [capacitor-community/admob](https://github.com/capacitor-community/admob) (MIT, v8.2.0, rewarded) | react-native-purchases, react-native-google-mobile-ads (no verificados hoy) | Pequeño |
| Curva para vuestro perfil | Media-alta: C#, Editor, assets | **Media**: GDScript ≈ Python; nodos y señales en días | Alta | **Baja**: es lo que hacéis | Baja-media | Media |
| Licencia y coste | Personal gratis hasta 200.000 USD de ingresos/financiación; Pro 2.310 USD/año/asiento desde el 12-01-2026; Runtime Fee cancelada en septiembre de 2024 ([unity.com](https://unity.com/pricing-updates), vía buscador) | **MIT**, 0; 4.7.2 estable del 18-08-2026 ([releases](https://github.com/godotengine/godot/releases)) | 5 % sobre ingresos brutos acumulados por encima de 1 M USD; 3,5 % si se lanza en Epic Games Store desde 2025 ([unrealengine.com/faq](https://www.unrealengine.com/en-US/faq), vía buscador) | MIT: Capacitor 8.5.2 (11-09-2026), Phaser 4.2.1, PixiJS 8, three.js | MIT (Expo SDK 57) | BSD-3 (no verificado) / Flame MIT |
| Riesgos propios | Editor obligatorio, builds pesadas, licencia cambiante | Plugins nativos mantenidos por pocos (GDMP: 132 estrellas) | Peso, equipo de 2 | 60 fps y cámara+ML en WebView; grabación exige plugin nativo; PWA en iOS muy limitada | Capa RN sin motor | Comunidad pequeña |

**Recomendación provisional (ordenada).**

1. **Godot 4** si el concepto es físico y con "juice" (lanzar, globos, partículas, pantalla de culpable animada), 2D o 2.5D. Texto para Claude Code, MIT, 13-19 MB, sensores y cámara nativos, GDMP, SDKs de Colyseus y Nakama, IAP y AdMob con plugins MIT. Pierde en voz (sin SDK de LiveKit/Agora) y en tamaño de ecosistema móvil.
2. **Web + Capacitor** si el concepto es de interfaz (palabras, cartas, temporizadores, símbolos) con animación moderada. Vuestra experiencia, el APK más ligero y continuidad desde el prototipo. Antes de elegirla: medir en un Android de gama media real 60 fps sostenidos en WebView y MediaPipe web en WebView.
3. Unity solo si es 3D o la voz integrada es central (Vivox). Unreal, Flutter/Flame y Expo: no para este equipo y este juego.

La decisión final depende del concepto y del estilo visual (2D/2.5D/3D) de las Fases B y C.

| Si el concepto necesita… | Motor más adecuado |
|---|---|
| Físicas, partículas, "lanzar" con giroscopio y reacciones en pantalla | Godot 4 |
| Cámara con gestos como mecánica frecuente | Godot (GDMP) o Unity; en web solo si la medición en WebView es buena |
| Interfaz, texto, cartas, temporizadores, símbolos | Web + Capacitor |
| 3D o 2.5D con modelos | Godot 4 (ligero) o Unity |
| Voz integrada desde el día uno | Unity + Vivox, o web/Godot + LiveKit self-host |
| Prototipo en una semana | PWA web, sin motor |
| Clip automático sin permisos | Cualquiera, desde el estado; en web con `MediaRecorder` sobre canvas |

---

## 3. Blender: solo para assets

Blender (GPL, gratis; última etiqueta **v5.2.2** del 14-09-2026 según [tags del espejo en GitHub](https://github.com/blender/blender/tags)) no es un motor. Aporta: en **2D**, Grease Pencil para animar una mascota con cámara y luz reales; en **2.5D**, render de sprites desde modelos low-poly (cámara ortográfica, 8 direcciones) para usarlos como atlas en Godot o PixiJS; en **3D**, modelado, rig y exportación glTF a Godot/Unity/three.js. Su coste es tiempo de aprendizaje: para dos personas sin artista rinde más como "exportador" de lo que generan otras herramientas que como herramienta principal.

Alternativas más rápidas (precios **no verificados**, webs bloqueadas; modelos de precio de memoria):

| Necesidad | Herramienta | Nota |
|---|---|---|
| Píxel-art y sprites | Aseprite (pago único), Krita (GPL, gratis) | La GPL de la herramienta no afecta a los assets |
| UI y pantallas | Figma (plan gratuito) | SVG directo a Godot/web |
| 2.5D/3D rápido para web | Spline (plan gratuito; exporta web y glTF) | Encaja con three.js |
| Sprites con IA | Midjourney, Scenario, Layer.ai, modelos locales | Revisar licencia comercial y política de las tiendas; el problema real es la coherencia de estilo |
| Modelos 3D con IA | Meshy, Tripo (créditos; plan gratuito limitado) | Topología sucia: limpiar en Blender |

---

## 4. Arquitectura mínima para el prototipo (no para el producto)

Objetivo: validar la diversión en 1-2 semanas con gente que nunca haya jugado, con lo que ya sabéis hacer.

- **Cliente:** PWA con Next.js (o Vite + React/Svelte), `<canvas>` con PixiJS si hace falta animación, vertical, unión por código de 4 letras o QR. Sin tienda ni instalación.
- **Salas:** (a) **Supabase Realtime** (Broadcast + Presence) con el estado en una tabla y un cliente "director" por orden de llegada (aceptable en prototipo, no en producto); o (b) **PartyKit/partyserver** o **Playroom Kit** con estado en servidor: diez líneas más y entrada/salida en caliente real. Recomendación: (b) con partyserver, porque se reaprovecha.
- **Sensores:** `DeviceMotionEvent` con botón "activar movimiento" (gesto e HTTPS obligatorios en iOS). Valida lanzar y sacudir.
- **Cámara:** `@mediapipe/tasks-vision` en Safari y Chrome; vale para probar si "enseñar un número" tiene gracia, aunque el rendimiento no sea el final.
- **Micro:** Web Audio API con calibración de 2 s; suficiente para probar grito/soplido en un bar real.

Lo que **no** se valida con esta pila: fricción real de descarga e instalación, rendimiento final de cámara y animación en WebView empaquetado, voz integrada, clip con `MediaRecorder` en iOS (parcial), permisos de tienda, compras y anuncios, comportamiento al bloquear pantalla o cambiar de app a mitad de ronda.

---

## 5. Costes mensuales estimados en el MVP

Mismos supuestos que §1.4. Cuentas de desarrollador: en el doc de publicación.

| Partida | 0 salas | 1.000 salas/mes | 10.000 salas/mes | Fuente |
|---|---|---|---|---|
| Salas: Colyseus Cloud | 0 (local) | 15 USD | 15-60 USD (hipótesis) | [docs.colyseus.io](https://docs.colyseus.io/cloud/pricing-billing), vía buscador |
| Salas: Cloudflare Durable Objects | 0 | 0-5 USD | 5-30 USD (hipótesis) | [changelog Cloudflare](https://developers.cloudflare.com/changelog/2025-12-12-durable-objects-sqlite-storage-billing), vía buscador |
| Salas: Supabase Realtime | 0 | 25 USD + exceso (45 M mensajes frente a 5 M incluidos; precio no verificado) | Inviable por mensajes salvo ≤ 1 msg/s | [limits.mdx](https://github.com/supabase/supabase/blob/master/apps/docs/content/guides/realtime/limits.mdx); [jetadmin](https://www.jetadmin.io/blog/supabase-pricing-2026-guide-to-plans-limits-and-real-world-costs/) |
| Salas: Photon Fusion (Unity) | 0 | 0 | 0-125 USD | [doc.photonengine.com](https://doc.photonengine.com/photon/v1/pricing), vía buscador |
| Salas: Unity Relay + Lobby | 0 | 0 | 0 | [unity.com/pricing](https://unity.com/products/gaming-services/pricing), vía buscador |
| Voz: Vivox (Unity) | 0 | 0 | 0 (≤ 5.000 PCU) | [support.unity.com](https://support.unity.com/hc/en-us/articles/31045802890260), vía buscador |
| Voz: LiveKit self-host | 0 | 5-20 USD VPS (hipótesis) | 20-80 USD VPS + tráfico (hipótesis) | Cloud no verificado |
| Voz: Agora/Daily por minuto | 0 | 120.000 min: 0-120 USD (hipótesis ~1 USD/1.000 min, **no verificado**) | 1,2 M min: ~1.200 USD (misma hipótesis) | No verificado |
| Voz: Discord/WhatsApp externos | 0 | 0 | 0 | — |
| Hosting web/API (Vercel, Cloudflare Pages) | 0 | 0-20 USD | 20 USD | No verificado hoy |
| Motor | 0 | 0 | 0 | §2 |

Lectura: sin voz integrada, el MVP cuesta **0-40 USD/mes** hasta 10.000 salas. La voz por minutos es la única línea que puede pasar de 1.000 USD/mes; la gratuita real es Vivox (Unity) o LiveKit en un VPS.

---

## 6. Implicaciones para nuestro juego

1. **Sensores como momentos, no como control continuo.** Cámara en ventanas de 2-3 s con el catálogo de MediaPipe (dedos, pulgar, puño, palma, victoria), móvil quieto; nada a dos manos ni con movimiento. Siempre con alternativa táctil para quien no dé permiso de cámara.
2. **"Soplar" solo pegado al móvil y con calibración**; en bar, la mecánica robusta es grito relativo o golpecito/sacudida (sin micro). En remoto con voz, soplar queda descartado.
3. **Sala autoritativa ligera** (Colyseus o Durable Objects) desde el prototipo: resuelve de serie los cuatro puntos de "entrar y salir". Ningún modelo donde un móvil sea host.
4. **Voz fuera del MVP**: remoto con Discord/WhatsApp y métrica de uso; si crece, LiveKit self-host (Godot/web) o Vivox (Unity).
5. **El clip se genera desde el estado**, en vertical, sin grabar pantalla ni cámara: sin diálogos de permiso, sin caras, sin RGPD. Cámara, solo opt-in y más adelante.
6. **Motor: Godot 4 o web + Capacitor**, tras concepto y estilo visual; antes, una tarde de medición en un Android de gama media (fps en WebView, MediaPipe en WebView, APK real de Godot con y sin módulos).
7. **Peso objetivo del invitado:** < 20 MB en Android (Godot recortado o Capacitor); nada que arranque en 50 MB.
8. **Arquitectura que no cierre el futuro:** eventos de ronda en servidor (replay, analítica, equipos), compras validadas en servidor ("paga el anfitrión" = desbloqueo por sala), anuncios recompensados solo entre partidas.

### No verificado en esta consulta (webs bloqueadas)

Precios de LiveKit Cloud, Agora, Daily, Photon Voice, Heroic Cloud (base), Firebase RTDB, Cloudflare Workers Paid, VideoKit, Meshy, Tripo, Spline, Aseprite; exceso de mensajes y conexiones de Supabase; texto oficial de ReplayKit, `MediaRecorder.AudioSource` y constraints de audio de getUserMedia; `getUserMedia` en WKWebView; Discord Social SDK; Unity Input System; soporte Unity/Godot de Playroom; FPS de Apple Vision; año de las releases de Colyseus 0.18, LiveKit 1.13.7 y MediaPipe 1.0.0 (GitHub lo omite en el año en curso); cifras de peso de APK (solo foros).
