# 🎮 Remix CryptoParty 3D - Finanzas & Web3

> **Videojuego educativo 3D de tablero interactivo estilo Mario Party sobre finanzas descentralizadas y Web3, con economía dual, 10 minijuegos arcade de fin de ronda, personajes icónicos y gráficos procedurales de última generación.**

---

## 📋 Tabla de Contenidos
1. [Visión General & Propósito Didáctico](#-visión-general--propósito-didáctico)
2. [Pila Tecnológica & Arquitectura](#-pila-tecnológica--arquitectura)
3. [Mecánicas del Juego](#-mecánicas-del-juego)
   - [Economía Dual: GWEI vs. Bloques de Consenso](#economía-dual-gwei-vs-bloques-de-consenso)
   - [Estructura de la Partida & Rondas](#estructura-de-la-partida--rondas)
   - [Personajes & Jugabilidad](#personajes--jugabilidad)
4. [El Tablero 3D & Distritos Temáticos](#-el-tablero-3d--distritos-temáticos)
5. [Catálogo de los 10 Minijuegos de Fin de Ronda](#-catálogo-de-los-10-minijuegos-de-fin-de-ronda)
6. [Efectos Visuales, Shaders GLSL & Audio 3D](#-efectos-visuales-shaders-glsl--audio-3d)
7. [Sistema de Billetera Sandbox & Seguridad Web3](#-sistema-de-billetera-sandbox--seguridad-web3)
8. [Oráculo de Mercado Bitcoin & Sentimiento Web3](#-oráculo-de-mercado-bitcoin--sentimiento-web3)
9. [Glosario y Aprendizaje Integrado](#-glosario-y-aprendizaje-integrado)
10. [Instalación, Desarrollo & Despliegue](#-instalación-desarrollo--despliegue)
11. [Atajos de Teclado & Controles](#-atajos-de-teclado--controles)

---

## 🔮 Oráculo de Mercado Bitcoin & Sentimiento Web3

El juego cuenta con un **Oráculo de Mercado Descentralizado** en tiempo real que conecta la economía del juego con el pulso financiero real del mundo cripto:

- **Feeds en Vivo**:
  - **Precio Spot BTC/USD**: Conexión directa a Binance API (`api.binance.com`) con fallback automático a CoinGecko.
  - **Índice Fear & Greed**: Consulta periódica a Alternative.me (`api.alternative.me/fng`) para clasificar el sentimiento en vivo (Codicia Extrema, Codicia, Neutral, Miedo o Pánico Extremo).
- **Régimen de Mercado Dinámico**:
  - **Euforia / Bullrun** (Codicia > 70 o BTC 24h > +6%): Airdrops y Staking rinden **+50%**, pero el Gas sube un **+40%** por congestión. Bloques a 110 GWEI.
  - **Neutral / Consolidación**: Costes y rendimientos estándar base.
  - **Corrección / FUD**: Gas con **25% de descuento** y bloques con rebaja a 90 GWEI.
  - **Cisne Negro / Pánico Extremo**: Oferta histórica **"Buy the Dip"**: Bloques de consenso con **25% de descuento (75 GWEI)** y gas fee reducido en un **40%**.
- **Simulador Didáctico de Escenarios**:
  - Permite a estudiantes, jugadores y profesores cambiar instantáneamente las condiciones macroeconómicas (Bullrun, Neutral, FUD, Pánico) para observar cómo reaccionan las mecánicas del juego y la cuadrícula cuántica 3D, o pulsar para volver a los datos en vivo.
- **Predicción en Casilla 8 (Chainlink)**:
  - Al caer en la casilla del oráculo, los participantes predicen la tendencia del feed live con probabilidades y bonificaciones de volatilidad ajustadas al régimen actual.

---

---

## 🌟 Visión General & Propósito Didáctico

**Remix CryptoParty 3D** transforma conceptos abstractos y complejos del ecosistema de las finanzas descentralizadas (**DeFi**), la tecnología **Blockchain** y la seguridad digital en una experiencia interactiva, dinámica y entretenida.

A través de partidas de tablero por turnos, 4 jugadores compiten por convertirse en el **Maestro Web3** adquiriendo y validando **Bloques de Consenso (Estrellas)** mientras gestionan su reserva de **GWEI (gas / liquidez)**, participan en votaciones de gobernanza DAO, responden trivias de ciberseguridad, esquivan rug pulls y compiten en minijuegos arcade.

---

## 🛠️ Pila Tecnológica & Arquitectura

El proyecto está diseñado con estándares de alto rendimiento y renderizado en tiempo real sin dependencias pesadas innecesarias:

- **Motor 3D**: [Three.js](https://threejs.org/) (r128) con soporte para iluminación PBR (`MeshStandardMaterial`), sombras dinámicas (`PCFSoftShadowMap`), niebla volumétrica y mapeo de tonos ACES Filmic.
- **Shaders GLSL Personalizados**: Shaders de fragmentos y vértices en WebGL con derivadas estándar anti-aliasing (`fwidth`) para renderizar la cuadrícula cuántica reactiva del suelo.
- **Motor de Interpolación**: [TWEEN.js](https://github.com/tweenjs/tween.js) para transiciones fluidas de cámara orbital, movimiento suave de peones por el tablero y animaciones de HUD.
- **Motor de Audio Sintetizado**: [Web Audio API nativa](https://developer.mozilla.org/es/docs/Web/API/Web_Audio_API) mediante osciladores procedurales (senoidales, triangulares y diente de sierra) y envolventes de ganancia sin requerir ficheros de audio externos.
- **Efectos de Partículas**: [Canvas-Confetti](https://www.npmjs.com/package/canvas-confetti) orquestado con cañones direccionales, fuegos artificiales celestes y estrellas doradas.
- **Frontend & Estilos**: [Tailwind CSS](https://tailwindcss.com/) v4 integrado con fuentes tipográficas Google Fonts (*Inter* y *Outfit*), paleta de colores Cyberpunk Neón y efectos de cristal (*Glassmorphism*).
- **Bundler & Tooling**: [Vite](https://vitejs.dev/) + [TypeScript](https://www.typescriptlang.org/) para tipado estricto y recarga ultrarrápida.

---

## 🎲 Mecánicas del Juego

### Economía Dual: GWEI vs. Bloques de Consenso

El juego replica la dinámica de valor de las redes descentralizadas:

1. **GWEI (Moneda de Gas / Liquidez)**:
   - Se utiliza para pagar tarifas de transacción, apostar en minijuegos, comprar ítems en la tienda y pagar el coste de forjado de nuevos bloques.
   - Si un jugador se queda sin GWEI, no queda eliminado, pero sufre penalizaciones de gas y no puede forjar bloques hasta restablecer su liquidez.

2. **Bloques Validados (⭐ Estrellas de Consenso)**:
   - Representan la victoria final. Cada bloque cuesta **100 GWEI** al caer en casillas de consenso (casillas 12 y 18) o ganar minijuegos en rondas clave.
   - El ganador absoluto es el jugador con más Bloques de Consenso al terminar la **Ronda 10**. En caso de empate en bloques, se desempata por reserva acumulada de GWEI.

### Estructura de la Partida & Rondas

- La partida consta de **10 Rondas completas**.
- Cada ronda se compone del turno secuencial de los 4 jugadores (Tirada de dados, desplazamiento 3D, activación de evento de casilla).
- Al finalizar el turno del último jugador en cada ronda, se ejecuta automáticamente uno de los **10 Minijuegos de Fin de Ronda**.
- Tras el minijuego, se reparten las recompensas de GWEI y Bloques, la ronda se incrementa y el suelo de la arena muta de fase lumínica.

### Personajes & Jugabilidad

Cuatro avatares icónicos con personalidad e inteligencia artificial propia:

| Personaje | Rol | Color Neón | Rasgo Característico |
|---|---|---|---|
| **Doge** 🐕 | Humano (Jugador Principal) | Oro Neón (`#f59e0b`) | Espíritu comunitario y degen legendario. |
| **Vitalik Bot** 🦄 | IA | Cyan Neón (`#00f0ff`) | Enfoque algorítmico en contratos inteligentes y escalabilidad. |
| **Satoshi AI** ⚡ | IA | Verde Neón (`#10b981`) | Máxima seguridad, ahorro de gas y precisión matemática. |
| **Pepe Degen** 🐸 | IA | Púrpura Neón (`#a855f7`) | Alto apetito por el riesgo y jugadas impredecibles en swaps. |

---

## 🗺️ El Tablero 3D & Distritos Temáticos

El tablero circular consta de **24 casillas interconectadas** mediante puentes de datos por los que circulan paquetes de luz cuántica, divididas en 6 distritos especializados:

1. **Génesis Hub (Casillas 0 - 3)**:
   - *Casilla 0*: **Bloque Génesis** (otorga +20 GWEI por vuelta completa).
   - *Casilla 1*: **Staking Pool** (+15 GWEI de rendimiento pasivo).
   - *Casilla 2*: **Tarifa de Gas L1** (-10 GWEI por congestión de red).
   - *Casilla 3*: **Airdrop de Tokens** (+25 GWEI por recompensa comunitaria).

2. **Distrito DeFi & Exchanges (Casillas 4 - 7)**:
   - *Casilla 4*: **Uniswap AMM Swap** (intercambio descentralizado con deslizamiento).
   - *Casilla 5*: **Quiz de Ciberseguridad** (trivia interactiva con premio de +30 GWEI o penalización de -15 GWEI).
   - *Casilla 6*: **Gas Surge** (-20 GWEI por pico de demanda).
   - *Casilla 7*: **Warp Speed L2 Rollup** (teletransporte cuántico de +3 casillas).

3. **Distrito de Oráculos & Degen (Casillas 8 - 11)**:
   - *Casilla 8*: **Oráculo Chainlink** (predicción de feeds de precios off-chain).
   - *Casilla 9*: **Recompensa de Staking** (+20 GWEI).
   - *Casilla 10*: **Ruleta Web3 Degen** (apuesta de alto riesgo: moonshot 2x o liquidación).
   - *Casilla 11*: **Tarifa de Red** (-12 GWEI).

4. **Distrito de Consenso & Gobernanza (Casillas 12 - 15)**:
   - *Casilla 12*: **Validador de Bloque (⭐)** (compra de Bloque de Consenso por 100 GWEI).
   - *Casilla 13*: **Fondo de Tesorería** (+18 GWEI).
   - *Casilla 14*: **Quiz de Ciberseguridad II** (preguntas avanzadas sobre llaves privadas y contratos).
   - *Casilla 15*: **Gas Congestion L1** (-25 GWEI).

5. **Distrito de Seguridad & Alertas (Casillas 16 - 19)**:
   - *Casilla 16*: **Cosecha DeFi Yield** (+35 GWEI).
   - *Casilla 17*: **Trampa Rug Pull** (alerta de estafa: pérdida de -30 GWEI si no se posee Escudo de Gas).
   - *Casilla 18*: **Nodo Validador PoS (⭐)** (segundo punto de forjado de Bloques).
   - *Casilla 19*: **Gobernanza DAO** (propuesta de votación con impacto para todos los jugadores).

6. **Distrito de Alta Frecuencia & Bóveda (Casillas 20 - 23)**:
   - *Casilla 20*: **Micro-Tarifa L2** (-5 GWEI).
   - *Casilla 21*: **Puente Wormhole Cross-Chain** (salto dimensional al extremo opuesto del tablero).
   - *Casilla 22*: **Fondo de Liquidez LP** (+22 GWEI).
   - *Casilla 23*: **Bóveda Secreta de Satoshi** (minijuego de descifrado con premio de +60 GWEI).

---

## 🕹️ Catálogo de los 10 Minijuegos de Fin de Ronda

Al finalizar cada una de las 10 rondas, el motor `MiniGamesEngine` activa un minijuego interactivo:

1. **Ronda 1: Atrapa el Airdrop 🪂**
   - *Mecánica*: Mueve la canasta recolectora con el ratón o flechas para atrapar tokens dorados que caen del cielo evitando los virus y códigos maliciosos.
2. **Ronda 2: Esquiva los Rug Pulls ⚠️**
   - *Mecánica*: Controla a tu personaje esquivando proyectos sospechosos y trampas que caen a gran velocidad.
3. **Ronda 3: Clicker Minero Proof-of-Work ⛏️**
   - *Mecánica*: Genera hashes lo más rápido posible pulsando repetidamente para resolver el bloque criptográfico antes de que expire el tiempo.
4. **Ronda 4: Swap Veloz AMM 🔄**
   - *Mecánica*: Conecta pares de liquidez correctos bajo presión de tiempo para obtener el mejor enrutamiento y tasa de cambio.
5. **Ronda 5: Defensa Anti-Phishing 🛡️**
   - *Mecánica*: Distingue entre URLs legítimas y enlaces maliciosos de phishing para blindar tu nodo.
6. **Ronda 6: Subasta Gas Rush ⛽**
   - *Mecánica*: Puja la cantidad justa de gas en tiempo real para entrar en el siguiente bloque prioritario sin pagar de más.
7. **Ronda 7: Memoria de Frase Semilla 🧠**
   - *Mecánica*: Memoriza y reproduce la secuencia de palabras de recuperación en el orden exacto.
8. **Ronda 8: Puente Cross-Chain (QTE) 🌉**
   - *Mecánica*: Evento de tiempo rápido (Quick Time Event) pulsando las teclas indicadas en el momento exacto para validar transacciones multi-cadena.
9. **Ronda 9: Detector de Liquidez DeFi 📊**
   - *Mecánica*: Identifica piscinas con impermanent loss controlado y mayor APR antes de que cambien los oráculos.
10. **Ronda 10: Gobernanza DAO Relámpago ⚖️**
    - *Mecánica*: Votación comunitaria de impacto múltiple con recompensa de Bloque Especial para el primer puesto.

---

## 🎨 Efectos Visuales, Shaders GLSL & Audio 3D

### 1. Suelo Cuántico con Shader Reactivo a la Ronda
El suelo no es una textura estática, sino un shader GLSL procedural ejecutado en la GPU:
- **Evolución Cromática**:
  - *Rondas 1 a 3 (Fase Génesis)*: Resplandor cyan y azul matriz profundo (`#00f0ff`).
  - *Rondas 4 a 7 (Fase DeFi)*: Púrpura eléctrico y violeta interestelar (`#a855f7`).
  - *Rondas 8 a 10 (Fase Clímax / Superciclo)*: Oro solar, destellos ámbar y magenta láser (`#f59e0b` / `#ec4899`).
- **Frecuencia de Pulso**: Aumenta progresivamente de un latido cósmico pausado (1.1 rad/s) a una taquicardia cibernética acelerada (3.9 rad/s) en la última ronda.
- **Ondas de Choque Radiales (`triggerFloorGridSurge`)**: Al cambiar de ronda, validar bloques o hacer clic en la píldora de ronda, una onda expansiva de energía recorre la cuadrícula.

### 2. Sistema de Cámaras Orbitales
- **Vista Isométrica (Predeterminada)**: Perspectiva cinematográfica óptima para seguir la acción del tablero.
- **Vista Cenital (Top-Down)**: Vista estratégica completa desde arriba para planificar tiradas y revisar distritos.
- **Modo Drone 360°**: Movimiento orbital continuo alrededor del Núcleo Central Blockchain.
- **Zoom Dinámico**: Aproximación automática al personaje en movimiento durante su tirada de dados.

### 3. Motor de Audio Sintetizado (Sin Dependencias Externas)
Implementado enteramente mediante `AudioContext` nativo:
- Sonidos de dados rodando y clic de casillas.
- Fanfarria de victoria y armonía de validación de bloque.
- Tono de advertencia de penalización de gas.
- Efecto sonoro de warp cuántico y activación de escudos.

---

## 🔐 Sistema de Billetera Sandbox & Seguridad Web3

- **Billetera Sandbox Didáctica**: El juego incluye un simulador de billetera Web3 con dirección simulada (`0x71C...3A9f`), saldo de GWEI en tiempo real y red de pruebas didáctica.
- **Escudo Global Anti-Interferencias de Extensiones**: Implementa un interceptor de errores para evitar que extensiones del navegador de terceros (como MetaMask o Phantom inyectadas en iframes) interrumpan la ejecución del juego o emitan falsos positivos de consola.

---

## 📚 Glosario y Aprendizaje Integrado

El juego cuenta con un **Glosario Web3 Completo** accesible desde el botón superior `📖 GLOSARIO`, explicando con definiciones claras y directas términos clave:
- *Blockchain & Bloque Génesis*
- *Proof of Work (PoW) vs. Proof of Stake (PoS)*
- *Gas & GWEI*
- *Smart Contracts & dApps*
- *DeFi & AMM (Automated Market Makers)*
- *Airdrops & Staking*
- *DAO (Organización Autónoma Descentralizada)*
- *Rug Pull, Phishing & Buenas Prácticas de Ciberseguridad*

---

## 🚀 Instalación, Desarrollo & Despliegue

### Requisitos Previos
- **Node.js** v18.0 o superior
- **npm** o **bun**

### Pasos de Instalación

```bash
# 1. Clonar el repositorio
git clone <URL_DEL_REPOSITORIO>
cd remix-cryptoparty-3d

# 2. Instalar dependencias
npm install

# 3. Iniciar el servidor de desarrollo local (Puerto 3000)
npm run dev

# 4. Compilar para producción
npm run build

# 5. Comprobación de tipos y linting
npm run lint
```

---

## ⌨️ Atajos de Teclado & Controles

| Tecla / Acción | Función |
|---|---|
| **Espacio / Enter** | Tirar el dado cuando sea el turno del jugador humano. |
| **Arrastrar Ratón (Click Izquierdo)** | Rotar la cámara 3D alrededor de la arena. |
| **Rueda del Ratón** | Zoom in / Zoom out en el tablero. |
| **Click Derecho + Arrastrar** | Desplazar el punto focal de la cámara (Pan). |
| **Click en Casilla** | Ver la tarjeta de información y lore del distrito correspondiente. |
| **Click en Núcleo Central** | Ver estado del consenso y emitir sonido armónico. |
| **Click en Píldora de Ronda** | Emitir una onda cuántica en el suelo neón. |
| **Botón 🔊 Audio** | Activar / Silenciar los efectos de sonido sintetizados. |
| **Botón ⚡ Velocidad** | Alternar entre velocidad normal (1x) y rápida (2x) de animaciones. |
| **Botón 📷 Cámara** | Alternar entre vista Isométrica, Cenital y Drone 360°. |

---

<div align="center">
  <sub>Desarrollado con pasión para la alfabetización financiera y tecnológica descentralizada.</sub>
</div>
