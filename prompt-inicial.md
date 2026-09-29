Proyecto Albertina: sistema administrativo para un taller — primera sesión
1. Quién soy (leé esto con atención)
Soy Mariana, estudiante de último año de Ingeniería Informática. Es la primera vez que hago un sistema real. Nunca desarrollé un sistema completo, nunca trabajé para un cliente, nunca puse nada en funcionamiento para que otra persona lo use, y no conozco el mundo administrativo ni contable. Tengo lo que aprendí en la facultad, pero no la experiencia práctica.
Por eso te pido:

* Explicame todo como a alguien que empieza. No des por sentado que sé cómo se hace un sistema, qué etapas tiene, ni qué hace un profesional en cada una.
* Cada vez que uses un término técnico o del dominio, explicalo en 2 o 3 líneas, con un ejemplo si ayuda.
* Guiame paso a paso: decime qué hacer, en qué orden y por qué.
* Si ves que me estoy salteando algo que un profesional haría, avisame aunque no te lo haya preguntado.

Quiero que actúes como un desarrollador senior experto en sistemas de gestión, automatización de procesos e IA, que me guía como mentor. No solo quiero que las cosas se hagan bien: quiero entender el porqué de cada decisión, para poder mantener y defender el sistema frente a la clienta.
2. Dónde guardar los archivos
Todos los archivos que te pida guardar van en la carpeta `C:\Proyecto Albertina`. Ojo: el nombre de la carpeta tiene un espacio, así que en cualquier comando que uses la ruta tiene que ir entre comillas. Si la carpeta o alguna subcarpeta no existe, creala.
3. Cómo quiero que trabajemos

1. Idioma: hablame en español.
2. Explicá antes de hacer: qué vas a hacer, por qué y qué alternativas descartaste.
3. Pasos chicos: avanzá de a una tarea y frená al terminar cada una para que yo la revise.
4. No asumas reglas fiscales ni de negocio. Si algo depende de normativa argentina o de cómo trabaja la clienta, formulalo como pregunta. Si tenés que suponer algo para avanzar, marcalo como `SUPUESTO:`.
5. No inventes: ni normativa, ni librerías, ni APIs, ni versiones. Si no estás seguro de algo, decímelo explícitamente.
6. Pedí permiso antes de instalar cosas, borrar archivos o ejecutar comandos que puedan romper algo.
7. Si algo que te pido es mala idea, decímelo con argumentos.
8. En esta sesión no se escribe código ni se eligen tecnologías. Primero hay que entender bien el problema.

4. Lo que sé del proyecto hasta ahora

* La clienta tiene un taller (todavía no sé el rubro exacto).
* Quiere automatizar el circuito administrativo de cobros y pagos.
* Hoy usa un Excel muy simple donde carga los datos de un remito y lo imprime sobre hojas de remito preimpresas con casilleros vacíos: cada dato cae exactamente en su casillero. Quiere lo mismo para los recibos, pero con una solución más fácil que Excel.
* Cuando paga a un proveedor, hace la transferencia y le manda el comprobante. Quiere empezar a emitir órdenes de pago con formato.
* Le interesa la inteligencia artificial, pero no tiene una idea concreta de para qué usarla.
* No es una persona técnica (lo dice ella misma).
* Estamos en Argentina, así que aplica la normativa local (ARCA, ex AFIP).

5. Transcripción completa del audio de la clienta
Esta es la transcripción textual del audio que me mandó, sin modificaciones:
"Hola Mariana, ¿cómo estás? Perdón que recién te conteste, pero bueno, recién hoy vine al taller y te puedo contar un poco mejor. (0:12) A mí como me interesa un poco como automatizar lo que sería como el circuito de pagos, digamos. (0:23) No sé, cuando yo haga una factura, por ejemplo, que de manera automática yo la pueda cargar en un mensual de esa factura y que a su vez ya se vayan derivando a cada cuenta corriente de los clientes.(0:39) Capaz que estoy hablando un poco chino y si te lo muestro y lo ves, se entiende un poco mejor. (0:46) Pero bueno, va un poco por ahí. (0:48) Nosotros actualmente en Excel tenemos como medio un programita demasiado simple de, nada, yo cargo los datos de un remito, por ejemplo.(0:57) Ya tenemos como un papel que tiene los remitos y como los casilleros vacíos, entonces cuando yo lo pongo en la impresora y pongo imprimir, se me imprime todo, nada, exactamente en donde se tendría que imprimir, no sé si se entiende. (1:15) Lo mismo me gustaría poder hacer con los recibos, o sea, capaz no hacer el mismo programa de Excel, sino ya buscar otra manera más fácil de hacerlo. (1:25) Nada, también algo que lo estamos haciendo actualmente es emitir órdenes de pago, o sea, nosotros siempre cuando yo hago un pago a un proveedor, les mando el comprobante de la transferencia y queda ahí.(1:39) Pero como que me gustaría que se pueda emitir una orden de pago como, no sé, con algún formato, que día, qué factura le estamos pagando, qué día, a qué cliente, como cosas así, cosa que esa orden de pago también pueda ir restándose de las cuentas correctas de cada uno de los proveedores. (2:02) No sé, es como, bueno, obviamente que esto es muy administrativo, obviamente, y por ahí, no, no sé, no entiendes mucho de lo que te estoy hablando, pero sería cuestión de que lo veas y nada, me digas cómo lo podemos hacer. (2:17) Bueno, yo tengo más o menos ideas en la cabeza, algo de inteligencia artificial, sé, poco, o sea, sé, pero más o menos, que también, bueno, se me ocurrió capaz poder entrar por ese lado.(2:35) Nada, tengo un curso ahí también de inteligencia artificial que tengo videos para ver y para practicar, pero bueno, como nada, soy bastante inútil todavía con la tecnología y con estas cosas, entonces como, nada, la solución que vos me puedas dar, buenísimo. (2:51) Y obviamente esto es lo primero que se me va ocurriendo, pero siento que hay como más cosas para pulir todavía."
Notas sobre la transcripción: es un audio hablado transcripto, así que puede tener errores. En particular:

* Donde dice "cuentas correctas de cada uno de los proveedores" (2:02), probablemente quiso decir "cuentas corrientes".
* Donde dice "a qué cliente" al hablar de las órdenes de pago (1:39), probablemente quiso decir "a qué proveedor".

6. Lo que te pido en esta sesión
Hacé estas tareas en orden y frená al final de cada una para que la revise.
Tarea 1 — Guardar el contexto

* Guardá la transcripción textual de la sección 5, sin modificarla y con las notas al final, en `C:\Proyecto Albertina\referencias\audio-clienta-01.md`.
* Guardá este prompt completo en `C:\Proyecto Albertina\prompt-inicial.md`, para tener registro de dónde partimos.

Tarea 2 — Explicame el panorama
Como nunca hice un sistema, antes de las preguntas necesito entender dónde estoy parada. Explicame, de forma simple:

1. Cómo es el proceso de hacer un sistema para un cliente, de principio a fin: qué etapas tiene, qué se hace y qué se entrega en cada una, y en qué etapa estamos ahora.
2. Lo que entendiste de lo que pide la clienta: qué circuitos describe y cómo se relacionan los documentos que menciona.
3. Los conceptos del dominio que necesito entender para poder hablar con ella sin perderme.
4. Qué partes de su pedido están claras y cuáles son ambiguas o faltan.

Guardalo en `C:\Proyecto Albertina\panorama.md`.
Tarea 3 — Las preguntas
Quiero que vos pienses las preguntas, con tu criterio de senior, según lo que creas que me hace falta para completar el proyecto de punta a punta. No solo para entender lo que pide, sino todo lo necesario para diseñarlo, desarrollarlo, ponerlo en funcionamiento y mantenerlo en el tiempo. No te limites a lo que ella mencionó: un buen relevamiento también descubre necesidades que el cliente no dijo.
Explicame con qué criterio elegiste y ordenaste las preguntas, así aprendo a hacerlo yo.
Quiero dos versiones con la misma numeración (P1, P2, P3…):
a) Versión para mí → `C:\Proyecto Albertina\preguntas-clienta.md`. Para cada pregunta:

* por qué importa y qué parte del sistema afecta;
* si es BLOQUEANTE, es decir, si sin esa respuesta no se puede avanzar;
* las respuestas más probables y cómo cambiaría el sistema según cada una;
* si la puede responder mejor su contador;
* dos campos vacíos para completar después: `Estado: PENDIENTE` y `Respuesta:`.

Si hay cosas que tengo que averiguar yo (y no la clienta), listalas aparte en ese mismo archivo.
b) Versión para mandarle a la clienta por WhatsApp → `C:\Proyecto Albertina\mensaje-clienta.txt`:

* lenguaje simple y sin jerga; si un término técnico es inevitable, explicalo entre paréntesis;
* tono cálido, en español rioplatense con voseo, escrito como si fuera yo;
* formato de WhatsApp: texto plano, títulos de bloque con `*asteriscos simples*`, sin Markdown;
* misma numeración que la versión para mí;
* al principio, invitala a contestar por audio diciendo el número de cada pregunta, y aclarale que si no sabe alguna no pasa nada;
* ella no es técnica: pensá cuántas preguntas es razonable mandarle por mensaje sin abrumarla. Si hacen falta más, proponé dividirlas en rondas o dejar algunas para una reunión, y explicame por qué;
* al final, pedile los materiales (documentos, archivos, fotos) que creas que me van a servir, aclarando que puede tapar nombres y montos. En la versión para mí, explicame para qué sirve cada material.

Tarea 4 — Guía para la reunión presencial
En `C:\Proyecto Albertina\guia-reunion.md`, dame consejos concretos para cuando la vea en persona: qué pedirle que me muestre, cómo registrar lo que veo, qué no prometerle todavía y cómo detectar necesidades que ella no mencionó.
Después de la Tarea 4: frená
No escribas código ni propongas tecnologías todavía. Esperá a que yo vuelva con las respuestas de la clienta.
7. El objetivo final
El objetivo es que al final exista un sistema funcionando que la clienta use en su día a día. No te doy un plan de trabajo: cuando tengamos las respuestas, quiero que vos me propongas los pasos. Por ahora, tené este objetivo en cuenta al pensar qué información me falta.
