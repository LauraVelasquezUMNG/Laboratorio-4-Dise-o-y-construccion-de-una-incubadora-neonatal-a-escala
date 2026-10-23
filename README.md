# Laboratorio 4: Diseño y construcción de una incubadora neonatal a escala

## Integrantes
* Laura Valentina Velásquez Castiblanco (5600846)
* Carlos Felipe Moreno Guzmán (5600881)
* Juan Andrés Mateus Durán (5600787)

## Objetivos

### Objetivo General
Comprender la importancia de las incubadoras neonatales en la supervivencia, el desarrollo y la salud del recién nacido, a partir del diseño y la implementación de un sistema que emule su modo de operación.

### Objetivos Específicos
- Identificar los componentes principales de una incubadora neonatal y la función que cumple cada uno dentro del sistema.
- Desarrollar un sistema que emule el modo de operación de una incubadora neonatal, integrando los elementos necesarios para generar y regular un ambiente controlado.
- Analizar cómo influye el control de variables como la temperatura, la humedad y el flujo de aire en la salud y el bienestar del neonato.

> ### Parte A

## Revisión de la Literatura

### 1. Incubadora neonatal: definición y propósito

Una **incubadora neonatal** es un dispositivo médico que genera un entorno controlado en el que se regulan variables importantes para el desarrollo del recién nacido. Su origen está ligado a la atención de neonatos prematuros, que requieren un medio capaz de simular las condiciones del vientre materno [1]. Constructivamente, es un recinto cerrado al que se suministra aire calentado externamente; la potencia de calentamiento puede controlarse manualmente o mediante un **servocontrol** termostático que mantiene la temperatura de la piel o del aire en un valor deseado [2].

En su funcionamiento básico, un ventilador o turbina pequeña toma el aire del exterior y lo hace pasar por un elemento calefactor (por ejemplo, una resistencia) hasta alcanzar la temperatura especificada [3]. Junto con las cunas de calor radiante y los colchones calefactados, las incubadoras forman el grupo de dispositivos de asistencia a la termorregulación del neonato. Las cunas de calor radiante son abiertas y facilitan el acceso al paciente, pero aumentan las pérdidas evaporativas, que en las incubadoras pueden limitarse elevando la humedad del aire [2].

### 2. Termorregulación del neonato y necesidad de la incubadora

Los neonatos sanos y a término regulan su temperatura corporal, mientras que los prematuros y enfermos tienen dificultades para mantenerla constante sin asistencia externa debido a la inmadurez de su sistema de termorregulación. Esto los expone a estrés por frío e hipotermia, con mayor morbilidad y mortalidad. La pérdida de calor es especialmente crítica en neonatos pequeños y prematuros por su elevada relación entre superficie corporal y masa. Se denomina **ambiente térmico neutro** al conjunto de condiciones ambientales que produce una temperatura cutánea óptima, correspondiente a la mínima tasa metabólica en reposo [2].

La Organización Mundial de la Salud (OMS) establece como temperatura corporal normal del recién nacido el intervalo de 36,5 °C a 37,5 °C [4]. La hipotermia se clasifica en leve (36,0–36,4 °C), moderada (32,0–35,9 °C) y grave (menos de 32 °C). La prematuridad agrava el problema: cuanto más prematuro es el neonato, menor es la grasa subcutánea que actúa como aislante, y la **termogénesis sin temblor**, que genera calor en el tejido adiposo pardo, es ineficiente por debajo de aproximadamente 32 semanas de gestación. La relevancia clínica es cuantificable: en un estudio de Laptook et al., con 5277 neonatos de 401 a 1499 g, cada 1 °C de descenso en la temperatura de admisión se asoció con un aumento del 28 % en la mortalidad [5].

### 3. Mecanismos de pérdida de calor que la incubadora debe contrarrestar

El neonato intercambia calor con el entorno por cuatro mecanismos (conducción, convección, radiación y evaporación) a través de la piel y del tracto respiratorio [2], [5]. Comprenderlos permite diseñar las intervenciones que bloquean la transferencia de calor del neonato hacia el ambiente y explica la función de cada parte de la incubadora. En las ecuaciones, *Q* representa la potencia térmica intercambiada.

**Conducción.** Es la transferencia de calor por contacto directo entre la piel y una superficie más fría; para una pared plana se describe con la ley de Fourier [5], [6]:

$$Q_{cond} = \frac{k \times A}{L} \times (T_{s} - T_{c})$$

donde *k* es la conductividad térmica del material, *A* el área de contacto, *L* el espesor, *T*<sub>s</sub> la temperatura de la piel y *T*<sub>c</sub> la de la superficie en contacto. En un neonato sobre un colchón de espuma esta pérdida es pequeña y suele considerarse despreciable [2].

**Convección.** Es el calor que pasa de la piel al aire en movimiento cuando la piel está más caliente que el aire, y se modela con la ley de enfriamiento de Newton [5], [6]:

$$Q_{conv} = h_{c} \times A \times (T_{s} - T_{a})$$

donde *h*<sub>c</sub> es el coeficiente de convección, que depende de las condiciones del flujo de aire, y *T*<sub>a</sub> la temperatura del aire.

**Radiación.** Es la emisión de energía en forma de ondas electromagnéticas y resulta significativa en las incubadoras, donde la pérdida hacia paredes frías es una preocupación importante [2]:

$$Q_{rad} = \epsilon \times \sigma \times A \times (T_{s}^{4} - T_{w}^{4})$$

donde ε es la emisividad, σ la constante de Stefan–Boltzmann (5,67×10⁻⁸ W·m⁻²·K⁻⁴), *T*<sub>w</sub> la temperatura de la pared y las temperaturas se expresan en kelvin [6].

**Evaporación.** Consiste en la pérdida de agua por la piel (transepidérmica) y por el tracto respiratorio; el calor necesario para evaporarla se toma de la piel y reduce la temperatura corporal [2]:

$$Q_{evap} = m_{w} \times h_{fg}$$

donde *m*<sub>w</sub> es la tasa de pérdida de agua y *h*<sub>fg</sub> el calor latente de vaporización, del orden de 0,6 kcal por gramo de agua perdida. La tasa de evaporación es proporcional al gradiente de presión de vapor entre la piel y el ambiente y crece al disminuir la humedad ambiente [5]. En prematuros de menos de 30 semanas de gestación, las pérdidas por evaporación superan el 30 % del calor metabólico generado [2].

En condiciones de equilibrio térmico, el calor metabólico producido iguala las pérdidas totales:

$$Q_{met} = Q_{cond} + Q_{conv} + Q_{rad} + Q_{evap}$$

Cuando las pérdidas superan la producción metabólica, el balance energético es negativo. La incubadora aporta el calor y las condiciones ambientales que cierran ese balance [2].

### 4. Componentes principales de una incubadora neonatal y su función

La Tabla 1 resume las partes principales de una incubadora neonatal y su función, y la Figura 1 muestra la ubicación de las partes visibles desde el exterior.

**Tabla 1.** Componentes principales de una incubadora neonatal y su función.

| <p align="center"> Componente </p> | <p align="center"> Función </p>  |    N.º en Fig. 1    | Fuente |
|:---|:---|:---:|:---:|
| **Cúpula (cubierta)** | Aísla al neonato del ambiente exterior (corrientes de aire, bajas temperaturas) y crea el microambiente. Debe permitir ver al neonato; suele fabricarse en acrílico. | 1 | [1] |
| **Puertas de acceso** | Facilitan el cuidado del neonato y reducen al mínimo la pérdida de temperatura y los cambios bruscos del ambiente interno. | 2 | [1], [2] |
| **Colchón y portacolchón** | Soporte del neonato, ubicado sobre el chasis y dentro de la cúpula. La conducción sobre un colchón de espuma es despreciable. | 3 | [1], [2] |
| **Chasis** | Base metálica que aloja los sensores y la fuente de alimentación y soporta el portacolchón y la cúpula. | 4 | [1] |
| **Panel de control y pantalla** (interfaz del servocontrol) | Permite fijar la temperatura de control y recibir las alertas del equipo. | 5 | [1], [5] |
| **Doble pared** (cuando existe) | Reduce las pérdidas radiativas y la pérdida total de calor. | No visible | [2], [5] |
| **Elemento calefactor** | Calienta el aire que se suministra al recinto (por ejemplo, una resistencia). | Interno | [2], [3] |
| **Ventilador** | Toma aire, lo hace pasar por el elemento calefactor y lo hace circular dentro de la cabina. | Interno | [3], [5] |
| **Sensores de temperatura y controlador (servocontrol)** | Miden la temperatura de la piel o del aire y aumentan o disminuyen el calor para mantener la temperatura de consigna. | Interno | [2], [5] |
| **Humidificador** | Depósito o vía de agua que genera un ambiente húmedo para limitar las pérdidas por evaporación. | Interno | [2], [5] |
| **Sensores de seguridad y alarmas** | Alertan ante temperatura fuera de rango, humedad, luminosidad o ruido, y ante la apertura de la puerta. | Interno | [1] |
| **Fuente de alimentación y protección eléctrica** | Convierte la tensión alterna de red en tensión continua para los circuitos y sensores; incluye elementos de protección como el fusible. | Interno | [1] |

<p align="center">
  <img width="450" height="450" alt="image" src="https://github.com/user-attachments/assets/df9ba6d7-78d7-4efd-b6d0-164086060584" />
</p>

<p align="center"><em>Figura 1. Partes externas de una incubadora neonatal. Adaptada de [7].</em></p>

### 5. Envolvente: cúpula, puertas, doble pared y soporte del neonato

La **cúpula** es la responsable de aislar al neonato y crear una barrera entre el ambiente exterior y el microambiente de la incubadora, protegiéndolo de corrientes de aire y bajas temperaturas. Debe permitir la visibilidad del neonato y estar hecha de un material que no reaccione con el oxígeno, para evitar la corrosión cuando se requiere oxigenoterapia; generalmente se utiliza acrílico de aproximadamente 6 mm de espesor. Las **puertas de acceso** facilitan el cuidado del neonato y reducen al mínimo la pérdida de temperatura y los cambios bruscos del ambiente interno; suelen ser dos frontales, dos laterales y dos posteriores, cubiertas por un plástico especial que atenúa la pérdida de calor, además de una puerta frontal grande por donde se introduce el neonato. El **chasis** es la base metálica que aloja los sensores y la fuente de alimentación y sobre la cual se ubica el portacolchón; debe soportar el peso del neonato y de la cúpula y resistir las temperaturas internas sin deformarse. El **colchón** y su **portacolchón** constituyen el soporte del neonato dentro de la cúpula [1].

> [!NOTE]
> Abrir una incubadora durante un procedimiento puede reducir entre 3 °C y 5 °C la temperatura del aire interior [2]. Por eso el diseño de las puertas y de la cubierta influye directamente en la estabilidad térmica.

En la incubadora de **doble pared**, dos paredes están separadas por una capa de aire y la interna se calienta a una temperatura cercana a la del aire interior, lo que reduce sustancialmente las pérdidas radiativas [2]. Además, según una revisión Cochrane, la doble pared disminuye la pérdida total de calor, la necesidad de producir calor y el consumo de oxígeno, aunque sin beneficios a largo plazo en los desenlaces del neonato, la mortalidad ni la duración de la estancia [5].

### 6. Calefacción, circulación de aire y servocontrol

El calor se genera con un **elemento calefactor**, por ejemplo una resistencia, y un **ventilador** o turbina pequeña toma el aire y lo hace pasar por él hasta alcanzar la temperatura especificada [3]. El aire calentado se suministra al recinto cerrado y circula por la cabina gracias al ventilador [2], [5].

En el **servocontrol** se fija una temperatura de control, referida a la piel o al aire, y el equipo aumenta o disminuye el calor para mantenerla mediante un sistema de realimentación. Como referencia clínica, se recomienda controlar la temperatura cutánea con un mínimo de 36,5 °C, valor que se eleva a 36,8–36,9 °C en prematuros extremos [5].

### 7. Humidificación

Los neonatos muy prematuros, con piel delgada y altas pérdidas evaporativas, requieren ambientes húmedos. Por eso las incubadoras incluyen un depósito o una vía para añadir agua y generar un ambiente húmedo [5], y la mayoría de las modernas incorporan humidificación suplementaria que puede elevar la humedad hasta 95 % [2].

La humedad elevada también tiene inconvenientes: se ha observado proliferación bacteriana en puntos fríos de incubadoras con humedad superior a 60 %, y las pérdidas transepidérmicas disminuyen más tarde con humedad de 75 % que con 50 %, lo que se asocia a un retraso en la maduración de la barrera cutánea. En la práctica clínica no existen estándares que guíen su uso y los niveles empleados varían entre 45 % y 100 % [5].

### 8. Sensores, alarmas, alimentación y seguridad

En la literatura se describen incubadoras con sensores de temperatura (con alerta cuando sale de un rango preestablecido, generalmente entre 36 °C y 38 °C), de humedad, de luminosidad y de ruido, además de una alarma de puerta abierta, luminosa mientras permanece abierta y sonora si supera los 30 s. La **fuente de alimentación** convierte la tensión alterna de la red en tensión continua mediante cuatro etapas: transformación (reduce la tensión de entrada), rectificación (pasa de corriente alterna a continua con un puente rectificador), filtrado (aplana la señal con condensadores) y estabilización (mantiene la salida constante con un regulador). Elementos como el fusible ayudan a prevenir daños al neonato y al equipo [1].

Como inconvenientes, la incubadora limita el acceso al neonato y actúa como barrera entre el niño y sus padres, lo que reduce el contacto. Además, es potencialmente peligrosa por el uso de electricidad y de elementos calefactores, y un ambiente cálido y húmedo aumenta el riesgo de infección [5].

### 9. Normativa aplicable

La norma IEC 60601-2-19 establece los requisitos particulares de seguridad básica y desempeño esencial de las incubadoras neonatales. No aplica a incubadoras de transporte (IEC 60601-2-20), cunas de calor radiante (IEC 60601-2-21) ni equipos de fototerapia infantil (IEC 60601-2-50) [8].

## Circuito de Control de Temperatura



## Circuito de Medición de Peso



> ### Parte B



> ### Parte C

### 1. Procedimiento General

El prototipo se construyó con una cubierta de **acrílico** transparente, que permite ver el interior de la cabina, y con dos módulos funcionales: uno de calefacción y uno de pesaje. El módulo de calefacción consiste en una caja de madera que aloja un ventilador mediano de 12 V y, frente a él, una resistencia de potencia de 20 W y 20 Ω fijada con soportes metálicos. El principio de operación sigue el descrito en la guía: el ventilador impulsa aire sobre el elemento resistivo para llevar el calor a la cabina por convección. Este módulo se alimentó con un cargador de celular de 12 V y 200 mA.

El módulo de pesaje se construyó con una **celda de carga de 10 kg** fijada a una base de madera, con su respectiva plataforma de soporte para recibir la carga. La celda se conectó a un módulo amplificador **HX711**, encargado de convertir su señal analógica en un valor digital, y este a su vez a una placa ESP32, que procesa la señal y muestra el peso en una pantalla LCD.

Para validar el pesaje se colocó sobre la plataforma un patrón de peso conocido y se comparó el valor mostrado en la pantalla con el valor real. Para validar la calefacción se energizó el módulo con el ventilador y la resistencia, y se observó si la temperatura de la cabina aumentaba.

### 2. Resultados Obtenidos

Las estructuras del prototipo quedaron ensambladas e integradas: la cubierta de acrílico, el módulo de calefacción, la plataforma de pesaje y la electrónica de control con su pantalla. El costo total del sistema fue de **$150.000 COP**.

El módulo de pesaje funcionó: la celda de carga de 10 kg respondió a la carga y el valor se mostró en la pantalla LCD. La lectura no se fija de inmediato, sino que avanza de forma progresiva hasta estabilizarse, lo que ocurrió en aproximadamente **1 minuto**. Frente al patrón de peso conocido, el sistema presentó un error aproximado menor al **8 %**.

En el módulo de calefacción, el ventilador operó con normalidad y mantuvo la circulación de aire dentro de la cabina; sin embargo, esta no alcanzó un calentamiento apreciable. No se registró un valor numérico de temperatura, por lo que no fue posible comprobar el funcionamiento del control de lazo cerrado dentro del rango de 36 °C a 37,5 °C.

### 3. Análisis de Resultados

**Análisis 1: Eficacia del control de temperatura y error en el cálculo del peso**

El pesaje resultó el subsistema más logrado. Con una celda de carga de bajo costo, el sistema entregó un valor con un error aproximado menor al 8 % respecto al patrón. Esta exactitud es útil para validar el principio de medición, pero para un neonato resulta limitada: a modo de ejemplo, el 8 % de una masa de 1000 g equivale a 80 g. A esto se suma el tiempo de estabilización de cerca de 1 minuto, que es aceptable para un peso estático, pero largo para un neonato que se mueve sobre la plataforma. No se determinó cuál es la causa del avance gradual de la lectura, lo que queda como punto por analizar en una siguiente iteración.

En la calefacción, la cabina no logró calentarse, y la explicación más probable es que la potencia disponible fue insuficiente. A 12 V, la resistencia de 20 Ω requeriría disipar la siguiente potencia (0.6 A de corriente) para entregar su calor nominal:

$$P_{res} = \frac{V^{2}}{R} = \frac{12^{2}}{20} = 7.2 \text{ W}$$

mientras que el cargador utilizado, de 12 V y 200 mA, puede entregar como máximo:

$$P_{fuente} = V \times I = 12 \times 0.2 = 2.4 \text{ W}$$

es decir, cerca de una tercera parte de lo que la resistencia necesita, y menos aún si el ventilador se alimentó de la misma fuente. Con esa potencia limitada, el flujo de aire del ventilador, que debería distribuir el calor, tiende a disipar el poco que se genera antes de que se acumule en la cabina. Como no se midió la corriente ni la temperatura, esta explicación es una interpretación a partir de las especificaciones de los componentes y no una comprobación experimental.

> [!NOTE]
> Con una corriente de 0.2 A, la caída de tensión en una resistencia de 20 Ω sería de 4 V y la potencia disipada de solo 0.8 W. Este valor es una referencia de orden de magnitud, debido a que el ventilador comparte la fuente y la corriente real no se midió.

**Análisis 2: Comparación con sistemas comerciales en capacidades, limitaciones y precio**

Para la comparación se consultaron las fichas públicas de dos incubadoras comerciales: el Dräger Babyleo TN500 [9] y la línea LEEX B6/B8 [10]. En el caso de Instrumentalia S.A.S. no se encontró una ficha técnica pública con especificaciones que permitiera incluirla en la comparación.

**Tabla 2.** Comparación del prototipo con incubadoras comerciales.

| <p align="center"> Característica </p> | <p align="center"> Prototipo </p> | <p align="center"> Dräger Babyleo TN500 [9] </p> | <p align="center"> LEEX B6/B8 [10] </p>|
|:---|:---|:---|:---|
| Calefacción y control de temperatura | Ventilador de 12 V y resistencia de 20 W / 20 Ω; sin calentamiento apreciable | Calefacción convectiva en modo incubadora y calefactor radiante en modo cuna; colchón calefactado opcional; ajuste de aire de 20 a 39 °C y de piel de 34 a 38 °C, en pasos de 0,1 °C | 7 canales de medición y 3 protecciones independientes de límite de calor |
| Humedad | No incluida en el alcance de la práctica | Ajuste de 30 a 99 % de humedad relativa | Humidificación activa |
| Oxígeno | No incluido en el alcance de la práctica | Opcional, ajuste de 21 a 65 % | Oxigenación asistida opcional |
| Pesaje | Celda de carga de 10 kg; error aproximado menor al 8 % y estabilización de cerca de 1 min | Báscula integrada opcional, para pacientes de hasta 10 kg | Báscula digital opcional |
| Cubierta | Acrílico transparente | Capota con cambio automático entre modo incubadora y modo cuna | Doble pared y cortina de aire |
| Alarmas y monitoreo | Pantalla LCD con el valor del peso | Alarmas ópticas y acústicas | Pantalla táctil de 8 in; monitoreo de signos vitales opcional (ECG, SpO2, presión no invasiva, respiración y CO2) |
| Precio | $150.000 COP | $190.000.000 | $28.000.000 |

En capacidades, la diferencia principal es la regulación de la temperatura. Los equipos comerciales ajustan por separado la temperatura del aire y de la piel con una resolución de 0,1 °C, combinan varias fuentes de calor y añaden protecciones independientes contra sobrecalentamiento, mientras que el prototipo no logró calentar la cabina. Humedad, oxígeno, alarmas y monitoreo de signos vitales son también funciones que ofrecen las referencias comerciales y que quedaron fuera del alcance de esta práctica. En el pesaje, en cambio, la solución desarrollada cumple el mismo principio que la báscula opcional de los equipos comerciales, aunque no se dispone en las fichas de su exactitud para compararla con el error del prototipo.

En precio, el prototipo costó $150.000 COP, frente a los $190.000.000 COP del Dräger Babyleo TN500 y los $28.000.000 COP de la línea LEEX B6/B8. La diferencia es considerable: el prototipo representa una fracción mínima del costo de cualquiera de los dos equipos comerciales. Esto se explica por el alcance reducido del prototipo: dos subsistemas básicos, sin las funciones de seguridad, monitoreo y certificación que caracterizan a un equipo clínico.

### 4. Preguntas para la Discusión

**Pregunta 1: ¿Qué otras variables (y por qué) además de las aquí mencionadas son críticas en el monitoreo neonatal?**

La **humedad** es una de las más importantes, ya que los neonatos muy prematuros tienen alta pérdida de agua por evaporación a través de la piel, y las incubadoras incorporan humidificación para limitarla [2], [5]. Los equipos comerciales también ofrecen control de **oxígeno** como opción, además de ajuste de la humedad relativa en un rango definido [9], [10]. Otra variable es la **temperatura de la piel**, distinta de la temperatura del aire: los equipos comerciales permiten usar cualquiera de las dos como referencia de control [9].

En el monitoreo de **signos vitales**, la línea LEEX incluye de forma opcional o estándar el electrocardiograma, la saturación de oxígeno (SpO2), la presión no invasiva, la respiración y el CO2 [10], lo que muestra que la frecuencia cardiaca, la respiración y la oxigenación se consideran parte del monitoreo del neonato. Por último, el **ruido y la luminosidad** dentro de la cabina se han incorporado como variables a vigilar con sensores y alarmas en prototipos de incubadora [1].

**Pregunta 2: ¿Qué haría falta para convertir el sistema desarrollado en una incubadora neonatal real?**

El primer paso es dimensionar la **potencia de calefacción**: según el análisis anterior, la fuente utilizada entrega aproximadamente una tercera parte de la potencia que la resistencia necesita, por lo que se requeriría una fuente y un elemento calefactor adecuados al volumen de la cabina. Luego, un **control de lazo cerrado** con sensores de temperatura calibrados, de aire y de piel, como en los equipos comerciales, que regulan ambos con resolución de 0,1 °C [9].

Para llegar a un equipo clínico también harían falta funciones de seguridad y monitoreo: protecciones independientes contra sobrecalentamiento, como las 3 que tiene la línea LEEX [10], y alarmas ópticas y acústicas [9]. En el pesaje habría que reducir el error y el tiempo de estabilización. Finalmente, el equipo debe cumplir la norma **IEC 60601-2-19**, que establece los requisitos de seguridad básica y desempeño esencial de las incubadoras neonatales [8].

**Pregunta 3: ¿Qué semejanzas hay entre una incubadora neonatal y una servo-cuna?**

Ambas son dispositivos de apoyo a la termorregulación del neonato y comparten el principio de **servocontrol**: miden la temperatura del paciente y ajustan el calor entregado para mantenerla en el valor deseado [2]. El Dräger Babyleo TN500 lo ilustra bien, debido a que integra los dos modos en un mismo equipo: al cerrar la capota funciona como incubadora con calefacción convectiva y, con la capota abierta, como cuna radiante, con ajuste de temperatura de piel en ambos casos y alarmas ópticas y acústicas [9].

La diferencia está en la forma de calentar y en el acceso al paciente: la incubadora es un recinto cerrado con aire calentado, mientras que la cuna radiante es abierta y facilita el acceso, pero aumenta las pérdidas por evaporación, que en la incubadora pueden limitarse elevando la humedad del aire [2].

### 5. Conclusión

La práctica permitió construir un prototipo funcional de incubadora neonatal a escala, con cubierta de acrílico, un módulo de calefacción y un módulo de pesaje, con un costo total de $150.000 COP. El pesaje con una celda de carga de 10 kg resultó viable: el sistema mostró el valor en la pantalla LCD con un error aproximado menor al 8 % y estabilizó la lectura en cerca de 1 minuto. Estos resultados indican que medir el peso con componentes de bajo costo es factible, aunque lograr la exactitud y la rapidez que exige el cuidado de un neonato requiere mejorar la medición. En la temperatura, la cabina no alcanzó un calentamiento apreciable, y el análisis de los componentes sugiere que la potencia de la fuente, de 2.4 W frente a los 7.2 W que la resistencia necesita, fue insuficiente. Por ello, controlar con gran precisión variables como la temperatura es factible en principio, pero exige una fuente de potencia adecuada, sensores calibrados y un control de lazo cerrado como los de los equipos comerciales. Como siguiente paso se recomienda redimensionar la alimentación del módulo de calefacción con una fuente capaz de entregar la corriente que la resistencia necesita, y medir la temperatura de la cabina para validar el control dentro del rango de 36 °C a 37,5 °C. En el módulo de pesaje, conviene identificar la causa del avance gradual de la lectura antes de estabilizarse, con el fin de reducir ese tiempo de respuesta a un valor adecuado para un neonato.

### Referencias

[1] L. Restrepo-Pérez, N. Durango-Londoño, N. Gómez-Suárez, F. González-Ramírez y N. Rivera-Bonilla, "Prototipo de incubadora neonatal," *Rev. Ing. Biomédica*, vol. 1, no. 1, pp. 55–59, may. 2007. [En línea]. Disponible: http://www.scielo.org.co/pdf/rinbi/v1n1/v1n1a12.pdf

[2] L. C. Wrobel, M. K. Ginalski, A. J. Nowak, D. B. Ingham y A. M. Fic, "An overview of recent applications of computational modelling in neonatology," *Philos. Trans. R. Soc. A*, vol. 368, no. 1920, pp. 2817–2834, jun. 2010, doi: 10.1098/rsta.2010.0052.

[3] Universidad Militar Nueva Granada, "Guía de preparación práctica de laboratorio: Diseño y construcción de una incubadora neonatal a escala," Laboratorio de Instrumentación Biomédica y Biosensores, GL-AA-F-1, Rev. 3, sep. 2025.

[4] World Health Organization, "Thermal protection of the newborn: a practical guide," WHO, Ginebra, Suiza, Rep. WHO/RHT/MSM/97.2, 1997. [En línea]. Disponible: https://www.who.int/publications-detail-redirect/WHO_RHT_MSM_97.2

[5] R. B. Knobel-Dail, "Role of effective thermoregulation in premature neonates," *Res. Rep. Neonatol.*, vol. 4, pp. 147–156, 2014, doi: 10.2147/RRN.S52377.

[6] T. L. Bergman, A. S. Lavine, F. P. Incropera y D. P. DeWitt, *Fundamentals of Heat and Mass Transfer*, 7.ª ed. Hoboken, NJ, EE. UU.: Wiley, 2011.

[7] Ningbo David Medical Device, "Incubadora neonatal con ruedas YP-2200B, de altura variable, con pantalla táctil y con monitor," MedicalExpo. [En línea]. Disponible: https://www.medicalexpo.es/prod/ningbo-david-medical-device/product-69526-998666.html

[8] International Electrotechnical Commission, "Medical electrical equipment – Part 2-19: Particular requirements for the basic safety and essential performance of infant incubators," IEC 60601-2-19:2020, Ginebra, Suiza, 2020. [En línea]. Disponible: https://webstore.iec.ch/en/publication/89860

[9] Innolitics, "Babyleo TN500 (K251619)," FDA Device Database. [En línea]. Disponible: https://fda.innolitics.com/device/K251619

[10] LEEX Medical, "B6 / B8 Infant Incubator," LEEX. [En línea]. Disponible: https://leexmedical.com/en/product/b6-b8-b3-infantincubator/

