# ¿Y si pasa hoy? — juego serio de ARCADE

**ARCADE** es el equipo que diseña el juego. **«¿Y si pasa hoy?»** es una app web interactiva y responsive (también instalable como PWA) con la que las familias de la **Zona Occidente y Dosquebradas** crean hábitos diarios frente al fenómeno de **El Niño** y otros desastres. Proyecto del semillero para las Olimpiadas Unadistas.

> **Estado:** prototipo. El juego no es un sistema de alertas; ante una emergencia real: ponte a salvo y llama al **123**.

## Cómo se juega (en 30 segundos)

- **5 niveles:** Agua, Energía, Calor, Fuego y Sismo. Cada uno muestra **6 hábitos** a la vez (una *jugada*).
- Cada hábito marcado le quita vida al enemigo del nivel y suma **XP**; con el sexto, una ventana te muestra tu **insignia** y llegan **6 hábitos nuevos** (cada nivel tiene un banco de 18 que se repite).
- **Insignias:** como las de los exploradores. La escalera (Aspirante → Semilla → Explorador → Guardián → Centinela → Leyenda) se sube con la XP, así que **repetir los hábitos** te lleva más arriba. **Familia:** cada integrante juega con su *nickname* y el ranking familiar muestra quién lidera y quién necesita ayuda.
- **EL JEFE:** personaje flotante que abre un chat de apoyo. Conversa con IA si hay un servidor conectado; si no, responde con frases predefinidas. Las emergencias siempre se responden en el momento, sin esperar a la IA.

Manual completo para jugadores: [docs/MANUAL_DE_USUARIO.md](docs/MANUAL_DE_USUARIO.md).

## Probarlo en tu computador

Requisitos: **Node.js 20.6 o superior** (no hay que instalar nada para el juego; el servidor del chat necesita `npm install` una vez).

```bash
cd servidor-jefe && npm install && cd ..   # solo la primera vez
npm run dev:web                              # abre http://localhost:3000
```

Sin clave de la API el juego funciona completo y el chat usa respuestas predefinidas. Para activar la IA, mira [servidor-jefe/README.md](servidor-jefe/README.md) (la clave vive solo en el servidor, nunca en la página).

> El botón **APK para Android** de la portada es solo una **propuesta visual de desarrollo futuro**: todavía no existe un APK. Hoy la app se instala desde el navegador (PWA).

## Qué hay en cada carpeta

| Carpeta | Contenido |
|---|---|
| [`src/`](src) | **El juego** (HTML + CSS + JavaScript sin dependencias ni paso de compilación). Se puede publicar tal cual en cualquier hosting de archivos. |
| [`servidor-jefe/`](servidor-jefe) | Servidor Node que conecta el chat de EL JEFE con Claude sin exponer la clave. Opcional. |
| [`agente-el-jefe/`](agente-el-jefe) | Fuente única de las instrucciones de EL JEFE y paquete del agente de Microsoft 365 Copilot. |
| [`pruebas/`](pruebas) | Pruebas unitarias (`unit/`, en Node) y pruebas en el navegador (`e2e/`). |
| [`docs/`](docs) | Manual de usuario, arquitectura y guía para contribuir. |

## Comandos

| Comando | Qué hace |
|---|---|
| `npm run dev:web` | Servidor de desarrollo en `http://localhost:3000` (juego + chat; incluye `/__pruebas/`). |
| `npm start` | Igual, sin las rutas de pruebas (para publicar). |
| `npm test` | Todas las pruebas unitarias y del servidor (sin red, sin clave, sin gastar créditos). |
| `npm run dev:simulador` + `npm run dev:web:ia` | Prueba el chat con IA contra un **simulador** de la API (puerto 3100). |
| `npm run agente` | Regenera el agente de Copilot y el prompt del servidor desde `agente-el-jefe/instrucciones.md`. |

## Para quien va a tocar el código

1. Lee [docs/ARQUITECTURA.md](docs/ARQUITECTURA.md): cómo está organizado, el flujo de un hábito marcado y el formato de lo que se guarda.
2. Lee [docs/CONTRIBUIR.md](docs/CONTRIBUIR.md): cómo agregar un hábito, un nivel o una sección, y cómo verificar que nada se rompió.

## Pendientes conocidos

- **Contenido por verificar** antes de un uso público: las cifras de la portada (63 %, 1.092 ha), la fecha de la Circular de MinAmbiente, la cifra de la OMM y los consejos de seguridad con la gestión del riesgo municipal.
- **Ranking entre dispositivos:** hoy la familia comparte un dispositivo (todo se guarda en `localStorage`). Sincronizar requiere un servidor con base de datos.
- **APK de Android:** propuesta futura (podría generarse con PWABuilder, Bubblewrap o Capacitor a partir de la PWA ya incluida).
- Declarar en la entrega final la herramienta de IA usada en la construcción.

## Equipo

Natalia Elizabeth Pérez, Henrry Borrero, Jaime Jose Garcia, Nelson Serna y la estudiante semillerista Valentina Rengifo — ARCADE.
