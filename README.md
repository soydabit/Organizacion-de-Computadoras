# Organizacion-de-Computadoras
Este repositorio contiene material de la cursada de OC, en pricipio tiene un resumen de lo que estudie y consulte con profesores de teoria para el final de la materia.
# Preparando final de OC

# Horarios de consulta practica

[Apuntes consulta de final](https://www.notion.so/Apuntes-consulta-de-final-1faf0238bf2980b18645f11f88f664e2?pvs=21)

![image.png](image.png)

# Repaso final

- ***Punto Flotante***
    
    ### Error absoluto maximo y Error Relativo
    
    ![image.png](image%201.png)
    
- ***Semi-sumador y sumador completo***
    
    ## Semi-sumador
    
    El semisumador permite realizar la suma de dos bits `a` y `b` sin tener en cuenta un acarreo anterior. Esto es equivalente a una suma muy simple de dos bits binarios.
    
    Por ejemplo si queremos realizar la suma de los bits a y b tendremos 
    
    ```jsx
    bits de entrada o bits a sumar : A y B
    bits de salida o resultado de la suma: S y C(carry
    ```
    
    ![image.png](image%202.png)
    
    ## Sumador completo
    
    A diferencia del semi-sumador el sumador completo si considera el bit de acarreo en la entrada, es decir que podremos tener en la entrada el valor de bit de acarreo de la suma anterior.
    
    Expresandolo de la siguiente formas(ver de derecha a izquierda)
    
                                                                ←←←←←←←←← 
    
    ![image.png](image%203.png)
    
    ![image.png](image%204.png)
    
    Se puede crear un sumador de 4 bits conectando sumadores completos en serie de la siguiente forma
    
    mirandolo de izquirdad a derecha tendremos que `Cin` en el caso del primer sumador complet tendra valor 0 y el valor de `Cin` en el sumador completo 1 tendra el valor de `Cout` del sumador 0 , y asi hasta llegar al ultimo sumador .
    
    ![image.png](image%205.png)
    
    > Las tablas de ambos se crea haciedno un xor de las entradas, de forma mas facil, si en la entrada hay 1 imparares la salida(sumatoria) es 1, para el caso de carry out el valor se da al tener carry
    > 
- ***Suma de productos***
    
    
    El método de **suma de productos** consiste en construir una función lógica como una expresión booleana formada por la suma (OR) de términos producto (AND) que representan las combinaciones de entrada que generan una salida 1 en la tabla de verdad. Cada término producto incluye todas las variables, en forma directa o negada según el caso. Este método permite implementar circuitos combinacionales usando compuertas AND, OR y NOT
    
    ### Paso 1:
    
    para dar el ejempo puedo decidir la cantidad de varibles es decir podria usar (a,b) y podria decidir cuando F toma valor 1, para este ejemplo decido que `F=1 cuando a=1, b=0 y a=0, b=1` 
    
    ### Paso 2:
    
    Ahora tenemos que armar la tabla de verdad
    
    ![image.png](image%206.png)
    
    ### Paso 3:
    
    Con la tabla de verdad y las condiciones para F=1 aplicadas en el pasa anterior ahora tenemos que armar las expresiones logicas en de los casos en los que F=1 y representarlas como miniterminos
    
    de forma → (x.y) en los que si x es 1 queda tal cual y si x en la tabla de verdad es 0 queda negada ~x, entonces los miniterminos nos quedarian de la siguiete forma → (~a.b)+(a.~b) 
    
    ¿Por se suman los minterminos ?¿por que se multiplica cada variable con la otra?
    
    Para entender esto nos tenemos que basar en la defincion de ***Suma de productos*** entonces entedemos que aplicamos multiplicacion a los miniterminos porque se expresan con una compuerta `and` y a los miniterminos se los suman porque nos referimos a una compuerta `OR` 
    
    ### Paso 4:
    
    Ahora nos queda expresar esto en un ciciuto logico en los que las variables de un minitermino seran las entradas de una compuerta and y las salida de cada compuerta and sera la entrada de la compuerta or. 
    
    En resumen necesitamos tantas compuertas and como miniterminos y solo una compuerta or
    
    par este caso nos quedaria algo asi →
    
    ![image.png](image%207.png)
    
    > Podrias usar una not para negar las variables ya que no queda expresada de la mejor forma que a o b son 0 o tienen un valor distindo de b y a, lo recomendable seria algo como a —compuerta NOT—→ENTRADA A COMPUERTA AND
    > 
- ***Instrucciones***
    
    
    ***1.¿Que elementos debe poseer una instruccion?***
    
    - Codigo de operacion : Se espedifica la opeacion a realizar(suma,resta,mult,E/S,etc.).La operacion se indica mediante un codigo binario denominado codop
    - Referencia operando  fuente o origen: la operacion puede involucrar a uno o mas operandos origen, es decir operandos que son entradas para la instruccion.
    - Referencia operando destino o resultado:la operacion puede producir un resultado por lo que se indica un un registro, dir de memoria u operando implicito donde se alamacenara.
        - Los operandos fuente y resultado pueden
        estar en tres lugares :
        • Memoria   
        • Registro de la CPU
        • Dispositivo de E/S
    - Referencia a la siguiente instruccion: dice al porcesador donde captar la sig instruccion luego de completarse la ejecucion de la instruccion actual.
    
    ***2. Describa el modo de direccionamiento que se utiliza en las intrucciones de salto condicional***
    
    (Corregido por runco)
    
    Direccionamiento relativo : Se suma un valor al PC(contador de programa) a fin de determinar la direccion realativa de la instruccion actual.También puede usarse el **modo directo** (con una dirección fija JMP 3000h) o **modo indirecto** (donde se accede a una dirección a través de un registro o memoria JMP BX)
    
     
    
    ***Describa el modo de direccionamiento que se utiliza en las intrucciones de salto incondicional***
    
    En una instrucción de salto incondicional se puede utilizar el **modo de direccionamiento relativo**, donde se indica un desplazamiento con respecto al contador de programa (**PC**), permitiendo saltos dentro del programa sin necesidad de direcciones absolutas.
    
    | Tipo de instrucción | ¿Qué necesita? | Modos comunes |
    | --- | --- | --- |
    | **Salto incondicional** | Dirección de código | Relativo, directo, indirecto |
    | **Salto condicional** | Dirección + condición | Relativo, directo, indirecto |
    | **Operación aritmética** | Datos (operandos) | Registro, inmediato, directo, desplazamiento |
    
    ## Tipos de instrucciones
    
    Podemos categorizar las instrucciones de máquina como de:
    
    - Procesamiento de datos:
    operaciones aritméticas y lógicas.
    - Almacenamiento de datos:
    transferencias dentro del sistema.
    - Instrucciones de E/S:
    transferencia de datos entre la computadora y
    los mecanismos externos.
    - Control
    
    ***¿Que es el formato de Instruccion?***
    
    Un formato de instruccion define la descripcion en bits de una instruccion. La misma debe incluir el codigo de operacion(***codop***), los operandos que seran refernciados en algunos de los modos de direccionamiento vistos (inmediato,directo,indirecto,registro,indirecto con registro, con desplazamiento y pila).
    En la mayoría de los repertorios de instrucciones se emplean **múltiples formatos de instrucción**, para adaptarse a distintos tipos de operaciones y maximizar la eficiencia del código.
    
    ### ***Repertorio de instrucciones***
    
    ![image.png](image%208.png)
    
    ***Describa el formato de instruccion de una maquian de 1 direccion*** 
    En una **máquina de 1 dirección**, cada instrucción contiene un **código de operación (opcode)** y **una dirección**. El operando indicado se toma de memoria y se opera con el acumulador, que es el operando implícito. El resultado normalmente se guarda en el acumulador. Este formato simplifica el hardware pero requiere más instrucciones para tareas complejas.
    
    ```jsx
    En este tipo de arquitecturas solo se usan direcciones por lo cual si queremos
    guardar un dato en un lugar debemos hacer los siguiente
    load 100 -> cargo lo que hay en la dir 100 en el acumulador implicito
    store 150 -> guardo lo que hay en el acumulador en la dir 150 
    ```
    
    Desventajas
    
    - **Mayor cantidad de instrucciones necesarias** para realizar operaciones complejas.
    - Menor flexibilidad, ya que **el acumulador es el destino y uno de los operandos fijos**.
    - Ineficiente en programas largos o complejos.
    
    ## ¿Como es el formato de instruccion de una maquina de 3 direcciones ?
    
    El formato de instruccion de una maquina de 3 direcciones se caracteriza por tener explicitamente 3 operandos en la instruccion, dos operandos fuente y un operando destino. Esto permite que la instruccion realiza operaciones entre los dos operandos fuentes o valores y los almacene en el operando destino, todo en la misma instruccion.
    
    - Permite operaciones mas completas en una sola instruccion
    - Reduce la cantidad de instrucciones adicionales para mover datos
    - Favorece un uso eficiente de los registros
    
    Desventajas
    
    - Instrucciones mas largas
    - requier mayor espacio de memoria para cada instruccion
    - mas complejidad den el diseño del decodificador
    
    ### **Máquina de 2 direcciones**
    
    ### ✅ Ventajas:
    
    - Compromiso entre simplicidad y potencia.
    - Instrucciones más **cortas que en 3 direcciones**, pero más expresivas que en 1.
    - Más adecuada para arquitecturas con menos registros disponibles.
    
    ### ❌ Desventajas:
    
    - Generalmente **uno de los operandos fuente se sobreescribe** (no se conservan ambos).
        - Ejemplo en MSX88
            
            ```nasm
            ADD AX, CX -> Sumo : AX + CX y se guarda en AX 
                                 -> En lenguaje de alto nivel seria: total:= total + cantidad;
            ```
            
    - Puede requerir instrucciones adicionales para guardar valores intermedios.
- ***IEEE 754***
    
    ### Describa características de IEEE 754 simple precisión
    
           El estándar **IEEE 754** define la representación de números en punto flotante. En su versión  
    
      de **simple precisión (32 bits)**, los bits se distribuyen de la siguiente forma:
    
    - **1 bit** para el **signo** (0 positivo, 1 negativo),
    - **8 bits** para el **exponente**, con un **exceso (bias)** de 127 (es decir, 27−12^7 - 127−1),
    - **23 bits** para la **mantisa** o **fracción**, que representa la parte decimal del número, asumiendo una parte entera implícita igual a 1 (en números normalizados).
    
    Esto permite representar números reales positivos y negativos con un amplio rango y precisión, y es utilizado ampliamente en arquitecturas de hardware y software.
    
    ### Describa características de IEEE 754 doble precisión
    
    El estandar IEEE 754 define la representacion de numeros en punto flotante.En su version de doble presicion(64 bits), los bits se distribuyen en la sguiente forma
    
    1bit signo - 11 bits de exponente(2^N-1-1) - 52 bits de mantisa
    
    > Importante explicar el cuadro de cada sistema, no basta con las explicaciones anteriores
    > 
    
    ![image.png](image%209.png)
    
    ![image.png](image%2010.png)
    
- ***Organizacion de memoria***
    - Organizacion 2D y 2 1/2D
        
        ![image.png](image%2011.png)
        
    
    ### Describa y realice un esquema de organización 2D y con capacidad de almacenamiento de 1024 palabras de 16 bits
    
    ### Posible solucion del ejercicio
    
    Este ejercicio se lo consulte a runco y dijo que estaba bien.
    
    ![Imagen de WhatsApp 2025-05-12 a las 19.13.03_61397d42.jpg](Imagen_de_WhatsApp_2025-05-12_a_las_19.13.03_61397d42.jpg)
    
    ![image.png](image%2012.png)
    
    Este ejemplo es de una memoria de 4 bits 
    
    En el ejercicio se piden para 1024 palabras por lo que desde el decodificadro deberiamos tener 1024 salidas o hacer 2^w = 2^10, y el tamaño de la palabra se indica como 16 bits
    
    ## Ejemplo del ejercicio anterior con organizacion de memoria 2 1/2D
    
    ### Ejemplo de la catedra
    
    ![image.png](image%2013.png)
    
    ### Resolucion planteada (por runco)
    
    ![Imagen de WhatsApp 2025-05-14 a las 21.41.58_0cf3e862.jpg](Imagen_de_WhatsApp_2025-05-14_a_las_21.41.58_0cf3e862.jpg)
    
    > Para este ejercicio se pide mas que nada graficar como lo hice, pero no esta de mas dar data del tipo de organizacion.
    > 
    
    ## ¿Por que la organizacion de memoria semiconductora 2 1/2D utiliza 2 decodificadores?
    
    la utilización de dos decodificadores en la organización de memoria 2 1/2D es una estrategia inteligente para **equilibrar la eficiencia en la selección de la memoria con la complejidad del circuito de decodificación**, ofreciendo una solución práctica y ampliamente utilizada en sistemas de memoria.
    
    - El docodificador de filas se encarga de seleccionar una fila o palabra de celdas de memoria. Recibe una direccion de memoria como entrada y acitiva una linea como salida que corresponde a la fila deseada.
    - El decodificador de columnas se encarga de seleccionar el bit en especifico dentro  de la palabra
    
    ## ¿Por que la organizacion de memoria 2D No necesita refresco?
    
    Por el tipo de estructura, dado que la organizacion de memoria 2D es de SRAM y esta compuesta de FLIP-FLOPS no necesita refresco, los flips flops guradan el estado sin necesidad de refresco, no como los transistores de DRAM que al perder la carga electrica pierden los datos por lo que se deben refrescar.
    
    ![image.png](image%2014.png)
    
    Basada en flip flops: memoria estática (SRAM)
    Basada en transistores: memoria dinámica (DRAM).
    Cargas almacenadas en transistores (capacitores)
    
- ***Jerarquia de memoria***
    
    ### ¿Cuáles son los principios que permiten el funcionamiento de un sistema de memoria basado en jerarquía?
    
    - **Principio de localidad temporal**:
        
        Establece que si un dato se accedió recientemente, es probable que se vuelva a acceder en un futuro cercano. Esto sucede comúnmente en estructuras como bucles, donde las mismas variables o instrucciones se reutilizan varias veces seguidas.
        
    - **Principio de localidad espacial**:
        
        Indica que si se accede a una posición de memoria, es probable que pronto se acceda a posiciones cercanas. Por eso, en lugar de traer solo una dirección de memoria, se cargan bloques completos (líneas de caché), aumentando la eficiencia.
        
        ```jsx
        EJEMPLO DE APLICACION DE AMBOS
        
        Loc. temp: vec[i]
        Loc. esp: for(){}
        
        for (int i = 0; i < n; i++) {
            vec[i] = i * 2;
        }
        Localidad en los programas: consecuencia de la estructura secuencial de los
        programas.
        Localidad en los datos: consecuencia de las estructuras secuenciales de datos.
        ```
        
        ### ¿ En que consiste una jerarquia de memoria ?
        
        ![image.png](image%2015.png)
        
        > Para este ejercicio se deben explicar las velocidades de los tipo de memoria y la capacidad de almancenamiento, ademas se deben usar palabras tecnicas para la respuesta general.
        > 
        
        ## Sustento de los principios de localidad de memoria
        
        ### Principio de localidad espacial de referencia
        
        Se sustenta en : 
        
        - Ejecucion secuencial del codigo
        - Tendencia de los programadores a hacer proximas entre si variables relacionadas
        - Acceso a estructuras tipo matriz o pila
        
        ### Principio de localidad temporal de referencia
        
        Se sustenta en: 
        
        - Formacion de ciclos o bucles
        - Subrutinas(procedimientos o funciones)
        - Pilas
- ***MSX88***
    
    ### ¿El MSX88 simula una maquian de 2 direcciones ? justifique
    
     Sí, el MSX88 simula una máquina de 2 direcciones, ya que sus instrucciones permiten especificar dos operandos explícitos. Por ejemplo, en la instrucción `ADD A, B`, se indica que el contenido de B se suma al de A. El hecho de que sea una máquina de 16 bits se refiere al tamaño de sus registros o palabras, pero no define si es de 1, 2 o 3 direcciones.
    
- ***Circuitos logicos***
    
    ### ¿Que es un circuito combinatorio?
    
    ![image.png](image%2016.png)
    
    ![image.png](image%2017.png)
    
    ![image.png](image%2018.png)
    
    ## ¿Cual es la diferencia entre un circuito combinatorio y uno secuencial?
    
         **What is a Combinational Circuit?**
    
    A combinational circuit could be defined as a circuit whose output depends only on inputs at the same moment.
    
    The example of Combinational Circuit include:
    
    - Half Adder
    - Full Adder
    - Half Subtractor
    - Full Subtractor
    
    **What is a Sequential Circuit?**
    
    A sequential circuit is defined as a circuit whose output is not just based on the current inputs but also on the previous time of inputs.
    
    Examples of a Sequential circuit are:
    
    - Flip-Flops
    - Registers
    - Counters
    
    **The Key Differences Between Combinational and Sequential Logic Circuit**
    
    1. Sequential and combinational logic circuits are the basic building blocks of digital circuits. However, the existence of memory elements makes the main difference. The circuit for combination doesn’t have a memory element, while a sequential circuit is composed of memory elements.
    2. Sequential and combinational logic circuits can generate different outputs. The output from the circuit for combination is a function of the current inputs. However, the output generated by the sequential circuit is dependent on the prior output and current input.
    3. The feedback loop isn’t included in combinational logic circuits. However, any sequential logic circuit should contain it to monitor the output of previous cycles.
    4. The clock signal isn’t utilized in the combinational circuit. However, sequential utilize clock signals to ensure synchronization.
    5. The design process for the combinational circuit is simpler than that in the conventional circuit.
    
    1. 1. Sequential and combinational logic circuits are the basic building blocks of digital circuits. However, the existence of memory elements makes the main difference. The circuit for combination doesn’t have a memory element, while a sequential circuit is composed of memory elements.
    2. 2. Sequential and combinational logic circuits can generate different outputs. The output from the circuit for combination is a function of the current inputs. However, the output generated by the sequential circuit is dependent on the prior output and current input.
    3. 3. The feedback loop isn’t included in combinational logic circuits. However, any sequential logic circuit should contain it to monitor the output of previous cycles.
    4. 4. The clock signal isn’t utilized in the combinational circuit. However, sequential utilize clock signals to ensure synchronization.
    5. 5. The design process for the combinational circuit is simpler than that in the conventional circuit.
- ***Ciclos de instruccion***
    
    ### ¿Que es un ciclo de instruccion?
    
    Consite en ejcutar un programa, trayendo desde la memoria las instrucciones que lo componen una por una y cumplirlas de forma ordenada.
    
    El procesamiento de un instruccion se puede dividir en Captacion de la instruccion(lectura desde memoria) y ejecucion. Solo se interrumpe si ocurre algun error.
    
    ![image.png](image%2019.png)
    
    Si las interrupciones estan habiitadas cuando suerge una interrupcion se guarda el estado actual del procesador y se atiende la interrupcion
    
    // sacado del libro Stallings 7ma edicion
    
    Al principio de cada ciclo de instruccion, la CPU capta una instruccion de memoria en el registro PC para seguir la pista de que instruccion debe captarse despues.A no ser que pase algo la CPU siempre incrementa el PC de forma que si estamos en la dir 300 las proximos intrucciones a captar estaran en la direccion 301,302,etc(esta sucesion se puede alterar).
    
    La instruccion captada se almacena en el registro de instruccion IR de la [CPU.](http://CPU.la) La instruccion se escribe con un codigo binaria que especifica la accion a realizar para la [CPU.](http://CPU.La) La CPU interpreta la instruccion y lleva a cabo la accion requerida. 
    
    Las acciones pueden ser de 4 tipos:
    
    - Procesador-Memoria: se transfieren datos de cpu a memoria o viceversa
    - Procesador-E/S: se transfieren datos de un modulo E/S-CPU o viceversa
    - Procesamiento de datos: La cpu ha de realiza alguna operacion aritmetica o logica con los datos.
    - Control: una instruccion puede especificar que la secuencia de ejecucion se altere(como saltos),
- ***Modelo de von Neunmman***
    
    ![image.png](image%2020.png)
    
    ### Aspectos mas importantes
    
    - Utilización del sistema binario:
        - Simplifica la implementación de funciones.
        - Disminuye la probabilidad de fallos.
    - Instrucciones y datos residen en memoria:
        - Ejecución del programa en forma secuencial.
        - Aumenta la velocidad.
    - La memoria es direccionable por localidad sin
    importar el dato almacenado.
    
    ### Se introdujo el concepto de programa almacenado
    
    Antes para realizar distintas operaciones de debian realizar cambios en el hardware, esto era la programacion enhardware.
    
    Ahora se tiene un interprete de instrucciones el cual le envia las señaes de control a la ALU para que realize la operacion, esto es Programacion en hardware 
    
- ***Memoria cache***
    
    ## Idea general de la memoria cache
    
    La idea general es que cuando se hace referencia a una palabra, ella y alguna de las vecinas se traen de la memoria grande y lenta a la cache, para que en el siguiente acceso la palabra buscada se encuentre en la cache.
    
    Esto nos dice que si en la ejecucion de un programa usamos un dato muy probablemnte los datos que se usen proximamente estaran contiguos en la memoria al dato anterior por lo que lo mejor es traer un bloque con los datos para poder hacer un mejor uso de la cpu y no tener retardos llendo a traer datos que en cada ejecucion de la CPU.
    
    ![image.png](image%2021.png)
    
    ### Mapeo de la memoria(Capítulo 5: Memoria Externa
    Stallings, W., 5o Ed.)
    
    ### 1. Mapeo Directo
    
     Es una técnica donde cada bloque de memoria principal se asigna a una única ubicación específica en la caché.Un bloque de memoria principal siempre se va a cargar en la misma linea de memoria cache
    
    - Es simple y rapida
    - Puede traer ***problemas***, al tener bloques de memoria asignados a una direccion especifica en la cache esto no permite que se traiga otro bloque que tambien esta asignado a esa direccion de memoria.
    
    ### 2. Mapeo asociativo
    
    - Cualquier bloque de memoria principal puede cargarse en cualquier linea de la memoria cache
        - Esto soluciona el problema de mepeo directo ya que una linea de memoria chache no deberia ser reemplazada por otra
        - La desventaja es que se deberia buscar en todo la memoria cache para encontrar un lugar para traer el bloque de memoria principal
    
    ### 3. Mapeo asociativo por grupos
    
    - La memoria cache se divide en conjuntos de lineas, un bloque de memoria principal puede se mapeado a cualquier linea de un conjunto  especifico.
        - La busqueda de una linea disponible en la memoria cache es menos significativa que la busqueda en mapeo asociativo ya que solo se busca un linea disponible en el conjunto y no en toda la memoria cache
    
    ![image.png](image%2022.png)
    
- ***Modos de direccionemiento***
    
    ## Describa los modos de direccionamiento
    
    Los mdd tienen como objetivo:
    
    - Disminuir la cantidad de bits en la instrucción
    - Ma dirección puede que no se conozca hasta el
    momento de ejecutar el programa
    - Manejo más eficiente de datos (arreglos)
    
    ### 1. Direccionamiento inmediato
    
    En este modo, el **operando es un valor constante que se encuentra directamente en la instrucción**. No es necesario realizar ningún cálculo ni acceder a la memoria para obtener el dato; la instrucción lo contiene.
    
    - **Ejemplo:** `MOV AX, 0ABCDH` (Carga el valor hexadecimal `0ABCD` en el registro `AX`). Es como decirle a alguien: "Aquí tienes el número que necesitas, úsalo directamente".
    
    ### 2. Direccionamiento por registro
    
    El operando se encuentra en un **registro de la CPU**. La instrucción especifica el nombre o número del registro donde se halla el dato. Es el modo más rápido, ya que los registros son la memoria más cercana al procesador.
    
    - **Ejemplo:** `MOV CX, DX` (Copia el contenido del registro `DX` al registro `CX`). Imagina que los registros son cajones de acceso súper rápido, y la instrucción te dice: "Toma lo que hay en este cajón y ponlo en este otro".
    
    ### 3. Direccionamiento directo
    
    La instrucción contiene la **dirección de memoria exacta** donde se encuentra el operando. El procesador simplemente usa esta dirección para acceder al dato.
    
    - **Ejemplo:** `MOV AX, [2000H]` (Carga el contenido de la posición de memoria `2000H` en el registro `AX`). Es como decir: "Ve directamente a la dirección 2000 de la calle de la memoria y trae lo que encuentres allí".
    
    ### 4. Direccionamiento indirecto por registro
    
    La instrucción especifica un **registro que contiene la dirección de memoria** donde se encuentra el operando. Es decir, el registro actúa como un "puntero" a la ubicación real del dato en memoria.
    
    - **Ejemplo:** `MOV AX, [BX]` (Carga el contenido de la dirección de memoria apuntada por el registro `BX` en el registro `AX`). Piensa en esto como una nota que dice: "Mira en el cajón 'BX', ahí encontrarás un papel con la dirección real del dato".
    
    ### 5. Direccionamiento basado o indexado
    
    Combina el contenido de un **registro base** (o un registro índice) con un **desplazamiento (offset)** que forma parte de la instrucción. Esto es muy útil para acceder a elementos en estructuras de datos como arrays o arreglos.
    
    - **Direccionamiento basado:** La dirección efectiva se calcula sumando el contenido de un registro base y un desplazamiento.
        - **Ejemplo:** `MOV AX, [BX + 10H]` (Carga el contenido de la dirección `BX + 10H` en `AX`). Esto es como decir: "Ve al inicio de la 'lista BX' y avanza 10 posiciones para encontrar lo que buscas".
    - **Direccionamiento indexado:** Similar al basado, pero usa un registro índice, a menudo para recorrer elementos de un array.
        - **Ejemplo:** `MOV AX, [SI + 20H]` (Carga el contenido de la dirección `SI + 20H` en `AX`). Aquí, `SI` podría ser el índice de un elemento.
    
    ### 6. Direccionamiento relativo al contador de programa (PC-relative)
    
    La dirección efectiva se calcula sumando un **desplazamiento** (contenido en la instrucción) al valor actual del **contador de programa (PC)**. Se usa principalmente para saltos y bifurcaciones dentro del código, permitiendo un código reubicable (que puede cargarse en cualquier parte de la memoria).
    
    - **Ejemplo:** `JMP $+5` (Salta 5 bytes hacia adelante desde la instrucción actual). Es como decir: "Desde donde estás ahora, avanza 5 pasos en el programa".
- ***Teorema fundamental de la numeracion***
    
    ![image.png](image%2023.png)
    

### 

[Ejercicios de perifericos ](https://www.notion.so/Ejercicios-de-perifericos-1dcf0238bf29801691dad372f9cb2bb4?pvs=21)
