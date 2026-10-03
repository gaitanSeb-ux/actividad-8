# actividad-8
# Parte 1: Blockchain y Criptografía
1. Cadena de bloques con mensajes entre dos servidores (Paso a paso)
Para implementar una cadena de bloques funcional con transferencia de mensajes, se puede desarrollar un script básico en Python utilizando sockets y hashing criptográfico (SHA-256).
Paso 1: Definir la estructura del bloque
Cada bloque contiene un índice, una marca de tiempo (timestamp), el mensaje enviado, el hash del bloque anterior (previous_hash) y su propio hash único (hash).
Paso 2: Función de minería/creación de bloque
¿Cómo se crea un bloque? Se toman los datos del mensaje actual y se concatenan con el hash del bloque anterior. Luego se aplica una función criptográfica (SHA-256) para generar una cadena hexadecimal única. Si el sistema requiere una dificultad (como PoW - Proof of Work), se busca un "nonce" hasta que el hash cumpla con ciertas condiciones.
Paso 3: Comunicación entre Servidores (Sockets)

Servidor Emisor: Crea el mensaje, lo empaqueta en un bloque, calcula su hash y lo transmite a través de un socket TCP/IP al servidor receptor.

Servidor Receptor: Escucha en un puerto específico, recibe el bloque, verifica que el previous_hash coincida con el hash del último bloque de su registro local para garantizar la integridad, y si es válido, lo añade a su cadena (blockchain).
2. Tipo de encriptación en Blockchain y funcionamiento
¿Qué tipo de encriptación se maneja?
Blockchain utiliza principalmente criptografía simétrica y asimétrica (de llave pública/privada), además de funciones hash criptográficas (como SHA-256 y Keccak-256).
Cómo funciona?

Claves Asimétricas: Cada usuario posee una clave privada (firma digital) y una clave pública (su dirección en la red). La clave privada se usa para firmar transacciones de forma incuestionable, demostrando su autoría sin revelar la clave.

Hashing (SHA-256): Convierte cualquier bloque de datos en una cadena de caracteres de longitud fija. Es una función unidireccional (irreversible): cualquier modificación mínima en el mensaje original cambia por completo el hash resultante, garantizando la inmutabilidad.
3. Funcionamiento de una cadena de bloques en una transacción bancaria
Inicio: Un usuario solicita realizar una transferencia de dinero (transacción).

Transmisión: La transacción se transmite a una red peer-to-peer (P2P) compuesta de nodos (servidores bancarios/participantes).

Validación: Los nodos validan la transacción comprobando las firmas digitales y los saldos mediante las reglas del protocolo.

Agrupación: Las transacciones válidas se agrupan en un nuevo bloque de datos.

Consenso: Los nodos ejecutan un algoritmo de consenso (por ejemplo, Proof of Stake o Proof of Work) para acordar la validez del bloque.

Encadenamiento: Una vez aprobado, el bloque se enlaza criptográficamente al bloque anterior mediante su hash, registrándose de manera permanente e inalterable en el libro mayor (ledger).
. Comportamiento de Blockchain ante la computación cuántica y Computación Cuántica
¿Cómo se comporta ante la computación cuántica?
Los algoritmos cuánticos (como el Algoritmo de Shor) tienen el potencial de factorizar números grandes y resolver logaritmos discretos mucho más rápido que las computadoras clásicas. Esto pone en riesgo la criptografía asimétrica actual (como las firmas ECDSA utilizadas en Bitcoin/Ethereum), ya que una computadora cuántica suficientemente potente podría derivar una clave privada a partir de una clave pública. Las funciones hash (SHA-256) son más resistentes, pero requerirían duplicar su tamaño para mantenerse seguras (Algoritmo de Grover). Por ello, la comunidad estudia migrar hacia criptografía post-cuántica.

¿Qué es la computación cuántica?
Es un paradigma de computación basado en la mecánica cuántica que utiliza qubits (bits cuánticos) en lugar de bits clásicos (0 o 1). Gracias a los fenómenos de superposición (estar en múltiples estados a la vez) y entrelazamiento, pueden procesar volúmenes masivos de datos simultáneamente.

Tipo de seguridad que utiliza:
Emplea principios físicos y criptográficos avanzados. Destaca la Distribución Cuántica de Claves (QKD - Quantum Key Distribution), donde cualquier intento de intercepción altera el estado cuántico de los fotones, alertando inmediatamente a los usuarios.
| Tipo de Seguridad | Descripción | Aplicación Principal |
| :--- | :--- | :--- |
| **Criptografía Simétrica** | Usa una sola clave secreta compartida para cifrar y descifrar (ej. AES). | Encriptación de bases de datos y almacenamiento seguro. |
| **Criptografía Asimétrica** | Usa un par de claves: pública (cifra) y privada (descifra) (ej. RSA, ECC). | Firmas digitales, intercambio seguro de claves y autenticación. |
| **Funciones Hash** | Algoritmos unidireccionales que generan una huella digital única de un archivo. | Integridad de datos, contraseñas y bloques de Blockchain. |
| **Seguridad Cuántica (QKD)** | Seguridad basada en las leyes de la física cuántica para detectar escuchas. | Canales de comunicación gubernamentales y financieros de ultra-alta seguridad. |
