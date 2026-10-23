# Taller 2: Matriz de Riesgos — Interrapidísimo

**Integrante:** Santiago Moscoso Rodríguez

---

## 1. Contexto actualizado

Interrapidísimo es una empresa colombiana de mensajería y paquetería que trabaja con una red de franquicias por todo el país. En este taller me enfoco en la plataforma de rastreo de envíos y en quién puede entrar a ella (franquicias y personal), incluyendo los datos de remitentes y destinatarios que guarda. La escogí porque ahí se juntan las tres preocupaciones del primer taller: proteger los datos personales (ISO/IEC 27001), que el rastreo no se caiga (ITIL) y que todas las franquicias trabajen igual (COBIT).

## 2. Supuestos

No tengo acceso a información interna de la empresa, así que lo que sigue son supuestos, no hechos comprobados. Cada uno se podría confirmar pidiendo la evidencia que aparece en la matriz.

- **S1.** Cada persona de una franquicia tiene su propia cuenta en la plataforma, pero no sé si alguien las revisa de vez en cuando.
- **S2.** Las franquicias pueden consultar más envíos de los que realmente procesan.
- **S3.** La plataforma se usa muchísimo más en temporadas altas (diciembre, ventas en línea).
- **S4.** Los computadores de las franquicias son de cada dueño y no hay un estándar mínimo que alguien verifique.
- **S5.** Para marcar un envío como "entregado" no se exige evidencia obligatoria (firma o foto).

## 3. Activos y procesos analizados

| # | Activo o proceso | Tipo |
|---|---|---|
| A1 | Cuentas de acceso de franquicias y personal a la plataforma | Información / acceso |
| A2 | Base de datos de remitentes y destinatarios (nombres, direcciones, teléfonos) | Información |
| A3 | Plataforma de rastreo de envíos | Aplicación |
| A4 | Computadores de las franquicias conectados al sistema central | Infraestructura |
| A5 | Proceso de actualizar el estado del envío en cada franquicia | Proceso |

## 4. Matriz de riesgos (de mayor a menor nivel)

**Escala usada:** Probabilidad: 1 raro … 5 muy probable. Impacto: 1 consecuencia menor … 5 afecta gravemente la operación, datos críticos o cumplimiento. **Nivel** = probabilidad × impacto.

### R1 — Cuentas activas después del retiro

| Campo | Detalle |
|---|---|
| Activo o proceso | A1. Cuentas de acceso a la plataforma |
| Amenaza | Alguien que ya no trabaja en la franquicia (o una franquicia que se desvinculó) intenta entrar a la plataforma |
| Vulnerabilidad | Las cuentas siguen activas después del retiro y nadie las revisa de forma periódica |
| Riesgo | Un exempleado de una franquicia entra, mira datos de envíos y los usa para estafar a destinatarios. La empresa termina con una fuga de datos personales, quejas y posibles problemas legales |
| Probabilidad | **4** — en los puntos de servicio hay mucha rotación de personal, y sin revisión las cuentas viejas se van acumulando |
| Impacto | **4** — se exponen datos personales de varios usuarios |
| **Nivel** | **16** |
| Control actual | Supongo que no hay revisión. Evidencia a pedir: lista de cuentas activas vs. personal vigente |
| Control propuesto | Que la cuenta se desactive sola cuando termine el contrato o vínculo, y revisar cada mes las cuentas activas sin vínculo vigente, dejando un acta firmada |
| Prioridad | La más alta: es fácil de aprovechar y la consecuencia (fuga de datos) es grave. Marco: ISO/IEC 27001 |

### R2 — Franquicias que ven más de la cuenta

| Campo | Detalle |
|---|---|
| Activo o proceso | A2. Base de datos de remitentes y destinatarios |
| Amenaza | Un empleado de una franquicia, por curiosidad o mala intención, busca envíos que no le tocan |
| Vulnerabilidad | Los permisos son muy amplios: la franquicia puede consultar envíos que ella no procesó |
| Riesgo | Un empleado copia datos de envíos ajenos y los vende o los usa para molestar a alguien; la empresa pierde la confianza de sus clientes |
| Probabilidad | **3** — es posible, porque hay muchísima gente con acceso |
| Impacto | **5** — son datos personales de muchos usuarios y se arriesga a incumplir la norma de protección de datos |
| **Nivel** | **15** |
| Control actual | Supongo que no hay límite por franquicia. Evidencia a pedir: tabla de perfiles y permisos |
| Control propuesto | Crear perfiles por rol para que cada franquicia solo vea los envíos que registró o recibió, guardar un registro de cada consulta y revisar cada trimestre las consultas raras (por ejemplo, más de 100 en un solo día) |
| Prioridad | Muy alta por su impacto: un solo caso puede afectar a muchos clientes. Marco: ISO/IEC 27001 |

### R3 — Caída del rastreo en temporada alta

| Campo | Detalle |
|---|---|
| Activo o proceso | A3. Plataforma de rastreo de envíos |
| Amenaza | Un aumento fuerte de consultas en temporada alta o una falla técnica del servidor |
| Vulnerabilidad | No se conoce un servidor de respaldo ni alertas automáticas cuando algo se cae |
| Riesgo | La plataforma se cae varias horas en diciembre; los clientes no pueden rastrear, se llenan las líneas de reclamos y las franquicias no pueden registrar entregas |
| Probabilidad | **3** — las temporadas altas se saben con tiempo y ponen el sistema a prueba |
| Impacto | **4** — se interrumpe un servicio importante en todo el país |
| **Nivel** | **12** |
| Control actual | No lo sé. Evidencia a pedir: reporte mensual de disponibilidad y registro de caídas |
| Control propuesto | Poner monitoreo con alertas automáticas, medir la disponibilidad cada mes con una meta y hacer una prueba con servidor de respaldo antes de cada temporada alta |
| Prioridad | Alta: afecta el servicio completo, aunque dura poco tiempo. Marco: ITIL |

### R4 — Computadores de franquicia sin estándar mínimo

| Campo | Detalle |
|---|---|
| Activo o proceso | A4. Computadores de las franquicias conectados al sistema central |
| Amenaza | Un virus que roba contraseñas desde un computador de franquicia |
| Vulnerabilidad | No hay requisitos mínimos que alguien verifique (antivirus, actualizaciones, una cuenta por persona) |
| Riesgo | Un computador infectado en una franquicia entrega la contraseña de un usuario, un atacante entra a la plataforma y accede a datos sin permiso |
| Probabilidad | **3** — hay miles de equipos y cada dueño los cuida distinto |
| Impacto | **4** — puede dejar expuesta información sensible de varios usuarios |
| **Nivel** | **12** |
| Control actual | Supongo que no existe un estándar verificado. Evidencia a pedir: manual de requisitos para franquicias |
| Control propuesto | Publicar un manual de requisitos mínimos (antivirus activo, actualizaciones al día, cuenta individual por persona), pedir un chequeo anual firmado por cada franquicia y auditar una muestra cada año |
| Prioridad | Alta: un solo equipo descuidado abre la puerta a toda la plataforma. Marco: COBIT |

### R5 — Envíos marcados como entregados sin serlo

| Campo | Detalle |
|---|---|
| Activo o proceso | A5. Proceso de actualizar el estado del envío |
| Amenaza | Un error humano o alguien que cambia el estado a propósito |
| Vulnerabilidad | Marcar "entregado" no exige evidencia obligatoria y no se revisan los casos raros |
| Riesgo | Una franquicia marca como entregado un paquete que nunca llegó; el cliente reclama, la empresa le responde con información falsa y termina pagando indemnizaciones |
| Probabilidad | **4** — con tantos puntos y tanto volumen, los errores y las malas prácticas se van a ver seguido |
| Impacto | **3** — afecta a varios clientes y genera reclamos, pero no frena todo el servicio |
| **Nivel** | **12** |
| Control actual | Supongo que no hay evidencia obligatoria. Evidencia a pedir: ejemplos de entregas cerradas y su soporte |
| Control propuesto | Exigir firma o foto para cerrar un envío como entregado y sacar cada semana un reporte de envíos con tiempos raros para que lo revise auditoría interna |
| Prioridad | Media-alta: pasa seguido, pero pesa menos que los riesgos de datos. Marco: COBIT / ITIL |

## 5. Resumen de prioridades

| Orden | Riesgo | Nivel |
|---|---|---|
| 1 | R1 — Cuentas activas después del retiro | 16 |
| 2 | R2 — Franquicias que ven más de la cuenta | 15 |
| 3 | R3 — Caída del rastreo en temporada alta | 12 |
| 4 | R4 — Computadores de franquicia sin estándar mínimo | 12 |
| 5 | R5 — Envíos marcados como entregados sin serlo | 12 |