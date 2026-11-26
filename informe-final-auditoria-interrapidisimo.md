# Informe de auditoría: cuentas activas después del retiro en Interrapidísimo

Integrante: Santiago Moscoso Rodríguez

Tipo de ejercicio: prueba con datos simulados. Nada de lo que aparece en las tablas de resultados describe a Interrapidísimo.

---

## 1. Identificación y resumen ejecutivo

### Equipo y caso

Este informe lo hice de forma individual. El caso es Interrapidísimo, una empresa colombiana de mensajería y paquetería que trabaja con una red de franquicias por todo el país. Según Portafolio, tiene más de 3.000 franquicias y llega a 1.103 municipios. El sistema que analizo es su plataforma de rastreo de envíos, que usan tanto el personal propio como las franquicias, y que guarda datos personales de quien envía y quien recibe.

### Riesgo revisado

Es el riesgo R1, cuentas activas después del retiro, con nivel 16 en la matriz (probabilidad 4 por impacto 4).

| Elemento | Detalle |
|---|---|
| Activo | Las cuentas de acceso de franquicias y de personal propio a la plataforma de rastreo |
| Amenaza | Alguien que ya no trabaja en la franquicia, o una franquicia que se desvinculó, intenta entrar a la plataforma |
| Vulnerabilidad | La cuenta sigue activa después del retiro y nadie la revisa de forma periódica (esto último es un supuesto, no un hecho comprobado) |
| Riesgo | Un exempleado entra, consulta datos de envíos y los usa para estafar a destinatarios. La empresa termina con una fuga de datos personales, quejas y posibles problemas legales |
| Por qué probabilidad 4 | En los puntos de servicio hay mucha rotación de personal y, sin revisión, las cuentas viejas se van acumulando |
| Por qué impacto 4 | Se exponen datos personales de varios usuarios, aunque no se detiene toda la operación |
| Control propuesto en la matriz | Desactivar la cuenta cuando termina el vínculo y revisar cada mes las cuentas activas sin vínculo vigente, dejando un acta firmada |

### Resultado principal

Se revisó una muestra simulada de 10 cuentas. En 7 la desactivación se hizo dentro del plazo y en 3 hubo excepciones: dos cuentas se cerraron con 7 días de demora, y una sigue activa y registra un ingreso 3 días después del retiro.

### Aviso importante

No tengo acceso a información interna de Interrapidísimo, así que los datos de la prueba y la regla de plazo son inventados para el ejercicio y están marcados como simulados. Los resultados muestran cómo se haría la prueba y cómo se escribiría un hallazgo. No dicen nada sobre cómo trabaja la empresa en la realidad.

## 2. Objetivo y alcance

### Objetivo

Determinar si las cuentas de acceso a la plataforma de rastreo, tanto de franquicias como de personal propio, se desactivan dentro del plazo establecido cuando termina el vínculo de la persona, durante los últimos seis meses.

### Alcance

| Elemento | Definición |
|---|---|
| Proceso | Baja de usuarios: desactivar las cuentas cuando termina el vínculo |
| Sistema | La plataforma de rastreo de envíos, solo el módulo de administración de usuarios y el registro de ingresos (quién entró y cuándo) |
| Población | 40 retiros simulados de personal propio y de franquicias |
| Periodo | Del 1 de abril al 30 de septiembre de 2026 |
| Áreas que explicarían el proceso o guardarían la evidencia | TI (Tecnologías de la Información, el área que administra los sistemas), Gestión Humana y la coordinación de franquicias |

### Exclusiones

- Otros sistemas de la empresa, como facturación o correo, porque el riesgo trata de la plataforma de rastreo.
- Cuentas de clientes finales, porque el control revisado es el de personal y franquicias.

### Lo que no se ejecutó

El plan original tenía otro paso: cruzar las cuentas que siguen activas al 30 de septiembre con el personal vigente, para encontrar cuentas de gente que se fue y nadie reportó. Ese paso no se hizo en esta prueba. Por eso la prueba solo puede ver retiros que alguien reportó.

## 3. Criterios y metodología

### Qué debería ocurrir

Para la prueba usé una regla ficticia: según un procedimiento de bajas de acceso inventado para este ejercicio, toda cuenta se desactiva a más tardar 2 días calendario después de la fecha en que termina el vínculo.

Como apoyo general uso ISO/IEC 27001, en las partes que hablan de derechos de acceso y de responsabilidades cuando alguien termina su vínculo. Esa norma dice que los accesos deben retirarse al terminar el vínculo, pero no fija cuántos días, así que el plazo de 2 días no se le atribuye a ella.

### Procedimiento

Usé el procedimiento del plan que revisa si el control se cumple en la práctica:

1. Tomar el listado de retiros del periodo con su fecha (en una auditoría real lo darían Gestión Humana y la coordinación de franquicias).
2. Tomar el listado de cuentas con su fecha de desactivación (en una auditoría real lo exportaría TI directamente del sistema).
3. Cruzar los dos listados y calcular, por cada retiro, los días entre el retiro y la desactivación.
4. Revisar el último ingreso de cada cuenta para ver si alguien entró después de la fecha de retiro.
5. Anotar cada excepción con la cuenta, las fechas y los días de demora.

Se considera excepción cuando pasan más de 2 días entre el retiro y la desactivación, cuando la cuenta sigue activa, o cuando hay un ingreso después de la fecha de retiro.

### Muestra

La población simulada es de 40 retiros. En una auditoría real se numerarían y se sortearían 10 con números aleatorios en una hoja de cálculo, para no escoger solo los casos que se ven bien. Como aquí los datos son simulados, la muestra de 10 cuentas se armó como ejemplo de lo que saldría de ese sorteo, mezclando personal propio y franquicias.

### Evidencia examinada

Los listados simulados de retiros y de cuentas, con sus fechas y su último ingreso, que se muestran en la tabla de la siguiente sección.

## 4. Resultados y hallazgos

### Datos de la prueba (simulados)

| Cuenta | Tipo | Retiro | Desactivación | Días | Último ingreso | Resultado |
|---|---|---|---|---|---|---|
| P-03 | Personal propio | 6 abr | 6 abr | 0 | 3 abr | Dentro del plazo |
| F-12 | Franquicia | 14 abr | 15 abr | 1 | 14 abr | Dentro del plazo |
| F-27 | Franquicia | 2 may | 9 may | 7 | 2 may | Excepción |
| P-08 | Personal propio | 19 may | 19 may | 0 | 18 may | Dentro del plazo |
| F-31 | Franquicia | 3 jun | 5 jun | 2 | 3 jun | Dentro del plazo |
| F-05 | Franquicia | 17 jun | Sigue activa | no aplica | 20 jun | Excepción grave |
| P-11 | Personal propio | 1 jul | 2 jul | 1 | 30 jun | Dentro del plazo |
| F-19 | Franquicia | 22 jul | 22 jul | 0 | 21 jul | Dentro del plazo |
| F-40 | Franquicia | 11 ago | 18 ago | 7 | 11 ago | Excepción |
| P-14 | Personal propio | 9 sep | 10 sep | 1 | 9 sep | Dentro del plazo |

En esta muestra simulada, 7 de 10 cuentas se desactivaron dentro del plazo y 3 son excepciones. De esas 3, F-27 y F-40 se cerraron con 7 días de demora, y F-05 sigue activa y registra un ingreso 3 días después del retiro.

### Hallazgo H1: cuentas desactivadas fuera del plazo

| Componente | Pregunta | Detalle |
|---|---|---|
| Criterio | ¿Qué debía ocurrir? | Desactivar la cuenta a más tardar 2 días calendario después del retiro, según el procedimiento de bajas ficticio |
| Condición | ¿Qué observamos? | En 2 de las 10 cuentas de la muestra (F-27 y F-40) la desactivación se hizo 7 días después del retiro, 5 días por encima del plazo. En las otras 7 cuentas desactivadas, el plazo se cumplió |
| Causa | ¿Por qué ocurrió? | Pendiente de confirmar. La prueba no lo establece. Una hipótesis para verificar es que el aviso del retiro llegó tarde desde la franquicia, porque las dos cuentas son de franquicias, pero no se probó |
| Efecto o riesgo | ¿Qué ocurrió o podría ocurrir? | Las cuentas quedaron disponibles unos días más de lo permitido, tiempo en el que podrían haberse usado para un acceso no autorizado. En los datos de la muestra, el último ingreso de ambas fue el día del retiro, así que no se observó uso posterior |
| Recomendación | ¿Qué podría hacerse? | Revisar el flujo entre el aviso de retiro y la desactivación para ubicar dónde se pierden esos 7 días, y dar seguimiento mensual a las cuentas desactivadas fuera de plazo |

### Hallazgo H2: cuenta sin desactivar con un ingreso posterior al retiro

| Componente | Pregunta | Detalle |
|---|---|---|
| Criterio | ¿Qué debía ocurrir? | Desactivar la cuenta a más tardar 2 días después del retiro y que no haya ingresos después de esa fecha |
| Condición | ¿Qué observamos? | La cuenta F-05 (retiro el 17 de junio) seguía activa al cierre del periodo revisado y registra un ingreso el 20 de junio, 3 días después del retiro |
| Causa | ¿Por qué ocurrió? | Pendiente de confirmar. La prueba no lo establece. Podría ser que la baja nunca se ejecutó o que nunca se avisó la salida, pero no hay evidencia de cuál fue |
| Efecto o riesgo | ¿Qué ocurrió o podría ocurrir? | Se registró un ingreso a una cuenta de alguien que ya no tenía vínculo. Si lo hizo la persona retirada u otra no autorizada, se habría accedido a datos de envíos sin permiso. |
| Recomendación | ¿Qué podría hacerse? | Desactivar la cuenta de inmediato, revisar desde dónde fue el ingreso y qué consultó, y revisar toda la población en busca de otras cuentas con ingresos posteriores al retiro |

### Qué podemos afirmar y qué no

| Con soporte | Sin soporte (haría falta más evidencia) |
|---|---|
| En 2 de las 10 cuentas simuladas se observó una desactivación 7 días después del retiro | El 20 % de las cuentas se gestiona mal (10 cuentas no representan a toda la población) |
| En la cuenta simulada F-05 se registró un ingreso 3 días después del retiro | El exempleado ingresó al sistema (el registro muestra un ingreso a la cuenta, no quién fue) |
| Las 3 excepciones de la muestra corresponden a cuentas de franquicias | Las franquicias son el origen del problema (es una muestra pequeña y la causa no se probó) |

## 5. Conclusión y limitaciones

### Conclusión

En esta muestra simulada de 10 cuentas, el control de desactivar las cuentas a tiempo no se cumplió en 3 casos: dos cierres con 7 días de demora y una cuenta que sigue activa y tuvo un ingreso después del retiro. Como la prueba es simulada, la conclusión sirve para mostrar cómo se llegaría a un hallazgo con evidencia, no para opinar sobre la empresa.

### Limitaciones

- Los datos y la regla de 2 días son ficticios, así que nada de esto describe a Interrapidísimo.
- La muestra es pequeña, por lo que no permite sacar porcentajes de toda la población.
- La causa de las demoras no se probó.
- El ingreso a F-05 no dice quién entró, solo que la cuenta se usó.
- La prueba parte de retiros reportados. No detecta cuentas de personas que se fueron sin que nadie avisara, que era el paso del plan que no se ejecutó.

### Qué quedaría pendiente en una auditoría real

Pedir la política de bajas vigente y confirmar su plazo, recibir los listados reales de retiros y de cuentas exportados del sistema, definir el tamaño de la muestra con la población real, y ejecutar el cruce de cuentas activas contra el personal vigente.

## 6. Plan de acción y anexos

### Plan de acción

Es una propuesta sobre datos simulados, sujeta a acuerdo con la organización. Como H1 y H2 fallan en el mismo tramo del proceso, entre que se avisa el retiro y se desactiva la cuenta, se atienden con una sola acción.

| Campo | Detalle |
|---|---|
| Hallazgos que atiende | H1 (cuentas desactivadas fuera del plazo) y H2 (cuenta sin desactivar con un ingreso posterior al retiro) |
| Acción propuesta | Corregir el proceso de baja de punta a punta, desde el aviso del retiro hasta la desactivación. Incluye: (1) desactivar de inmediato las cuentas pendientes (F-05) y revisar desde dónde fue su ingreso y qué consultó; (2) confirmar la causa de las demoras, que la prueba no estableció; (3) fijar por escrito el plazo y quién responde en cada paso; (4) dar seguimiento mensual a las cuentas activas sin vínculo vigente, como propone el control de la matriz |
| Responsable propuesto | Responsable de gestión de accesos de TI, con apoyo de Gestión Humana y de la coordinación de franquicias |
| Prioridad | Alta. H2 ya muestra un ingreso a una cuenta de alguien retirado y H1 es la misma falla en menor grado |
| Plazo propuesto | Paso 1: 5 días hábiles. Pasos 2 a 4: 30 días. Sujeto a acuerdo con la organización |
| Evidencia de cierre | Registro de la desactivación de F-05 y de la revisión de su ingreso, procedimiento de bajas actualizado con plazo y responsables, y una prueba posterior con el mismo procedimiento sobre una muestra nueva |