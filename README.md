# ElectronicVoting

 
El voto electrónico (también conocido como voto electrónico ) es un voto que utiliza medios electrónicos para ayudar o encargarse de emitir y contar los votos. Dependiendo de la implementación particular, el voto electrónico puede usar máquinas de votación electrónica independientes (también llamadas EVM) o computadoras conectadas a Internet. Puede abarcar una variedad de servicios de Internet , desde la transmisión básica de resultados tabulados hasta la votación en línea con todas las funciones a través de dispositivos domésticos conectables comunes. El grado de automatización puede limitarse al marcado de una boleta en papel, o puede ser un sistema integral de entrada de votos, registro de votos, encriptación y transmisión de datos a servidores, y consolidación y tabulación de resultados electorales. Un sistema de voto electrónico digno debe realizar la mayoría de estas tareas al mismo tiempo que cumple con un conjunto de estándares establecidos por los organismos reguladores, y también debe ser capaz de hacer frente con éxito a los estrictos requisitos asociados con la seguridad , precisión , integridad, rapidez, privacidad , auditabilidad y accesibilidad. , rentabilidad , escalabilidad y sostenibilidad ecológica . La tecnología de votación electrónica puede incluir tarjetas perforadas , sistemas de votación de escaneo óptico y quioscos de votación especializados (incluidos los sistemas de votación electrónicos autónomos de grabación directa , o DRE). También puede implicar la transmisión de papeletas y votos a través de teléfonos, redes informáticas privadas o Internet .

# Esta plataforma se ha diseñado con todas las garantías:

Votación electrónica supervisada físicamente por representantes de autoridades electorales gubernamentales o independientes (por ejemplo, máquinas de votación electrónica ubicadas en los colegios electorales);
Voto electrónico remoto a través de Internet (también llamado i-vote) donde el votante envía su voto electrónicamente a las autoridades electorales, desde cualquier lugar

- **Esta plataforma se ha diseñado con todas las garantías:**

- **Garantía de legitimidad del votante** (“solamente vota quien está autorizado”).

- **Garantía de privacidad:** la relación entre votante y voto no puede ser conocida ni puede ser deducida.

- **Garantía de corrección:** el resultado debe proceder exactamente de los votos emitidos de manera legítima. Solamente los votos válidos                                 procedentes de votantes legítimos deben ser tenidos en cuenta. Por tanto, se evitan votos duplicados, no                                     válidos, etc.

- **Garantía de integridad:** se utilizan métodos de seguridad de última generación que evitan cualquier intento de manipulación de los votos.

- **Garantía de verificación personal del voto:** el votante puede verificar que su voto ha sido correctamente recibido.

- **Garantía de verificación universal del voto:** cualquier participante u observador debe poder verificar los resultados de la votación.

- **Garantía de fiabilidad:** el sistema está preparado contra ataques externos, fallos tecnológicos y ataques contra la privacidad de los votantes.

# EVALUACIÓN DE CALIDAD 

- Análisis del código fuente de la aplicación, para comprobar que no contiene código malicioso.

- Análisis del diseño y estructura de la base de datos para comprobar aspectos como la privacidad y la legitimidad.

- Comprobación del sistema empleado para almacenar y salvaguardar el censo de votantes.

- Análisis de las medidas de seguridad lógica empleadas: de qué forma asegura el sistema la legitimidad, privacidad, corrección e integridad, qué herramientas criptográficas y de seguridad utiliza.

- Análisis del control de acceso a todos los elementos del sistema (Bases de datos, claves, servidores, etc).

- Comprobación de seguridad física.

- Análisis de las posibles vulnerabilidades de los medios utilizados por los votantes.

- Comprobación del sistema empleado para la realización y publicación del escrutinio (resultado de la votación).

- Prueba completa del sistema: realización de varias votaciones de prueba e intentos de ataque al sistema para comprometer su fiabilidad (ataques DoS, suplantación de identidad, etc). Las pruebas se han hecho verificando todas las fases de la votación: desde la comprobación del censo, pasando por la fase de voto (autenticación, votación, verificación) y terminando por la fase de recuento o escrutinio y verificación de resultados.

El resultado final ha sido totalmente satisfactorio, consiguiendo la máxima puntuación (5 sobre 5).


# DESCRIPCIÓN

El sistema de votación está basado en dos aplicaciones independientes:

- La aplicación de voto

- La aplicación de administración de las votaciones.

La aplicación de voto sirve para identificar al votante, mostrar las votaciones accesibles a su Matricula y seleccionar las opciones a votar en una votación concreta. Una vez realizada la selección, le pasa el control a la aplicación de administración que es la encargada de validar el voto seleccionado y al votante (firma electrónica) y realizar la grabación del voto en las bases de datos.





# Proceso de voto
Una vez el usuario ha realizado su selección de voto en la aplicación de votación, el sistema comprueba la validez del Matricula comprobando que está entre los censados de la votación y que no ha realizado ya el voto en esta votación. También se comprueba que se encuentre dentro del periodo de votaciones indicado en los parámetros de la votación.

A continuación, se realizará la comprobación de la identidad de la persona que está haciendo el proceso, de dos posibles maneras:

CÓDIGO SMS: Si la votación no está marcada como firma electrónica, se envía un código aleatorio de 6 caracteres al teléfono móvil registrado en el censo de la votación para el Matricula indicado. Si el usuario teclea correctamente el código enviado, la identificación se da por satisfactoria.

**FIRMA ELECTRÓNICA:** Si la votación está marcada como firma electrónica, al usuario se le pedirá que seleccione un certificado de firma electrónica. Se comprobará la validez de la firma, caducidad, revocación, etc., y se comprobará que el Matricula asociado a la firma electrónica es el correspondiente al usuario que está realizando la votación. Si todo este proceso es correcto, la identificación se da por satisfactoria.

La aplicación de administración lee los datos del voto y a continuación realiza las siguientes acciones:

- **OBTENCIÓN DEL SELLO DE TIEMPO:** Se conecta online con la TSA correspondiente y obtiene el sello de tiempo. La TSA devuelve el sello de tiempo y su número de serie único que son almacenados en la base de datos para su posterior utilización y control.

- **GRABACIÓN DEL VOTO:** El proceso de grabación del voto en la base de datos se basa en varios procesos en cadena ejecutados todos como una única transacción. La información se almacena de forma encriptada. Se marca en el censo de la votación que el votante a realizado el voto, indicando el sello de tiempo asociado, y los datos técnicos de la firma electrónica si es que el proceso se realizó en esta.

- **GENERACIÓN DEL CERTIFICADO DE VOTACIÓN:** Se generará un certificado en PDF con la información de la votación y la realización del voto, indicando a su vez un código de verificación de dicha votación a través de una página pública de la plataforma. El certificado emitido está firmado electrónicamente.

- **ENVÍO DE COMUNICACIÓN DE VOTO A LOS AUDITORES:** Si en la votación está marcada la opción de enviar comunicación de voto realizado a los interventores, se enviará un correo a todos los interventores registrados y que tengan marcado en su perfil la opción de recibir correo con la votación.

- ENVÍO DE COMUNICACIÓN DE VOTO AL VOTANTE: Se enviará un correo electrónico y un SMS al votante indicando que se ha realizado la votación.

# ADMINISTRACIÓN DE UNA VOTACIÓN

Un administrador podrá:

- Cambiar datos de la cuenta, logotipos, nombres, datos de contacto … Esta información se mostrará en la pantalla de votaciones, listados, certificaciones o comunicaciones que envíe la plataforma.

- **Preferencias de las votaciones**: idioma, colores, fondos, imagen con icono.

- **Listas de votaciones:** definir fechas de inicio y fin del periodo de votaciones, los puntos a votar, las opciones dentro de cada punto, la ordenación de las opciones, valores mínimos y máximos para el nº de opciones a votar por cada punto, imagen asociada, etc. Se dispondrá de una opción para previsualizar la votación, que permite ver el aspecto que tendrá en pantalla la votación que se está diseñando.

- **Censo electoral:** Se puede cargar el censo bien manualmente (uno a uno), o importando los datos desde un fichero de Excel.

- **Administrar interventores:** personas autorizadas a recibir información sobre el proceso de votación. Pueden recibir, cada vez que se realice una votación, una comunicación indicando los datos del votante (nombre y Matricula) y el momento de la votación.

- **Controles de auditoría:** comprobaciones de votos nulos, perdidos, etc.

- **Obtención de resultados:** Sólo cuando ha finalizado la votación. El sistema emite un certificado de resultados en un PDF firmado electrónicamente y con sello de tiempo. Contiene datos numéricos y de porcentajes, gráficos de tarta y de barras.
