# Taller 3: Plan de Auditoría — Interrapidísimo

**Integrante:** Santiago Moscoso Rodríguez

---

## 1. Identificación del equipo y del caso

| Elemento | Detalle |
|---|---|
| Integrante | Santiago Moscoso Rodríguez (trabajo individual) |
| Organización | Interrapidísimo, empresa colombiana de mensajería y paquetería |
| Sistema o proceso | Plataforma de rastreo de envíos y quién puede entrar a ella (franquicias y personal) |
| Riesgo seleccionado | **R1 — Cuentas activas después del retiro** |
| Marco usado | ISO/IEC 27001 (solo la parte de control de accesos) |
| Cambios al caso o a la matriz | Ninguno. Se usa la matriz del Taller 2 tal cual |

**Sobre los marcos:** en el primer trabajo elegí ISO/IEC 27001, ITIL y COBIT. Para R1 uso solo ISO/IEC 27001, porque es el que trata el control de accesos. ITIL (que el rastreo no se caiga) y COBIT (que las franquicias trabajen igual) responden a otros riesgos de la matriz y no hacen falta aquí.

## 2. Contexto y riesgo seleccionado

Interrapidísimo trabaja con una red de franquicias por todo el país. El sistema que analizo es la plataforma de rastreo de envíos y quién puede entrar a ella. La preocupación central es proteger los datos personales de remitentes y destinatarios, y que todas las franquicias manejen los accesos de la misma forma.

**Riesgo R1 — Cuentas activas después del retiro** (fila R1 de la matriz, sin cambios):

| Campo | Detalle |
|---|---|
| Activo o proceso | A1. Cuentas de acceso de franquicias y personal a la plataforma |
| Amenaza | Alguien que ya no trabaja en la franquicia (o una franquicia desvinculada) intenta entrar a la plataforma |
| Vulnerabilidad | Las cuentas siguen activas después del retiro y nadie las revisa de forma periódica (S1) |
| Consecuencia posible | Un exempleado consulta datos de envíos y los usa para estafar a destinatarios: fuga de datos personales, quejas y posibles problemas legales |
| Probabilidad | 4: hay mucha rotación en los puntos de servicio y, sin revisión, las cuentas viejas se acumulan |
| Impacto | 4: se exponen datos personales de varios usuarios |
| Nivel | 16 |
| Control actual | Supuesto: no hay revisión periódica (S1). No es un hecho comprobado |
| Control propuesto | Desactivar la cuenta automáticamente al terminar el vínculo y revisar cada mes las cuentas activas sin vínculo vigente, con acta firmada |

## 3. Justificación y objetivo de auditoría

**¿Por qué vale la pena auditar R1?** El puntaje (16) lo pone primero en la matriz, pero hay más razones:

- **Es la puerta de entrada.** Si los accesos de personas que ya se fueron siguen abiertos, no importa qué tan bien estén los demás controles.
- **Se puede revisar con evidencia concreta.** Se comparan dos listas (cuentas activas contra personal vigente) y cada cuenta tiene una respuesta clara: debería estar activa o no.
- **Junta dos preocupaciones del caso:** datos personales y consistencia entre franquicias, porque cada franquicia administra a su propia gente.
- **Su control deja rastro:** actas, fechas de retiro y registros de último ingreso que un auditor puede pedir.

**Objetivo principal:** Determinar si las cuentas de acceso a la plataforma de rastreo, tanto de franquicias como de personal propio, se desactivan dentro del plazo establecido cuando termina el vínculo de la persona, de acuerdo con el procedimiento vigente y con el control de acceso de ISO/IEC 27001, durante los últimos seis meses.

## 4. Alcance funcional y exclusiones

| Elemento | Definición |
|---|---|
| Proceso o función | Baja de usuarios: desactivar las cuentas cuando termina el vínculo de la persona (contrato del empleado o relación con la franquicia) |
| Sistema o componente | Plataforma de rastreo de envíos, solo el módulo de administración de usuarios y el registro de ingresos (quién entró y cuándo) |
| Población | Cuentas de franquicias y de personal propio cuyo vínculo terminó en el periodo, más un chequeo de cuentas activas al corte contra el personal vigente |
| Periodo | Del 1 de abril al 30 de septiembre de 2026: seis meses completos y ya cerrados, así la evidencia está terminada y es comparable |
| Áreas o responsables | TI / administración de la plataforma (listado de cuentas y registros de ingreso), Gestión Humana (fechas de retiro del personal propio) y coordinación de franquicias (vínculo de las franquicias y su personal) |

**Inclusiones:** cuentas de franquicias y de personal propio en la plataforma, el procedimiento de baja y las fechas de retiro, y los registros de último ingreso de cada cuenta.

**Exclusiones (con su razón):**

- *Otros sistemas (facturación, correo):* R1 trata de la plataforma de rastreo; meterlos diluiría el alcance.
- *Cuentas de clientes finales:* el control a evaluar es el de personal y franquicias.
- *R3 — Caída del rastreo en temporada alta y R4 — Computadores de franquicia sin estándar mínimo:* son otros riesgos de la matriz y tendrían su propio plan.

**Limitación que afecta la conclusión:** solo se pueden comparar las salidas que alguien haya reportado. Si una franquicia no avisa que desvinculó a una persona, esa cuenta no aparece como baja. Por eso se incluye el chequeo de cuentas activas al corte, que cubre esa parte, aunque no del todo.

## 5. Criterios aplicables o por confirmar

| # | Control a revisar | Condición esperada | Fuente | Por qué aplica al caso |
|---|---|---|---|---|
| C1 | Desactivar la cuenta al terminar el vínculo | La cuenta se desactiva dentro del plazo que defina la empresa, contado desde la fecha en que termina el vínculo de la persona | Procedimiento interno de bajas: criterio por confirmar mediante solicitud de la política vigente (incluido el plazo). Apoyo: ISO/IEC 27001, Anexo A, controles de derechos de acceso y de responsabilidades al terminar el vínculo | Es justo la vulnerabilidad de **R1 — Cuentas activas después del retiro** |
| C2 | Revisar las cuentas activas | Alguien compara cada cierto tiempo las cuentas activas con el personal vigente, con responsable y registro de la revisión | Política interna de revisión de accesos: criterio por confirmar mediante solicitud de la política vigente (incluida la periodicidad). Apoyo: ISO/IEC 27001, Anexo A, control de derechos de acceso, que incluye su revisión periódica | Si una baja se escapa, esta revisión es la segunda oportunidad de detectarla |
| C3 | Avisar la salida de una persona | Quien conoce la salida (Gestión Humana o coordinación de franquicias) se lo informa a TI y queda registro del aviso | Procedimiento interno de retiro de personal y desvinculación de franquicias: criterio por confirmar mediante solicitud de la política vigente. Apoyo: ISO/IEC 27001, Anexo A, controles de derechos de acceso y de responsabilidades al terminar el vínculo | Si la franquicia no avisa, la cuenta nunca se da de baja: es la limitación del alcance |

## 6. Programa de trabajo

Riesgo: **R1 — Cuentas activas después del retiro**. Periodo: 1 de abril al 30 de septiembre de 2026.

### P1. Entender y verificar el diseño del control

| Elemento | Detalle |
|---|---|
| Control | Desactivar la cuenta al terminar el vínculo y revisar las cuentas activas. Se supone que lo hace TI, con aviso de Gestión Humana o la coordinación de franquicias (por confirmar) |
| Criterio | C1, C2 y C3: existe una regla de baja con plazo, hay una revisión periódica y hay un aviso de salida con registro |
| Procedimiento | 1) Solicitar la política o procedimiento de bajas y confirmar que está vigente. 2) Entrevistar a TI, Gestión Humana y la coordinación de franquicias para entender quién avisa, a quién y cómo. 3) Pedir una captura de la configuración de la plataforma para ver si la desactivación es automática o manual. 4) Comparar lo que dicen las personas con lo que dicen los documentos |
| Población o muestra | No aplica muestra: se revisan documentos y configuración, no casos |
| Evidencia esperada | Política o procedimiento de bajas con fecha y versión, descripción de cargos o responsables, captura de la configuración de usuarios y notas firmadas de las entrevistas |
| Posibles excepciones | No existe política, existe pero no define plazo ni responsable, o lo que cuentan las personas no coincide con los documentos. Si no entregan la evidencia pedida, se registra como falta de evidencia |

### P2. Verificar la operación de las bajas

| Elemento | Detalle |
|---|---|
| Control | La baja de la cuenta cuando alguien se retira, a cargo de TI, y la revisión de cuentas activas |
| Criterio | C1: la cuenta se desactiva dentro del plazo que defina la empresa, desde la fecha de terminación del vínculo. C2: toda cuenta activa tiene un vínculo vigente |
| Procedimiento | 1) Pedir a Gestión Humana y a la coordinación de franquicias el listado de retiros del periodo, con fecha. 2) Pedir a TI, directamente del sistema, el listado de cuentas con su estado y su fecha de desactivación. 3) Cruzar ambos listados y calcular, por cada retiro, los días entre el retiro y la desactivación. 4) Pedir el registro de último ingreso de cada cuenta de la muestra y revisar si hubo ingresos después de la fecha de retiro. 5) Anotar cada excepción con persona, cuenta, fechas y días de demora. 6) Cruzar las cuentas activas al 30 de septiembre de 2026 con el personal y las franquicias vigentes a esa fecha, para detectar cuentas sin vínculo que nadie reportó |
| Población o muestra | Todos los retiros del periodo. Si son pocos, se revisan todos; si son muchos, se toma una muestra aleatoria, con tamaño por definir cuando se conozca la población real. Personal propio y franquicias se separan para que ninguno quede sin revisar |
| Evidencia esperada | Listados de retiros y de cuentas exportados del sistema (no armados a mano), registros de último ingreso, avisos de salida de la muestra y listados de personal y franquicias vigentes al corte |
| Posibles excepciones | Cuenta desactivada fuera del plazo, cuenta sin desactivar, ingreso registrado después del retiro (la más grave) o cuenta activa sin vínculo vigente. También se anota si no hay registro del aviso de salida |

**Cómo se corrobora lo que dicen las entrevistas:** en P1 se entrevista, pero cada cosa que digan se contrasta con un documento o una configuración. En P2 la conclusión sale de listados exportados del sistema y registros de ingreso, no de lo que alguien cuente.

### Fila de trazabilidad

| ID del riesgo | Control a evaluar | Criterio y fuente | Procedimiento | Población o muestra | Evidencia esperada |
|---|---|---|---|---|---|
| R1 | Política de bajas, revisión de cuentas y aviso de salida (diseño) | C1, C2 y C3: políticas internas (por confirmar); apoyo en ISO/IEC 27001, control de accesos | P1 | Documentos y configuración, sin muestra | Política vigente, responsables, captura de configuración, notas de entrevistas |
| R1 | Desactivar la cuenta al terminar el vínculo | C1: procedimiento interno de bajas (por confirmar) | P2, pasos 1 a 5 | Todos los retiros del periodo o muestra aleatoria (tamaño por definir) | Listados exportados del sistema, registros de último ingreso |
| R1 | Revisar cuentas activas contra personal vigente | C2: política interna de revisión (por confirmar) | P2, paso 6 | Cuentas activas al 30 de septiembre de 2026 | Listado de cuentas activas, listados de personal y franquicias vigentes, actas de revisión |
| R1 | Avisar la salida de una persona | C3: procedimiento interno de retiro (por confirmar) | P1 (diseño) y P2, paso 5 (operación) | Retiros de la muestra | Avisos de salida registrados |

## 7. Responsables, cronograma, supuestos y limitaciones

### 7.1 Responsables y cronograma

Como el trabajo es individual, Santiago Moscoso Rodríguez es el responsable de todas las fases. Es una propuesta de 5 semanas, contadas desde que la empresa aprobara la auditoría.

| Fase | Semana | Qué se haría | Producto |
|---|---|---|---|
| Preparación | 1 | Afinar el programa de trabajo y preparar la lista de documentos a pedir, la guía de entrevista y la plantilla de excepciones | Plan ajustado y plantillas listas |
| Solicitud de información | 2 a 3 | Enviar la solicitud formal, hacer seguimiento y recibir política, listados y configuración | Evidencia recibida y registrada, con fecha y quién la entregó |
| Revisión | 3 a 4 | Hacer las entrevistas (P1), cruzar los listados (P2) y anotar las excepciones | Registro de excepciones y papeles de trabajo |
| Cierre | 5 | Confirmar con TI y Gestión Humana que los datos están bien leídos y preparar la conclusión | Conclusión preliminar y lista de pendientes |

**Dependencias de la organización:**

- Autorización de la empresa para hacer la auditoría y acceder a la información.
- TI entrega los listados exportados del sistema y la captura de configuración.
- Gestión Humana entrega el listado de retiros del periodo, con fechas.
- La coordinación de franquicias entrega la lista de franquicias vigentes y desvinculadas.
- Disponibilidad de estas áreas para las entrevistas.
- Cuidado con los datos personales: los listados traen datos de personas, así que se pediría que los nombres vengan codificados cuando sea posible y que el acceso sea solo de lectura.

**Recursos necesarios:** hoja de cálculo para cruzar listados y calcular demoras, plantilla de solicitud de información, guía de entrevista, plantilla de registro de excepciones y una carpeta segura para la evidencia.

**Alcance real del taller:** en este trabajo solo se hace la planificación: el plan, los criterios, el programa de trabajo y las plantillas (lista de documentos a pedir, guía de entrevista y registro de excepciones). Todo lo que depende de acceso a la empresa queda como planificación: pedir la política de bajas, hacer las entrevistas, recibir los listados del sistema, cruzar los datos, encontrar excepciones y llegar a una conclusión. Por eso este documento es un plan y no un informe de resultados.

### 7.2 Supuestos y limitaciones

**Hechos comprobados (con fuente):**

| Hecho | Fuente |
|---|---|
| Interrapidísimo es una empresa colombiana de mensajería y paquetería | Portafolio |
| Tiene más de 3.000 franquicias y llega a 1.103 municipios (las cifras cambian según la fecha de la nota) | Portafolio (ver sección 8) |
| Es el operador con más envíos individuales del país, según el informe de MinTIC | La Nota Económica (ver sección 8) |
| R1 está en la matriz con probabilidad 4, impacto 4 y nivel 16 | Taller 2 de este mismo caso |
| Los controles de ISO/IEC 27001:2022 sobre derechos de acceso (A.5.18) y responsabilidades al terminar el vínculo (A.6.5) existen con ese nombre | Fuentes públicas que citan la versión 2022.|
| No se tuvo acceso a información interna de la empresa | Condición de este trabajo |

**Supuestos (aún no verificados):**

- **S1.** Cada persona de una franquicia tiene su propia cuenta en la plataforma, y no se sabe si alguien las revisa.
- **S2.** La plataforma tiene un módulo de administración de usuarios y guarda un registro de ingresos (quién entró y cuándo).
- **S3.** Gestión Humana y la coordinación de franquicias tienen las fechas de retiro del personal y de las franquicias.
- **S4.** Los listados se pueden exportar directamente del sistema.
- **S5.** El periodo de abril a septiembre de 2026 está cerrado y sus datos están completos.

**Información por solicitar:**

- Política o procedimiento de bajas, con fecha, versión y plazo.
- Política de revisión de accesos y su periodicidad.
- Procedimiento de aviso de salida de personal y de desvinculación de franquicias.
- Listado de retiros del periodo, con fechas.
- Listado de cuentas con estado y fecha de desactivación.
- Registros de último ingreso de cada cuenta de la muestra.
- Captura de la configuración de usuarios de la plataforma.
- Actas de las revisiones periódicas de cuentas.
- Listados de personal y de franquicias vigentes al 30 de septiembre de 2026.

**Propuestas del equipo:**

- El objetivo de auditoría y el alcance (módulo de usuarios, periodo de abril a septiembre de 2026).
- Los criterios C1, C2 y C3. Los plazos y la periodicidad no son de ISO: los define la empresa y, si no existen, se proponen.
- Los procedimientos P1 y P2, incluido el cruce de cuentas activas al corte.
- La muestra aleatoria, con tamaño por definir al conocer la población real.
- El cronograma de 5 semanas.
- El control propuesto de la matriz: desactivar automáticamente la cuenta y revisar cada mes.

**Aclaración final:** todo lo de "información por solicitar" es evidencia esperada, no obtenida. Como no se ejecutó la revisión, este trabajo no contiene hallazgos, porcentajes de cumplimiento ni conclusiones sobre si el control funciona.
