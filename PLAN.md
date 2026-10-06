# 🧭 Ruta IA — Camino A: Construir con IA

> **Objetivo:** entender qué es la IA moderna, cómo se interactúa con ella y cómo se construyen
> cosas encima: APIs, herramientas, RAG, agentes, arneses, MCP y skills. La meta final es
> **un agente que trabaje solo**.
>
> **Lenguaje:** Python (desde cero, aprovechando experiencia previa en C++, Scala, Spark y Java).
> **Ritmo sugerido:** 1–2 horas diarias, 5 días por semana.
> **Duración estimada:** ~6–7 meses.
> **Inicio:** 2026-10-05

---

## 📍 Dónde voy

| # | Módulo | Carpeta | Duración | Estado |
|---|---|---|---|---|
| 0 | Python desde cero | `00-python/` | 4–5 semanas | 🟡 En curso |
| 1 | Fundamentos: qué es la IA y cómo funciona un LLM | `01-fundamentos-ia/` | 1–2 semanas | ⬜ |
| 2 | Prompting: cómo hablarle a un modelo | `02-prompting/` | 1–2 semanas | ⬜ |
| 3 | La API: interactuar con LLMs desde código | `03-api-llms/` | 2 semanas | ⬜ |
| 4 | Tool use: darle herramientas al modelo | `04-tool-use/` | 2 semanas | ⬜ |
| 5 | RAG: que el modelo use tus datos | `05-rag/` | 2–3 semanas | ⬜ |
| 6 | Agentes: el bucle agéntico desde cero | `06-agentes/` | 2–3 semanas | ⬜ |
| 7 | Arneses: la infraestructura alrededor del agente | `07-arneses/` | 2 semanas | ⬜ |
| 8 | MCP: conectar agentes con el mundo | `08-mcp/` | 2 semanas | ⬜ |
| 9 | Skills: capacidades empaquetadas | `09-skills/` | 1–2 semanas | ⬜ |
| 10 | Multi-agente: orquestar varios agentes | `10-multi-agente/` | 2 semanas | ⬜ |
| 11 | Evals y seguridad: que funcione y no se rompa | `11-evals-y-seguridad/` | 2 semanas | ⬜ |
| 12 | 🏆 **Proyecto final:** agente autónomo | `12-agente-autonomo/` | 3–4 semanas | ⬜ |

Leyenda: ⬜ pendiente · 🟡 en curso · ✅ dominado

**Regla para avanzar:** un módulo se marca ✅ solo cuando cumples todo su **"Criterio de dominio"**.

---

## Cómo trabajamos

- **Cada módulo tiene:** conceptos → mini-ejercicios → 2–3 proyectos → criterio de dominio.
- **Proyectos con tus propios datos** siempre que se pueda (Strava, Notion, archivos personales), porque así hay más motivación.
- **Primero a mano, después con frameworks.** Construimos cada cosa desde cero para entenderla y solo después usamos la herramienta que la resuelve.
- **Un proyecto = una subcarpeta** dentro del módulo (por ejemplo `04-tool-use/p1-calculadora/`).
- **Control de costos:** usar la API cuesta dinero. Los modelos pequeños y baratos (Haiku) sirven para practicar, y los grandes se reservan para cuando de verdad hacen falta. Configura un límite de gasto mensual en la consola del proveedor.
- **Seguridad desde el día 1:** las API keys van en un archivo `.env`, que **nunca** se sube a git (ya está en `.gitignore`).

### Flujo con Git
- **Commit al terminar cada ejercicio o proyecto**, con un mensaje descriptivo:
  `git add -A && git commit -m "M0: ejercicio ritmo.py terminado"`
- **Prefijo con el módulo** en cada mensaje (`M0:`, `M3:`, `M12:`…) para que el historial cuente tu progreso.
- **Revisa antes de cada commit** con `git status` y `git diff`, para no subir nada que no deba ir.
- **Al cerrar un módulo**, márcalo ✅ en la tabla y crea una etiqueta: `git tag m0-completado`.

---

## Módulo 0 — Python desde cero
📁 `00-python/`

Es la base de todo. Se ve completo, pero a ritmo de alguien que ya programa: cada tema se contrasta con C++ y Scala.

**Temas**
1. Sintaxis, tipos, indentación, strings, f-strings, entrada y salida
2. Colecciones: listas, tuplas, diccionarios, sets, comprehensions
3. Funciones, lambdas, `*args`/`**kwargs`, scope, closures
4. Clases, `@dataclass`, dunder methods (`__str__`, `__eq__`…)
5. Excepciones, archivos, módulos, paquetes
6. Entornos virtuales (`venv`), `pip`, `requirements.txt`
7. Python idiomático: iteradores, generadores, type hints
8. **Imprescindibles para IA:**
   - JSON (`json`), HTTP (`httpx`/`requests`), variables de entorno (`python-dotenv`)
   - **Pydantic**: validación de datos (clave para la salida estructurada y las tools)
   - **`async`/`await`** básico (se parece a los Futures de Scala)
   - Git y GitHub

**Proyectos**
- [ ] `modulo-01/ritmo.py`: calculadora de ritmo de carrera
- [ ] Gestor de tareas por línea de comandos que guarde en JSON
- [ ] Cliente de una API pública (clima, por ejemplo) con `httpx` + Pydantic

**Criterio de dominio**
- [ ] Escribo un script de ~150 líneas con clases, funciones y manejo de errores sin buscar sintaxis básica
- [ ] Creo un proyecto con `venv`, dependencias y `.env` desde cero
- [ ] Consumo una API REST, valido la respuesta con Pydantic y manejo errores de red
- [ ] Explico qué hace `async`/`await` y cuándo usarlo

**Recursos:** tutorial oficial de Python (docs.python.org/es), *Automate the Boring Stuff with Python*, CS50P (Harvard, gratis).

---

## Módulo 1 — Fundamentos: qué es la IA y cómo funciona un LLM
📁 `01-fundamentos-ia/`

No se programa casi nada. El objetivo es construir un **modelo mental correcto**, porque todo lo demás se apoya en él.

**Temas**
- IA vs Machine Learning vs Deep Learning vs IA generativa
- Qué es una red neuronal (intuición, sin matemáticas pesadas)
- **Cómo funciona un LLM:** predice el siguiente token
- **Tokens** y tokenización: por qué importan para el costo y los límites
- **Ventana de contexto:** la "memoria de trabajo" del modelo
- Entrenamiento: pre-training → fine-tuning → RLHF
- **Embeddings:** texto convertido en vectores de significado
- Parámetros de generación: temperatura y `max_tokens`
- Limitaciones: alucinaciones, fecha de corte de conocimiento, no determinismo
- El panorama actual: modelos frontera (Claude, GPT, Gemini) vs abiertos (Llama, Mistral, Qwen)

**Proyectos**
- [ ] Notebook "explorando tokens": tokeniza textos en español e inglés y compara cuántos tokens usa cada uno
- [ ] Experimento de temperatura: el mismo prompt 10 veces con temperatura 0 y con temperatura 1, analizando la variabilidad
- [ ] Escribe con tus palabras un `explicacion.md`: "Cómo funciona un LLM, explicado a un amigo"

**Criterio de dominio**
- [ ] Explico qué es un token, la ventana de contexto y la temperatura sin consultar nada
- [ ] Explico por qué un LLM alucina
- [ ] Explico qué es un embedding y para qué sirve

**Recursos:** Andrej Karpathy, *Intro to Large Language Models* y *Deep Dive into LLMs* (YouTube); 3Blue1Brown, serie *Neural Networks* (capítulos sobre transformers y atención).

---

## Módulo 2 — Prompting: cómo hablarle a un modelo
📁 `02-prompting/`

**Temas**
- Anatomía de un prompt: rol, contexto, tarea, formato, ejemplos
- **System prompt** vs mensajes de usuario
- Ser claro y directo: el modelo como "colaborador brillante sin contexto"
- Few-shot: enseñar con ejemplos
- Estructurar con etiquetas XML (`<documento>`, `<instrucciones>`)
- Pedir razonamiento paso a paso (*chain of thought*)
- Prompts largos: dónde poner los documentos y dónde la pregunta
- Encadenar prompts (*prompt chaining*)
- Iterar: escribir un prompt → probar → medir → ajustar

**Proyectos**
- [ ] Biblioteca personal de prompts (`prompts/`) con al menos 10 prompts probados y documentados
- [ ] Clasificador de correos o notas en categorías, iterado hasta alcanzar más de 90% de aciertos en 20 ejemplos
- [ ] Generador de resúmenes de documentos largos con formato fijo

**Criterio de dominio**
- [ ] Tomo un prompt que falla y lo mejoro de forma sistemática (no a ciegas)
- [ ] Sé cuándo usar few-shot, XML o razonamiento paso a paso

**Recursos:** guía de prompt engineering de Anthropic (docs.claude.com); tutorial interactivo de prompt engineering en `github.com/anthropics/courses`.

---

## Módulo 3 — La API: interactuar con LLMs desde código
📁 `03-api-llms/`

Aquí deja de ser un chat y se convierte en software.

**Temas**
- Crear cuenta, API key, límite de gasto, consola
- SDK de Python: tu primera llamada
- Estructura de mensajes: `system`, `user`, `assistant`, conversación multi-turno
- **El modelo no tiene memoria:** tú mandas el historial completo en cada llamada
- **Streaming:** recibir la respuesta token por token
- **Salida estructurada:** obtener JSON válido y validarlo con Pydantic
- Visión: enviar imágenes y PDFs
- Costos: tokens de entrada y salida, **prompt caching**, batch API
- Manejo de errores: rate limits, reintentos, timeouts
- Elegir el modelo adecuado para cada tarea (rápido y barato vs potente)

**Proyectos**
- [ ] Chatbot de terminal con historial y streaming
- [ ] Extractor de datos: de facturas, tickets o PDFs a JSON validado con Pydantic
- [ ] **Coach de entrenamiento v1:** lee tus actividades (exportadas de Strava) y genera un análisis semanal
- [ ] Medidor de costos: un wrapper que registre tokens y costo por llamada

**Criterio de dominio**
- [ ] Construyo un chat multi-turno sin mirar la documentación
- [ ] Obtengo salida estructurada confiable y valido el resultado
- [ ] Estimo cuánto costará un proyecto antes de ejecutarlo
- [ ] Mi código sobrevive a errores de red y rate limits

**Recursos:** documentación de la API de Anthropic (docs.claude.com), curso *API fundamentals* en `github.com/anthropics/courses`.

---

## Módulo 4 — Tool use: darle herramientas al modelo
📁 `04-tool-use/`

**El concepto más importante de toda la ruta.** Un agente es, en esencia, un LLM que usa herramientas dentro de un bucle.

**Temas**
- Qué es una tool: una función tuya descrita con nombre, descripción y JSON Schema
- El ciclo: el modelo **pide** usar una tool → **tu código** la ejecuta → le devuelves el resultado
- Escribir buenas descripciones de tools (el modelo solo ve eso)
- Varias tools en una conversación, y tools en paralelo
- Manejo de errores dentro de tools
- Tools del servidor: búsqueda web y ejecución de código del lado del proveedor
- Generar el JSON Schema automáticamente desde Pydantic

**Proyectos**
- [ ] Calculadora: el modelo usa una tool para hacer cuentas exactas
- [ ] Asistente con 4–5 tools: clima, hora, leer archivo, buscar en notas, guardar nota
- [ ] **Coach de entrenamiento v2:** el modelo decide qué datos consultar (`get_activities`, `get_stats`, `compare_weeks`)

**Criterio de dominio**
- [ ] Implemento el ciclo de tool use a mano, sin frameworks
- [ ] Diseño tools que el modelo usa correctamente a la primera
- [ ] Explico por qué el modelo nunca ejecuta nada por sí mismo

**Recursos:** documentación de tool use de Anthropic, curso *Tool use* en `github.com/anthropics/courses`.

---

## Módulo 5 — RAG: que el modelo use tus datos
📁 `05-rag/`

**Temas**
- El problema: el modelo no conoce tus documentos y el contexto es finito
- Retrieval-Augmented Generation: buscar → inyectar en el prompt → responder
- **Embeddings** en la práctica: generar vectores y medir similitud
- **Chunking:** cómo partir documentos
- Bases de datos vectoriales: Chroma (local), pgvector
- Búsqueda híbrida: semántica + palabras clave (BM25)
- Reranking
- Citar fuentes en las respuestas
- Cuándo **no** hace falta RAG (contextos largos, prompt caching)
- RAG agéntico: el retrieval como una tool más

**Proyectos**
- [ ] Buscador semántico de tus notas o PDFs (sin LLM, solo embeddings)
- [ ] "Chatea con tus documentos": RAG completo con citas
- [ ] Comparativa: RAG ingenuo vs híbrido vs con reranking, midiendo la calidad de cada uno

**Criterio de dominio**
- [ ] Construyo un pipeline RAG de punta a punta
- [ ] Diagnostico si un fallo viene del retrieval o de la generación
- [ ] Decido con criterio entre RAG, contexto largo o una tool de búsqueda

**Recursos:** artículo *Contextual Retrieval* de Anthropic, documentación de Chroma, cursos cortos de RAG en DeepLearning.AI.

---

## Módulo 6 — Agentes: el bucle agéntico desde cero
📁 `06-agentes/`

**Temas**
- Qué es (y qué no es) un agente: **workflows** vs **agentes**
- Patrones de workflow: chaining, routing, paralelización, orchestrator-workers, evaluator-optimizer
- **El bucle agéntico:** pensar → actuar (tool) → observar → repetir hasta terminar
- Condiciones de parada y límites (máximo de iteraciones, presupuesto de tokens)
- Planificación y auto-corrección
- **Memoria:** de corto plazo (contexto) y de largo plazo (archivos, base de datos)
- Gestión del contexto: resumir y compactar cuando la conversación crece
- Cuándo **no** usar un agente

**Proyectos**
- [ ] **Mini-agente desde cero (~200 líneas, sin frameworks):** bucle + tools de archivos + shell con confirmación
- [ ] Agente investigador: recibe una pregunta, busca en la web, lee páginas y escribe un reporte
- [ ] Agente con memoria persistente que recuerda tus preferencias entre sesiones

**Criterio de dominio**
- [ ] Escribo el bucle agéntico de memoria y explico cada parte
- [ ] Elijo entre workflow y agente según el problema
- [ ] Mi agente se detiene de forma segura y no entra en bucles infinitos

**Recursos:** artículo *Building Effective Agents* de Anthropic (lectura obligatoria), blog de ingeniería de Anthropic.

---

## Módulo 7 — Arneses: la infraestructura alrededor del agente
📁 `07-arneses/`

Un **arnés** (harness) es todo lo que rodea al modelo para convertirlo en un agente útil: el bucle, las tools, la gestión de contexto, los permisos, los hooks y la interfaz. Claude Code es un arnés, y tu mini-agente del Módulo 6 también.

**Temas**
- Anatomía de un arnés: bucle, registro de tools, contexto, permisos, hooks, UI
- **Ingeniería de contexto:** qué entra en la ventana, cuándo y en qué orden
- Permisos y sandboxing: qué puede hacer el agente sin preguntar
- Hooks: ejecutar tu código antes o después de cada acción
- Subagentes y delegación
- **Estudio de caso: Claude Code** (lo estás usando ahora mismo), con `CLAUDE.md`, settings, hooks, slash commands y modo headless (`claude -p`)
- **Claude Agent SDK:** el arnés de Claude Code como librería de Python
- Otros frameworks: LangGraph, Pydantic AI, OpenAI Agents SDK (para comparar)

**Proyectos**
- [ ] Mejora tu mini-agente del Módulo 6 con permisos, hooks, logging y compactación de contexto
- [ ] El mismo agente reconstruido con el Agent SDK, comparando código y resultados
- [ ] Configura Claude Code para este repo: `CLAUDE.md`, hooks y comandos propios

**Criterio de dominio**
- [ ] Explico qué aporta un arnés más allá de "llamar al modelo"
- [ ] Construyo un agente con el Agent SDK con tools y permisos propios
- [ ] Diseño qué contexto recibe un agente para una tarea dada

**Recursos:** documentación de Claude Code y del Claude Agent SDK (docs.claude.com), blog de ingeniería de Anthropic (artículos sobre context engineering y harnesses).

---

## Módulo 8 — MCP: conectar agentes con el mundo
📁 `08-mcp/`

**Temas**
- El problema: N agentes × M servicios = N×M integraciones
- **Model Context Protocol:** el "USB-C" de los agentes
- Arquitectura: host, cliente y servidor
- Primitivas: **tools**, **resources** y **prompts**
- Transportes: stdio (local) y HTTP (remoto)
- Usar servidores existentes (ya tienes Notion y Strava conectados a Claude)
- **Construir tu propio servidor MCP** en Python (SDK oficial / FastMCP)
- Autenticación (OAuth) y seguridad: qué exponer y qué no

**Proyectos**
- [ ] Servidor MCP de tus notas locales: buscar, leer y crear
- [ ] Servidor MCP de una API que uses (por ejemplo tu propio análisis de entrenamientos)
- [ ] Conectar tus servidores a Claude Code y a tu agente del Módulo 7

**Criterio de dominio**
- [ ] Explico la arquitectura de MCP y cuándo usarlo en lugar de tools directas
- [ ] Publico un servidor MCP que funcione en Claude Code y en mi propio agente

**Recursos:** modelcontextprotocol.io (especificación y tutoriales), SDK de Python de MCP en GitHub.

---

## Módulo 9 — Skills: capacidades empaquetadas
📁 `09-skills/`

**Temas**
- Qué es una **skill**: una carpeta con un `SKILL.md` (instrucciones + metadatos) y, opcionalmente, scripts y recursos
- **Carga progresiva:** el agente solo ve el nombre y la descripción hasta que necesita la skill, lo que ahorra contexto
- Skills vs MCP vs tools vs system prompt: cuándo usar cada uno
- Escribir una buena descripción (decide cuándo se activa la skill)
- Skills con scripts: el agente ejecuta código empaquetado
- Skills en Claude Code, en Claude.ai y en la API / Agent SDK
- Evaluar y mejorar skills

**Proyectos**
- [ ] Skill "reporte de entrenamiento": genera tu reporte semanal con un formato fijo
- [ ] Skill con scripts de Python (por ejemplo analizar un CSV y generar gráficas)
- [ ] Skill para tu flujo de trabajo de código (convenciones, tests, commits)

**Criterio de dominio**
- [ ] Explico la carga progresiva y por qué escala mejor que un system prompt gigante
- [ ] Creo una skill que se activa en el momento correcto y produce resultados consistentes

**Recursos:** documentación de Agent Skills (docs.claude.com), repositorio `github.com/anthropics/skills`.

---

## Módulo 10 — Multi-agente: orquestar varios agentes
📁 `10-multi-agente/`

**Temas**
- Por qué usar varios agentes: contexto aislado, paralelismo, especialización
- Patrones: orquestador + trabajadores, pipeline, debate/revisión
- Subagentes en Claude Code y en el Agent SDK
- Comunicación y estado compartido entre agentes
- Costos: varios agentes multiplican el consumo de tokens
- Cuándo **no** vale la pena

**Proyectos**
- [ ] Sistema de investigación: un orquestador reparte subpreguntas a 3 investigadores y un redactor une los resultados
- [ ] Pipeline de código: agente que escribe → agente que revisa → agente que prueba

**Criterio de dominio**
- [ ] Justifico (con números de costo y calidad) cuándo un sistema multi-agente supera a uno solo
- [ ] Construyo un orquestador funcional con subagentes

**Recursos:** artículo de Anthropic sobre su sistema de investigación multi-agente (*How we built our multi-agent research system*).

---

## Módulo 11 — Evals y seguridad: que funcione y no se rompa
📁 `11-evals-y-seguridad/`

**Temas**
- **Evals:** sin medir no sabes si mejoraste
- Datasets de prueba, métricas, evaluación con código y con **LLM-as-judge**
- Evaluar agentes: éxito de la tarea, número de pasos, costo, uso de tools
- Observabilidad: trazas y logs de cada paso del agente
- **Seguridad:**
  - Prompt injection (directa e indirecta, vía documentos o páginas web)
  - Principio de mínimo privilegio para tools
  - Humano en el bucle para acciones irreversibles
  - Manejo de secretos
- Guardrails: validar entradas y salidas

**Proyectos**
- [ ] Suite de evals para tu coach de entrenamiento (20+ casos)
- [ ] "Ataca a tu propio agente": intenta romperlo con prompt injection y luego defiéndelo
- [ ] Dashboard simple de trazas: qué hizo el agente, cuánto costó y cuánto tardó

**Criterio de dominio**
- [ ] Cada cambio de prompt o de modelo lo valido con evals, no "a ojo"
- [ ] Identifico y mitigo los riesgos de prompt injection en mis agentes

**Recursos:** guía de evals de Anthropic (docs.claude.com), promptfoo (herramienta open source de evals).

---

## Módulo 12 — 🏆 Proyecto final: agente autónomo
📁 `12-agente-autonomo/`

**Un agente que trabaja solo:** se ejecuta según un horario o un evento, toma decisiones, usa herramientas, recuerda lo que hizo y te informa, sin que tengas que pedírselo.

**Idea propuesta: "Coach autónomo de entrenamiento"** (ajustable a tus intereses)
- ⏰ Se ejecuta solo cada mañana o al detectar una actividad nueva
- 📥 Lee tus actividades vía MCP (Strava)
- 🧠 Analiza carga, progreso y fatiga, comparando con tu historial (memoria)
- 📝 Escribe un reporte en Notion (vía MCP) usando una skill propia
- 🔔 Te notifica solo si hay algo importante (sobrecarga, récord personal, semana floja)
- 🛡️ Con límites de costo, logs, evals y permisos mínimos

*Alternativas:* agente de noticias o investigación diaria, agente que mantiene un repo de código (issues → PRs), agente de finanzas personales.

**Componentes que integra (toda la ruta)**
- [ ] Bucle agéntico con Agent SDK (M6, M7)
- [ ] Tools propias + servidores MCP (M4, M8)
- [ ] Skill para el formato del reporte (M9)
- [ ] Memoria persistente entre ejecuciones (M6)
- [ ] RAG sobre tu historial o notas, si aplica (M5)
- [ ] Ejecución programada: cron local, GitHub Actions o un servidor en la nube
- [ ] Evals, trazas, presupuesto y guardrails (M11)
- [ ] README con arquitectura, decisiones y lecciones aprendidas

**Criterio de dominio**
- [ ] El agente corre **2 semanas seguidas** sin intervención y produce resultados útiles
- [ ] Puedo explicar cada decisión de diseño y cada componente
- [ ] Está en GitHub como pieza de portafolio

---

## 📓 Bitácora

Anota aquí avances, dudas y aprendizajes clave (lo más reciente arriba).

- **2026-10-05:** Creada la ruta. Decidido: Python como lenguaje y Camino A como objetivo. Empezando Módulo 0, ejercicio `ritmo.py`.
