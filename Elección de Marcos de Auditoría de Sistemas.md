# **Elección de Marcos de Auditoría de Sistemas** 

**Santiago Moscoso Rodríguez** 

## **1. Organización elegida** 

Interrapidísimo, empresa colombiana de mensajería y paquetería, líder en el país en número de envíos individuales. Opera a través de una amplia red de franquicias en más de 1.100 municipios de Colombia, con flota propia y una plataforma tecnológica de rastreo de envíos. 

## **2. Contexto** 

Interrapidísimo se dedica al transporte y entrega de paquetes, documentos y mercancías dentro de Colombia (y cada vez más hacia el exterior, apoyando comercio electrónico). Su sistema de información principal es la plataforma de rastreo de envíos, usada tanto por el personal interno como por los clientes para ver en qué punto está su paquete, además de las bases de datos con direcciones y datos personales de remitentes y destinatarios. Al operar por medio de una red de miles de franquicias independientes, la empresa también depende de que cada punto use correctamente los sistemas centrales. Sus principales preocupaciones son: seguridad de los datos personales de millones de envíos que maneja al año, disponibilidad del sistema de rastreo y de las operaciones logísticas a nivel nacional, y que la información y los procesos se manejen de forma consistente en toda la red de franquicias, no solo en la sede central. 

## **3. Marcos elegidos y orden** 

1. ISO/IEC 27001 

2. ITIL 

3. COBIT 

## **4. Justificación** 

### ISO/IEC 27001 

Este marco se enfoca en la seguridad de la información: cómo se protegen los datos, quién puede acceder a ellos y qué se hace si hay una fuga o un ataque. Para Interrapidísimo, este es el riesgo más urgente porque maneja datos personales (nombres, direcciones, contenido) de millones de remitentes y destinatarios cada año, distribuidos entre la sede central y miles de franquicias. Si esta información se filtra, se pierde o es mal usada, el daño no es solo económico: hay un problema legal y de confianza, que en una empresa que vive de que la 

gente le confíe sus envíos es especialmente grave. Por eso va primero: antes de evaluar qué tan bien funciona el servicio, hay que asegurar que la información que lo sostiene esté protegida. 

### ITIL 

ITIL se enfoca en cómo se gestionan los servicios de TI: disponibilidad, atención de fallas, mejora continua. Para esta empresa, el sistema de rastreo de envíos es una parte central del servicio: si se cae o entrega información errada, se pierde la confianza del cliente y se generan reclamos, aunque el paquete físicamente sí se esté moviendo. Una vez protegida la información, el siguiente riesgo más importante es que ese sistema esté disponible y que, cuando algo falle, haya un proceso claro para solucionarlo rápido en todo el país. Por eso va segundo: complementa la seguridad con la operación diaria del servicio. 

### COBIT 

No se elige como marco principal porque su enfoque es más amplio, pero se vuelve relevante en este caso por un riesgo particular: Interrapidísimo opera a través de miles de franquicias independientes, y no basta con que la sede central tenga buenas prácticas de seguridad y servicio si cada franquicia usa los sistemas de forma distinta. COBIT ayuda a revisar si existen reglas claras, desde la dirección de la empresa, para que todos los puntos sigan los mismos estándares de TI. 

## **5. Evidencia propuesta por marco** 

### ISO/IEC 27001 

- **Política de seguridad de la información y control de accesos:** documento donde se defina quién puede ver o modificar los datos de los envíos. Por ejemplo, que un punto de franquicia solo vea la información de los paquetes que procesa, no la de todo el país. 

- **Registro de incidentes de seguridad:** historial de eventos como accesos no autorizados, pérdida de información o alertas de seguridad detectadas, junto con cómo se resolvieron. 

### ITIL 

- **Registro de incidentes del servicio:** reporte de caídas del sistema de rastreo, información de envíos que no se actualiza a tiempo, con el tiempo que tomó resolver cada caso. 

- **Acuerdo de nivel de servicio o métricas de disponibilidad:** documento o reporte que muestre el porcentaje de tiempo que la plataforma de rastreo estuvo funcionando en un periodo determinado. 

### COBIT 

- **Manual o guía de estándares de TI para franquicias:** documento que defina qué software, equipos o procesos mínimos debe tener cada punto de franquicia para conectarse al sistema central. 

- **Reporte de auditorías internas a franquicias:** evidencia de que la empresa revisa periódicamente si las franquicias están cumpliendo esos estándares y no que solo confían en que lo hagan. 

