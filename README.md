# Laboratorio L1 — Primer contacto

**Curso:** Introducción a las Ciencias de la Computación  
**Institución:** Universidad Nacional de Colombia — Sede Manizales  
**Equipo / especie:** **Glitx Synkai**  
**Herramientas:** Python, Google Colab, GitHub y Markdown (Obsidian)

Este repositorio reúne el desarrollo del **Laboratorio L1 — Primer contacto**: el análisis del mensaje de Arecibo, la construcción de herramientas para representar información, el diseño de un mensaje propio y su transmisión por un canal con ruido. Incluye las implementaciones, pruebas, evidencias visuales y reflexiones elaboradas durante las sesiones y la tarea puente.

La pregunta central del laboratorio es cómo **representar, transmitir y recuperar información** cuando el receptor desconoce nuestras convenciones de lectura.

## Guía de lectura

| Etapa | Documentación disponible | Contenido principal |
|---|---|---|
| **Sesión 1 · Recibir** | [Momento 1](sesion_1/momento_1.md) · [Momento 2](sesion_1/momento_2.md) · [Momento 3](sesion_1/momento_3.md) | Hipótesis iniciales, factorización de 1679, visualización y análisis del mensaje de Arecibo, convenciones y reflexión final. |
| **Tarea puente** | [Parte A](tarea_puente/parte_a.md) · [Parte B](tarea_puente/parte_b.md) · [Parte C](tarea_puente/parte_c.md) | Reproducción y verificación con SHA-256, cambios de base y diseño del mensaje de Glitx Synkai. |
| **Sesión 2 · Responder** | [Construcción y transmisión — versión ampliada](sesion_2/momento_2_act.md) · [Análisis del mensaje recibido](sesion_2/recibiendo_un_mensaje_n.md) | Codificación, protección frente al ruido, experimentos y descifrado preliminar de otra especie. |
| **Uso de IA** | [Bitácora de IA](bitacora_IA_L1.md) | Intervenciones relevantes del asistente, decisiones propias y mecanismos de comprobación. |

> [!NOTE]
> En `sesion_2/` se conservan tanto [`momento_2.md`](sesion_2/momento_2.md), con una versión inicial de la documentación, como [`momento_2_act.md`](sesion_2/momento_2_act.md), que incorpora el análisis del canal y la transmisión. **Para seguir el trabajo más completo, consultar `momento_2_act.md`.**

## Estructura del repositorio

```text
laboratorio_primer_contacto/
├── README.md
├── .gitignore
├── bitacora_IA_L1.md
├── mensaje.txt                          # Mensaje propio transmitido
├── recibido.txt                         # Mensaje recibido de otra especie
├── sesion_1/
│   ├── L1_sesion1.ipynb                 # Cuaderno de la sesión 1
│   ├── momento_1.md
│   ├── momento_2.md
│   ├── momento_3.md
│   └── imagenes/                        # Visualizaciones de Arecibo
├── tarea_puente/
│   ├── parte_a.md
│   ├── parte_b.md
│   ├── parte_c.md
│   ├── glitx_synkai_mensaje_bits.txt    # Boceto original: 1679 bits
│   └── imagenes/                        # Boceto y reconstrucción
└── sesion_2/               
    ├── momento_2_act.md                # Documentación
    ├── recibiendo_un_mensaje_n.md      # Análisis preliminar
    └── imagenes/                        # Evidencias de Colab
```

## Resultados principales

### 1. Lectura y representación de Arecibo

- Se estudió una secuencia de **1679 bits**, cuya factorización es **23 × 73**.
- Se implementaron y evaluaron herramientas como `es_primo`, `rectangulos`, `filas_de`, `dibujar` y funciones para interpretar números.
- Se analizaron patrones de conteo, secciones del mensaje y convenciones necesarias para interpretarlo.

[Ver cuaderno de la sesión 1](sesion_1/L1_sesion1.ipynb) · [Ver análisis](sesion_1/momento_2.md)

### 2. Tarea puente y mensaje propio

- Se reprodujo el mensaje de referencia y se comprobó su integridad mediante **SHA-256** y las cifras de control de la guía.
- Se implementaron conversiones iterativas y recursivas entre bases, verificadas con pruebas y casos aleatorios.
- Se diseñó un mensaje visual de **1679 bits** para la especie ficticia **Glitx Synkai**, centrado en un conteo, un laberinto y el desplazamiento de un personaje.

![Reconstrucción del boceto de Glitx Synkai](tarea_puente/imagenes/reconstruccion_del_boceto.png)

[Ver contrato de lectura y decisiones de diseño](tarea_puente/parte_c.md) · [Ver secuencia original](tarea_puente/glitx_synkai_mensaje_bits.txt)

### 3. Construcción y transmisión por un canal con ruido

La versión final no protegida quedó organizada en **53 filas × 47 columnas = 2491 bits**, con secciones separadas por filas de ceros. Se estudiaron dos mecanismos de protección: **paridad par** y **repetición triple con votación mayoritaria**, utilizando una probabilidad de inversión por bit de **1 %**.

| Indicador | Resultado observado |
|---|---:|
| Mensaje final sin protección | 2491 bits |
| Mensaje con paridad | 2544 bits |
| Mensaje con repetición triple | 7473 bits |
| Simulaciones realizadas | 1000 |
| Transmisiones con error en las que la paridad detectó al menos una anomalía | 1000 de 1000 |
| Mensajes recuperados íntegramente mediante repetición triple | 459 de 1000 |

Se eligió **repetición triple** para la transmisión final. El archivo [`mensaje.txt`](mensaje.txt) contiene una única cadena binaria de **7473 bits**, generada tras aplicar la protección elegida y el ruido una sola vez. Los resultados de la simulación corresponden a la ejecución registrada; no son garantías universales.

[Consultar implementaciones, pruebas y análisis](sesion_2/momento_2_act.md)

### 4. Recepción y análisis de un mensaje desconocido

El archivo [`recibido.txt`](recibido.txt) contiene **1311 bits**. A partir de su longitud, las formas rectangulares y la inspección de grupos de tres, se plantearon estas **hipótesis provisionales**:

| Aspecto | Resultado del análisis |
|---|---|
| Posible protección | Repetición triple; 422 de 437 grupos recibidos eran uniformes |
| Longitud tras votación | 437 bits |
| Disposición visual seleccionada | 23 filas × 19 columnas |
| Sistema de conteo probable | Base 6; números del 1 al 8 |
| Figuras reconocidas tentativamente | Una cruz y una taza |

**El significado definitivo de las figuras está pendiente de contraste con el contrato de lectura del equipo emisor.** Reconocer patrones y formular hipótesis no equivale a demostrar que se comprendió el mensaje.

![Sección visual del mensaje recibido](sesion_2/imagenes/seccion_2_recibido_colab.png)

[Leer el análisis detallado](sesion_2/recibiendo_un_mensaje_n.md)

## Cómo consultar el trabajo

1. Abrir los documentos de la **guía de lectura** en el orden de las etapas.
2. Consultar el cuaderno [`sesion_1/L1_sesion1.ipynb`](sesion_1/L1_sesion1.ipynb) en Jupyter o Google Colab para revisar el trabajo ejecutable disponible en este repositorio.
3. Revisar las implementaciones y salidas de Python incluidas en los archivos Markdown, junto con las imágenes de cada carpeta `imagenes/`.
4. Distinguir entre los **datos medidos**, las **interpretaciones propias** y las **hipótesis aún no verificadas**.

> [!IMPORTANT]
> Al momento de esta actualización, el repositorio **solo contiene el cuaderno `.ipynb` de la sesión 1**. Las actividades de la tarea puente y la sesión 2 están documentadas en Markdown, pero sus cuadernos de Colab aún no están publicados aquí.

## Uso responsable de inteligencia artificial

La IA se utilizó como **acompañamiento para aclarar conceptos, revisar intentos, señalar errores y organizar documentación**. Las propuestas, implementaciones y pruebas corresponden al trabajo realizado en el laboratorio. Se registran las consultas seleccionadas y su verificación en la [bitácora de IA](bitacora_IA_L1.md).

## Referencia del curso

Material oficial del laboratorio: [**L1 — Primer contacto · `cmorregof/labs-calculo-2026-2`**](https://github.com/cmorregof/labs-calculo-2026-2/tree/main/introduccion_cc).

---

*Laboratorio L1 — Primer contacto · Universidad Nacional de Colombia, Sede Manizales.*
