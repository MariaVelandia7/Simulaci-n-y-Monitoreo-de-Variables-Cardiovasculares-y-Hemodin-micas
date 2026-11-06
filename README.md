# Simulación y Monitoreo de Variables Cardiovasculares y Hemodinámicas

Instrumentación Biomédica y Biosensores, Ingeniería Biomédica, UMNG (Semestre VII).

## Integrantes
- María José Peña Velandia - 5600876
- Antonia Garzón Vanegas - 5600843
- Ana Sofia Conde Porras - 5600770

## Objetivo general
Operar con el simulador Pronk OxSim (OX-1) y el monitor de signos vitales uMEC 100 para pruebas funcionales.

## Objetivos específicos
• Identificar los modos de operación de un simulador de parámetros
hemodinámicos (Pronk OxSim).
• Verificar los límites de medición de un monitor de signos vitales mediante
simulación de variables hemodinámicas.
• Interpretar variaciones en los parámetros hemodinámicos asociadas a
estados fisiológicos y patológicos.

## Resumen de la práctica 
En esta práctica se verificó el funcionamiento del monitor de signos vitales usando el simulador óptico de pulsioximetría como referencia. Primero se hizo una revisión bibliográfica de ambos equipos, de sus principios de operación, de los parámetros que se pueden simular y de los errores máximos permitidos según la normativa y la ficha técnica del fabricante. Luego se dejó el monitor en modo de monitorización, se acopló el sensor al dedo artificial del simulador y se evaluaron cuatro condiciones: bradicardia, saturación baja, baja perfusión y taquicardia. En cada una se compararon los valores simulados con los medidos, se calcularon los errores absoluto y porcentual, se verificó si las alarmas debían activarse según los límites configurados y se registró el tiempo de respuesta de la alarma sonora. Finalmente, se discutió el principio de operación del simulador y por qué una mala perfusión puede generar falsas alarmas de SpO2 baja.

## Estructura del repositorio
Parte A – Revisión bibliográfica: descripción de los equipos, procedimiento para el modo monitor, parámetros simulables y errores máximos permitidos.
Parte B – Verificación de alarmas y errores de medición: resultados experimentales, cálculo de errores, verificación de alarmas, tiempos de respuesta y análisis.
Parte C – Preguntas para la discusión: principio de operación del OxSim OX-1 y falsos positivos de SpO2 en mala perfusión.

## Conclusión general
La práctica permitió comprobar que el monitor reproduce de forma confiable los valores de SpO2 y frecuencia de pulso generados por el simulador, con errores nulos o muy pequeños y dentro de las tolerancias declaradas por el fabricante. También permitió ver cómo las condiciones de la señal, en particular la baja perfusión, y la configuración de los límites influyen en la medición y en el comportamiento de las alarmas. Más allá de los valores obtenidos, el trabajo mostró que un simulador sirve como verificación funcional de toda la cadena de medición (sensor, cable y monitor), pero no reemplaza una calibración ni un estudio in vivo.

# Parte A — Revisión bibliográfica
### Introducción a la revisión

Antes de la práctica se hizo una revisión bibliográfica para reunir información técnica sobre los dos equipos: el monitor de signos vitales **Mindray uMEC 100** y el simulador de parámetros hemodinámicos **Pronk OxSim OX-1**. Se consultaron el manual de operación de la serie uMEC, la ficha técnica oficial del uMEC 100/120/150, las especificaciones publicadas por Pronk Technologies y sus distribuidores, la patente que describe el principio de funcionamiento del simulador y la norma internacional **ISO 80601-2-61**, que establece los requisitos particulares de seguridad básica y funcionamiento esencial de los pulsioxímetros. La información obtenida con apoyo de herramientas de inteligencia artificial se contrastó con estas fuentes, como lo pide la guía de laboratorio.

### Descripción general de los equipos

| Equipo | Fabricante | Tipo de dispositivo | Función en la práctica |
|---|---|---|---|
| Monitor de signos vitales **uMEC 100** con sensor de SpO2 | Shenzhen Mindray Bio-Medical Electronics Co., Ltd. (China) | Monitor de paciente multiparamétrico | Equipo bajo prueba. Mide la saturación periférica de oxígeno (SpO2), la frecuencia de pulso (PR) y el índice de perfusión (PI), muestra la onda pletismográfica y genera alarmas cuando los valores salen de los límites configurados. |
| Simulador **Pronk OxSim OX-1** | Pronk Technologies Inc. (EE. UU.) | Simulador óptico / probador funcional de pulsioximetría | Patrón de referencia funcional. Genera combinaciones predefinidas de SpO2, frecuencia de pulso y perfusión que representan condiciones fisiológicas y patológicas. |

#### Monitor de signos vitales Mindray uMEC 100

El uMEC 100 hace parte de la serie uMEC de Mindray (uMEC 100, 120 y 150). Es un monitor portátil de cabecera pensado para monitorizar de forma continua a pacientes adultos, pediátricos y neonatales en hospitalización, urgencias, recuperación y cuidados intermedios. Tiene pantalla táctil, teclas físicas de acceso rápido, batería interna recargable y almacenamiento de tendencias y eventos. Según la configuración, puede medir ECG, respiración, SpO2, frecuencia de pulso, presión arterial no invasiva (PANI) y temperatura. El módulo de SpO2 es de tecnología Mindray y cumple la norma ISO 80601-2-61.

**Especificaciones técnicas relevantes (ficha técnica Mindray):**

| Característica | Especificación del uMEC 100 |
|---|---|
| Peso | 3,5 kg (configuración estándar con batería, sin registrador ni accesorios) |
| Dimensiones | 300 × 210 × 165 mm |
| Pantalla | Táctil a color de 10,1 pulgadas, 1024 × 600 píxeles |
| Canales de forma de onda | Hasta 8 |
| Norma de SpO2 | ISO 80601-2-61 |
| Módulo de SpO2 | Mindray |
| Rango de SpO2 | 0 a 100 % |
| Resolución de SpO2 | 1 % |
| Exactitud de SpO2 | ±2 % (70–100 %, adulto/pediátrico); ±3 % (70–100 %, neonato); no especificada entre 0 y 69 % |
| Tiempo de actualización de SpO2 | ≤ 2 s |
| Índice de perfusión (PI) | Disponible |
| Tono variable según SpO2 (*pitch tone*) | Disponible |
| Rango de frecuencia de pulso (desde SpO2) | 20 a 300 lpm |
| Exactitud de frecuencia de pulso (desde SpO2) | ±3 lpm |
| Tiempo de actualización de PR | ≤ 2 s |

#### Simulador Pronk OxSim OX-1

El OxSim OX-1 es un simulador **óptico** de pulsioximetría de tamaño bolsillo (6,4 × 6,4 × 3,2 cm sin contar el dedo; unos 140 g sin pila). En lugar de conectarse eléctricamente al monitor, tiene un "dedo" artificial fijo sobre el que se pone el sensor de SpO2. Así se prueba la cadena completa: el sensor (LED y fotodiodo), el cable de extensión y el monitor. Sus características principales son:

- Funciona con **dos botones**: uno enciende el equipo y el otro recorre los modos.
- **Detecta automáticamente el tipo de sensor**, así que no hay que indicarle el fabricante del oxímetro que se va a probar.
- Se alimenta con una pila AA o con un adaptador de 6 VDC. La pila dura mínimo 8 horas de uso y el equipo entra en modo de reposo si pasan 10 minutos sin sensor.
- El dedo es permanente: no necesita cables adaptadores ni piezas de reemplazo.
- Carcasa de policarbonato, probada con 65 caídas desde 1 m sin fallas.
- Tiene un puerto serial opcional para ampliar los valores de saturación, frecuencia de pulso e índice de perfusión.
- Incluye un certificado de calibración y tiene garantía limitada de cuatro años.

---

### a. ¿Cómo colocar el uMEC 100 en modo "monitor"?

El manual de operación de la serie uMEC (capítulo 3, sección 3.7 *Operating Modes*) describe varios modos de operación: **modo monitorización**, **modo nocturno**, **modo privacidad**, **modo espera (Standby)** y **modo demostración**. El modo monitorización (*Monitoring Mode*) es el modo clínico que más se usa para vigilar al paciente, y **el monitor entra en él automáticamente al encenderse**.

**Procedimiento para dejar el uMEC 100 en modo monitor:**

1. **Verificar la alimentación:** conectar el monitor a la red eléctrica con el cable de alimentación o revisar que la batería interna tenga carga suficiente.
2. **Encender el equipo:** presionar el botón de encendido del panel frontal y esperar a que termine el autodiagnóstico de arranque.
3. **Comprobar el modo:** al terminar el arranque, el monitor entra directamente en modo monitorización y muestra la pantalla principal con las áreas de parámetros y de formas de onda.
4. **Configurar al paciente:** en **Menú principal → Gestión de pacientes** se elige la **categoría del paciente** (Adulto, para esta práctica). Esto importa porque los límites de alarma por defecto y la exactitud declarada dependen de la categoría.
5. **Conectar el sensor de SpO2:** conectar el cable y el sensor tipo pinza al conector de SpO2 del monitor. Cuando el sensor detecta un pulso válido (en el paciente o en el simulador), aparecen el valor de SpO2, la frecuencia de pulso, el índice de perfusión (si está habilitado) y la onda pletismográfica (Pleth).
6. **Revisar alarmas:** confirmar que las alarmas no estén en pausa ni silenciadas antes de empezar las pruebas.

**Si el monitor está en modo espera (Standby):**

El modo espera detiene temporalmente la monitorización sin apagar el monitor. Se entra con la tecla rápida **Standby** o con **Menú principal → Gestión de pacientes → Standby**. En este modo el monitor detiene todas las mediciones y desactiva las alarmas y los mensajes, excepto la alarma de batería baja. Para volver al modo monitor hay dos opciones:

- **Reanudar monitorización** (*Resume monitor*): sale del modo espera y sigue monitorizando al paciente actual.
- **Monitor**: sale del modo espera y admite un paciente nuevo.

Según el manual, al salir del modo espera y reanudar la monitorización, las alarmas quedan en pausa durante dos minutos y después se reactiva el sistema de alarmas. Por eso, si el monitor venía de Standby, una alarma puede tardar en activarse aunque el valor simulado ya supere el límite configurado, algo que hay que tener en cuenta al medir los tiempos de respuesta.

**Modos de operación del uMEC 100:**

| Modo | Descripción | Uso en la práctica |
|---|---|---|
| Monitorización | Modo normal de trabajo clínico; mide y genera alarmas. | Es el modo que se usa |
| Nocturno | Baja el brillo y el volumen de las alarmas para no molestar al paciente. | No recomendado, porque las alarmas audibles se oyen menos |
| Privacidad | Oculta los datos en la pantalla local; solo se ven en la central de monitorización. | No se usa |
| Espera (Standby) | Detiene mediciones y alarmas. | No se usa |
| Demostración | Muestra formas de onda y valores ficticios para capacitación. | No se usa, porque los datos no son reales |

---

### b. ¿Qué parámetros o variables fisiológicas pueden simularse con el Pronk OxSim OX-1? Explique cada uno.

El OxSim OX-1 simula **cuatro valores de saturación (85, 95, 98 y 99 %), tres frecuencias de pulso (40, 80 y 140 lpm) y dos niveles de perfusión (normal y baja)**, combinados en **cinco modos predefinidos**:

| Modo | SpO2 | Frecuencia de pulso | Índice de perfusión (PI) | Condición clínica que representa |
|---|---|---|---|---|
| 1 | 85 % | 80 lpm | ≈ 2,0 | **Hipoxemia / desaturación** con frecuencia normal |
| 2 | 95 % | 40 lpm | ≈ 2,0 | **Bradicardia** con saturación normal |
| 3 | 98 % | 80 lpm | ≈ 2,0 | **Adulto sano** (valores normales) |
| 4 | 98 % | 140 lpm | ≈ 2,0 | **Taquicardia** con saturación normal |
| 5 | 99 % | 80 lpm | ≈ 0,2 | **Baja perfusión** (*Low Perfusion*) |

A continuación se explica cada parámetro.

#### 1. Saturación periférica de oxígeno (SpO2)

La SpO2 es el porcentaje de hemoglobina de la sangre arterial que transporta oxígeno (oxihemoglobina, HbO2) respecto a la hemoglobina total capaz de transportarlo, medido de forma no invasiva por pulsioximetría:

$$SpO_2 = \frac{HbO_2}{HbO_2 + Hb} \times 100\%$$

**Principio de medición:** el sensor tiene, de un lado, dos LED, uno rojo (≈ 660 nm) y uno infrarrojo (≈ 900–940 nm), y del otro un fotodiodo. La oxihemoglobina absorbe más luz infrarroja y deja pasar más luz roja; la desoxihemoglobina (Hb) absorbe más luz roja. Según la ley de Beer-Lambert, la luz que llega al fotodiodo tiene dos componentes:

- **Componente DC (continua):** absorción constante de piel, hueso, tejido, sangre venosa y sangre arterial no pulsátil.
- **Componente AC (pulsátil):** variación de la absorción por el aumento del volumen arterial en cada latido.

El monitor calcula la **razón de razones** R:

$$R = \frac{(AC/DC)_{rojo}}{(AC/DC)_{infrarrojo}}$$

y la convierte en SpO2 con una **curva de calibración empírica (curva R)**, propia de cada fabricante y obtenida en estudios con voluntarios. En muchos oxímetros, R ≈ 0,5 corresponde a SpO2 ≈ 100 % y R ≈ 1,0 a SpO2 ≈ 85 %.

**Interpretación clínica:**

| Rango de SpO2 | Interpretación |
|---|---|
| 95–100 % | Normal en adultos sanos a nivel del mar |
| 91–94 % | Hipoxemia leve (puede ser normal en altura, como en Bogotá, o en pacientes con EPOC) |
| 86–90 % | Hipoxemia moderada |
| ≤ 85 % | Hipoxemia severa; requiere intervención inmediata |

**Valores que simula el OX-1:** 85 % (hipoxemia severa, modo 1), 95 % (límite inferior normal, modo 2), 98 % (normal, modos 3 y 4) y 99 % (normal-alto, modo 5).

#### 2. Frecuencia de pulso (PR, *Pulse Rate*)

Es el número de pulsaciones arteriales periféricas por minuto. En pulsioximetría se calcula a partir del **periodo de la onda pletismográfica** (el tiempo entre picos consecutivos de la componente AC), no a partir del ECG:

$$PR\,[lpm] = \frac{60}{T_{pulso}\,[s]}$$

En condiciones normales, la frecuencia de pulso es igual a la frecuencia cardíaca (HR). Pueden diferir cuando hay arritmias con latidos que no generan un pulso periférico efectivo (déficit de pulso), por ejemplo en la fibrilación auricular o con extrasístoles.

**Interpretación clínica (adulto en reposo):**

| Rango | Interpretación |
|---|---|
| < 60 lpm | **Bradicardia** (puede ser fisiológica en deportistas o patológica por bloqueos AV, hipotiroidismo, fármacos, hipotermia) |
| 60–100 lpm | Normal |
| > 100 lpm | **Taquicardia** (fiebre, dolor, ansiedad, hipovolemia, hipoxemia, arritmias) |

**Valores que simula el OX-1:** 40 lpm (bradicardia marcada, modo 2), 80 lpm (normal, modos 1, 3 y 5) y 140 lpm (taquicardia, modo 4).

#### 3. Índice de perfusión (PI)

El índice de perfusión es la relación porcentual entre la componente pulsátil (AC) y la componente no pulsátil (DC) de la señal infrarroja:

$$PI = \frac{AC_{IR}}{DC_{IR}} \times 100\%$$

Indica qué tan fuerte es el pulso en el sitio del sensor, es decir, **cuánta sangre arterial pulsátil llega al tejido** (perfusión periférica). Su rango típico va de 0,02 % (pulso muy débil) a 20 % (pulso muy fuerte). Un PI bajo puede deberse a vasoconstricción por frío, hipotermia, hipovolemia, shock, vasopresores o mala colocación del sensor. En los manuales de Mindray, un PI mayor que 1 se considera óptimo, entre 0,3 y 1 aceptable, y por debajo de 0,3 se recomienda reposicionar el sensor.

**Valores que simula el OX-1:** PI ≈ 2,0 (perfusión normal, modos 1 a 4) y PI ≈ 0,2 (baja perfusión, modo 5). El modo 5 queda por debajo del umbral de 0,3, así que pone a prueba la capacidad del monitor para medir con una señal débil.

#### 4. Onda fotopletismográfica (Pleth)

No es un valor numérico, sino la representación gráfica de la componente AC en el tiempo. Su forma refleja el pulso arterial: una subida rápida (sístole), un pico, una bajada más lenta y, en ocasiones, una muesca dícrota (cierre de la válvula aórtica). En el monitor:

- El **periodo** de la onda determina la frecuencia de pulso.
- La **amplitud** se relaciona con la perfusión: a menor PI, onda más pequeña o "aplanada".
- La **regularidad** de la forma indica la calidad de la señal: una onda irregular o con ruido sugiere artefacto por movimiento o mala colocación del sensor.

El OX-1 genera esta onda modulando la luz que devuelve al sensor, así que en el uMEC 100 se puede observar cómo cambia la onda con cada modo (más frecuente en taquicardia, más espaciada en bradicardia y de menor amplitud en baja perfusión).

---

### c. En el ámbito clínico, ¿cuáles son las tolerancias o errores máximos permitidos (EMP) para cada parámetro fisiológico mencionado en la parte (b)?

La referencia normativa internacional para los pulsioxímetros es la **ISO 80601-2-61**, que el uMEC 100 declara cumplir. Esta norma exige que el fabricante **declare** la exactitud de SpO2 y de frecuencia de pulso en sus documentos y fija un límite máximo para la exactitud de SpO2. En Colombia, el INVIMA clasifica los monitores de signos vitales como dispositivos médicos de riesgo IIb, y en los programas de mantenimiento y metrología biomédica se toma como EMP el valor que declara el fabricante, siempre que sea igual o más estricto que el de la norma.

#### Exactitud de SpO2: el concepto de A<sub>rms</sub>

La ISO 80601-2-61 expresa la exactitud de SpO2 como el **error cuadrático medio (A<sub>rms</sub>)** entre la lectura del pulsioxímetro y la saturación arterial de referencia (SaO2), medida con un CO-oxímetro en muestras de sangre arterial durante estudios de hipoxia controlada en voluntarios sanos:

$$A_{rms} = \sqrt{\frac{\sum_{i=1}^{n}(SpO_{2,i} - SaO_{2,i})^2}{n}}$$

La norma exige **A<sub>rms</sub> ≤ 4 %** en el rango de SaO2 de 70 a 100 %. Como A<sub>rms</sub> es un valor estadístico, solo alrededor de dos tercios de las lecturas caen dentro de ±A<sub>rms</sub> del valor real.

#### Tabla de errores máximos permitidos

| Parámetro | Límite de la norma ISO 80601-2-61 | EMP declarado por Mindray para el uMEC 100 | EMP usado en este informe | Observaciones |
|---|---|---|---|---|
| **SpO2** | A<sub>rms</sub> ≤ 4 % en 70–100 % | **±2 %** (70–100 %, adulto/pediátrico); ±3 % (neonato); no especificada entre 0–69 % | **±2 puntos porcentuales** | Todos los valores simulados (85, 95, 98, 99 %) están dentro del rango de 70–100 %, donde aplica la exactitud declarada. |
| **Frecuencia de pulso (PR)** | El fabricante debe declarar la exactitud de PR; puede verificarse con simulador | **±3 lpm** en 20–300 lpm | **±3 lpm** | En términos relativos: ±7,5 % a 40 lpm, ±3,75 % a 80 lpm y ±2,1 % a 140 lpm. |
| **Índice de perfusión (PI)** | Sin EMP normativo | Sin exactitud declarada (solo "disponible") | **Evaluación cualitativa** | El PI es un indicador relativo que depende del algoritmo y del sensor de cada fabricante; el propio OX-1 lo especifica como "aproximado". Se evalúa si el monitor detecta la baja perfusión y sigue dando SpO2 y PR válidos. |
| **Tiempo de actualización** | — | ≤ 2 s para SpO2 y PR | Referencia para el análisis | Sirve para analizar los tiempos de respuesta medidos en la Parte B. |
| **Alarmas** | IEC 60601-1-8: el fabricante debe declarar los retardos de las alarmas | Retardo de alarma configurable por el usuario | Activación correcta (sí/no) y tiempo de respuesta | Una alarma debe activarse siempre que el valor medido cruce el límite configurado. |

#### Fórmulas de error usadas en la verificación

$$E_{abs} = |V_{medido} - V_{simulado}|$$

$$E_{\%} = \frac{|V_{medido} - V_{simulado}|}{V_{simulado}} \times 100\%$$

**Criterio de aceptación:**
- SpO2: si E<sub>abs</sub> ≤ 2 % → **CUMPLE**
- PR: si E<sub>abs</sub> ≤ 3 lpm → **CUMPLE**

#### Limitación de la verificación con simulador

La ISO 80601-2-61 (anexo sobre simuladores, calibradores y probadores funcionales) y los manuales de Mindray aclaran que **un probador funcional o simulador no puede usarse para evaluar la exactitud de un pulsioxímetro**. Solo demuestra que el monitor reproduce correctamente la curva de calibración de su fabricante y que el sistema sensor–cable–monitor funciona y genera alarmas. La exactitud real de SpO2 solo se puede determinar *in vivo*, comparando las lecturas del pulsioxímetro con muestras de sangre arterial analizadas con un CO-oxímetro. En cambio, **la exactitud de la frecuencia de pulso sí puede verificarse con un simulador**. Por eso, los errores de SpO2 calculados en la Parte B deben interpretarse como una **verificación funcional** del equipo y no como una calibración.

# Parte B -VERIFICACIÓN DE ALARMAS Y ERRORES DE MEDICIÓN
## 1. Resultados experimentales

### 1.1. Tabla general de mediciones
Se realizaron cuatro pruebas modificando las condiciones de simulación y los límites de alarma del monitor.

| Prueba | Frecuencia simulada (bpm) | SpO2 simulada (%) | Límite superior SpO2(%) | Límite inferior SpO2 (%) | Tiempo hasta la alarma (s) |
|---|:---:|:---:|:---:|:---:|:---:|
| Bradicardia | 40 | 95 | 100 | 90 | 42,5 |
| Saturación baja | 80 | 85 | 100 | 90 | 86,3 |
| Low Perfusion | 80 | 99 | 100 | 90 | 19,4 |
| Taquicardia | 140 | 98 | 97 | 90 | 24,4 |

### 1.2. Valores mostrados por el monitor uMEC 100

| Prueba | FC simulada (bpm) | FC medida (bpm) | SpO2 simulada (%) | SpO2 medida (%) |
|---|:---:|:---:|:---:|:---:|
| Bradicardia | 40 | 40 | 95 | 95 |
| Saturación baja | 80 | 80 | 85 | 85 |
| Low Perfusion | 80 | 80 | 99 | 100 |
| Taquicardia | 140 | 140 | 98 | 98 |

## 2. Cálculo de errores absolutos y porcentuales
Para evaluar la diferencia entre los valores establecidos en el simulador y los registrados en el monitor se utilizaron las siguientes expresiones:

**Error absoluto:**  
<img width="86" height="26" alt="image" src="https://github.com/user-attachments/assets/67e055eb-3364-4ada-91dd-7ec18a8653a4" />  
**Error porcentual:**  
<img width="131" height="39" alt="image" src="https://github.com/user-attachments/assets/b04e0b2d-09ea-4d6d-8ab5-42052dff34c1" />  

Donde:
- V_s: valor simulado por el Pronk OxSim OX-1.
- V_m: valor medido por el monitor uMEC 100.
- E_a: error absoluto.
- E_p: error porcentual.

### 2.1. Prueba 1: Bradicardia (40 bpm y 95 % SpO2)
**Frecuencia cardíaca:**  
<img width="137" height="59" alt="image" src="https://github.com/user-attachments/assets/53b238e5-8d4d-4e29-8958-1c09274b85e6" />  
**Saturación de oxígeno:**  
<img width="125" height="55" alt="image" src="https://github.com/user-attachments/assets/f4734c3a-2f4f-4cba-94ee-76ad56126450" />  
Los resultados indican que los valores mostrados por el monitor coincidieron exactamente con los valores establecidos en el simulador.

### 2.2. Prueba 2: Saturación baja (80 bpm y 85 % SpO2)
**Frecuencia cardíaca:**  
<img width="143" height="63" alt="image" src="https://github.com/user-attachments/assets/5dee202a-da64-414b-afde-2a3cbf828b4c" />  
**Saturación de oxígeno:**  
<img width="122" height="61" alt="image" src="https://github.com/user-attachments/assets/6c265eff-94aa-402c-b7cb-a1d4f1043197" />  
En esta prueba se obtuvo una coincidencia exacta entre los valores simulados y los valores medidos por el monitor.
### 2.3. Prueba 3: Low Perfusion (80 bpm y 99 % SpO2)
**Frecuencia cardíaca:**  
<img width="143" height="71" alt="image" src="https://github.com/user-attachments/assets/59db91d3-81a1-41e2-b589-8777c529bc57" />  
**Saturación de oxígeno:**  
<img width="160" height="58" alt="image" src="https://github.com/user-attachments/assets/482dd36b-69f9-4aa5-9590-fb7e2aa98461" />  
En esta condición se presentó una diferencia de un punto porcentual entre la saturación simulada y la medida por el monitor, equivalente a un error porcentual de 1,01 %.

### 2.4. Prueba 4: Taquicardia (140 bpm y 98 % SpO2)
**Frecuencia cardíaca:**  
<img width="152" height="62" alt="image" src="https://github.com/user-attachments/assets/259c1c5f-3af9-454d-9cc2-2a12bbf2efa5" />  
**Saturación de oxígeno:**  
<img width="134" height="65" alt="image" src="https://github.com/user-attachments/assets/21cde936-92b1-47f4-b4f6-41a219d1dc79" />  
Los valores registrados coincidieron exactamente con los establecidos en el simulador.

## 3. Tabla de errores

| Prueba | Variable | Valor simulado | Valor medido | Error absoluto | Error porcentual |
|---|---|:---:|:---:|:---:|:---:|
| Bradicardia | FC | 40 bpm | 40 bpm | 0 bpm | 0 % |
| Bradicardia | SpO2 | 95 % | 95 % | 0  | 0 % |
| Saturación baja | FC | 80 bpm | 80 bpm | 0 bpm | 0 % |
| Saturación baja | SpO2 | 85 % | 85 % | 0  | 0 % |
| Low Perfusion | FC | 80 bpm | 80 bpm | 0 bpm | 0 % |
| Low Perfusion | SpO2 | 99 % | 100 % | 1  | 1,01 % |
| Taquicardia | FC | 140 bpm | 140 bpm | 0 bpm | 0 % |
| Taquicardia | SpO2 | 98 % | 98 % | 0  | 0 % |

## 4. Verificación de alarmas
Para analizar el comportamiento esperado de las alarmas se compararon las mediciones con los límites de saturación configurados en el monitor.

| Prueba | SpO2 medida | Límite inferior | Límite superior | Condición | Alarma esperada por SpO2 |
|---|:---:|:---:|:---:|---|---|
| Bradicardia | 95 % | 90 % | 100 % | Dentro del rango | No |
| Saturación baja | 85 % | 90 % | 100 % | Inferior al límite | Sí, baja |
| Low Perfusion | 100 % | 90 % | 100 % | Dentro del rango | No |
| Taquicardia | 98 % | 90 % | 97 % | Superior al límite | Sí, alta |

## 5. Análisis de los tiempos de respuesta
Los tiempos registrados corresponden al intervalo desde que se configuró el parámetro en el simulador hasta que se escuchó la alarma sonora del monitor.

| Prueba | Tiempo de respuesta |
|---|:---:|
| Bradicardia | 42,5 s |
| Saturación baja | 86,3 s |
| Low Perfusion | 19,4 s |
| Taquicardia | 24,4 s |

El tiempo promedio se calculó mediante:  
<img width="221" height="107" alt="image" src="https://github.com/user-attachments/assets/71bfef27-0741-404a-b2b6-7952b392e4c2" />  
El rango de variación fue:  
<img width="134" height="90" alt="image" src="https://github.com/user-attachments/assets/b3a6f27d-0677-4b54-b623-618fab195c66" />  

La prueba de saturación baja presentó el mayor tiempo registrado, con 86,3 segundos, mientras que la prueba *Low Perfusion* presentó el menor, con 19,4 segundos.

Estos resultados muestran que los tiempos de activación sonora variaron entre las condiciones evaluadas. Sin embargo, para interpretar el comportamiento de cada alarma es necesario considerar el parámetro que generó la alerta y sus límites de configuración.

## 6. Análisis de resultados

### 6.1. Prueba de bradicardia
En esta prueba se simuló una frecuencia cardíaca de 40 bpm y una saturación de oxígeno del 95 %. El monitor presentó exactamente los mismos valores, obteniéndose un error absoluto y porcentual de cero para ambas variables.

La saturación se encontraba dentro del rango configurado de 90 % a 100 %, por lo que no se esperaba una alarma por saturación. La activación de una alarma por frecuencia cardíaca baja dependía del límite inferior de FC establecido en el equipo.

### 6.2. Prueba de saturación baja
Se configuró una frecuencia cardíaca de 80 bpm y una saturación de oxígeno de 85 %. El monitor registró exactamente los valores simulados, con errores de medición iguales a cero.

Como la saturación se encontraba por debajo del límite inferior de 90 %, se esperaba la activación de la alarma correspondiente a SpO2 baja. Esta prueba permitió evaluar la capacidad del monitor para identificar condiciones de desaturación.

### 6.3. Prueba Low Perfusion
Se utilizó el modo *Low Perfusion* del simulador, configurado para representar una saturación de 99 % y una frecuencia cardíaca de 80 bpm. El monitor presentó una frecuencia de 80 bpm y una saturación de 100 %.

Se obtuvo un error absoluto de un punto porcentual y un error relativo de 1,01 % para SpO2. Esta diferencia puede relacionarse con las condiciones de baja perfusión, en las que disminuye la intensidad de la señal pulsátil utilizada para estimar la saturación.

Aunque la saturación medida se encontraba dentro del rango de alarma de 90 % a 100 %, esta prueba permitió estudiar las limitaciones de la pulsioximetría cuando la señal presenta una intensidad reducida.

### 6.4. Prueba de taquicardia
En esta prueba se simuló una frecuencia cardíaca de 140 bpm y una saturación de oxígeno de 98 %. El monitor mostró exactamente los mismos valores, obteniéndose errores absolutos y porcentuales de cero.

El límite superior de SpO2 se había configurado en 97 %, por lo que el valor de 98 % superaba el límite establecido y se esperaba la activación de una alarma por saturación elevada.

También se debía evaluar la alarma de frecuencia cardíaca elevada, cuya activación dependía del límite superior de FC configurado.
# Parte C — Discusión

## Preguntas para la discusión
### Pregunta 1: ¿Cuál es el principio de operación del Pronk OxSim OX-1 para simular una onda pulsátil?

El Pronk OxSim OX-1 es un **simulador óptico de transmisión de luz**. A diferencia de los simuladores electrónicos, que inyectan señales eléctricas al monitor por el cable del sensor, el OX-1 interactúa con la **luz** que emite el sensor real, como lo haría el dedo de un paciente. Su principio de funcionamiento está descrito en la patente de Pronk Technologies US 7,346,378 B2 (*Light transmission simulator for pulse oximeter*) y se puede dividir en cinco etapas:

**1. Captación de la luz del sensor.**
El sensor del monitor tiene dos LED (rojo e infrarrojo) que se encienden de forma alternada y muy rápida, a una frecuencia mucho mayor que la del corazón. El dedo artificial del OX-1 tiene un **fotodetector** alineado con esos LED que capta cada destello.

**2. Separación y sincronización de los canales rojo e infrarrojo.**
Un circuito separador distingue cuáles destellos son rojos y cuáles infrarrojos, y el simulador se sincroniza con la secuencia de encendido del oxímetro. Así sabe en qué momento debe devolver la luz "roja" y en qué momento la "infrarroja". En esta etapa también identifica automáticamente el tipo o fabricante del sensor, lo que le permite usar la curva de calibración (curva R) correcta.

**3. Generación de la componente continua (DC).**
Mediante sus propios LED, controlados por amplificadores de voltaje a corriente, y una **guía óptica**, el simulador envía luz al fotodiodo del sensor con una intensidad base atenuada. Esto imita la absorción constante de piel, hueso, tejido y sangre venosa de un dedo real.

**4. Modulación de la componente pulsátil (AC): la onda pulsátil.**
La intensidad de la luz devuelta se **modula en amplitud** con una forma de onda pletismográfica almacenada en el simulador, que se repite a la frecuencia seleccionada (40, 80 o 140 lpm). Esta modulación reproduce el aumento y la disminución del volumen de sangre arterial en cada latido. El monitor detecta esa variación periódica, dibuja la onda Pleth y calcula la frecuencia de pulso a partir de su periodo.

**5. Ajuste de la relación rojo/infrarrojo (SpO2) y de la profundidad de modulación (PI).**
- La profundidad de modulación se ajusta **por separado** en el canal rojo y en el infrarrojo. La relación entre ambas define la razón R = (AC/DC)<sub>rojo</sub> / (AC/DC)<sub>IR</sub>. El simulador elige R para que, en la curva de calibración del fabricante detectado, corresponda a la saturación deseada (85, 95, 98 o 99 %).
- La **profundidad global** de la modulación (relación AC/DC) determina el índice de perfusión: una modulación relativamente grande da PI ≈ 2,0 (perfusión normal) y una muy pequeña da PI ≈ 0,2 (baja perfusión).

**Resumen del principio:**

| Variable simulada | Qué controla el OX-1 |
|---|---|
| Frecuencia de pulso | La **frecuencia** con que se repite la modulación de la luz |
| SpO2 | La **relación** entre la modulación del canal rojo y la del infrarrojo (razón R) |
| Índice de perfusión | La **profundidad** (amplitud relativa AC/DC) de la modulación |
| Forma de la onda Pleth | La **forma de onda** almacenada que se usa para modular |

**Ventajas y limitaciones del principio óptico:** al trabajar con luz, el OX-1 prueba la cadena completa de medición (LED y fotodiodo del sensor, cable y monitor), así que también detecta fallas del sensor o del cable. Sin embargo, al depender de curvas R programadas y no de sangre real, **es un probador funcional y no un patrón de calibración**. No reproduce la absorción real de la hemoglobina, el efecto del color de la piel, la sangre venosa pulsátil, el movimiento ni la presencia de dishemoglobinas (carboxihemoglobina, metahemoglobina). Además, el OX-1 tiene solo cinco modos fijos, por lo que no permite simular arritmias, desaturaciones progresivas, artefactos por movimiento ni valores intermedios.

---

### Pregunta 2: ¿Por qué la SpO2 baja puede ser un falso positivo (falsa alarma) en una situación de mala perfusión?

Un **falso positivo** de SpO2 baja ocurre cuando el monitor muestra una saturación por debajo del límite de alarma y activa la alarma de desaturación, aunque la saturación arterial real del paciente (SaO2) sea normal. Esto pasa con frecuencia en la **mala perfusión** por las siguientes razones:

**1. La señal pulsátil es muy pequeña (baja relación señal/ruido).**
La pulsioximetría depende por completo de la componente pulsátil (AC) de la señal. Con mala perfusión (PI bajo), el AC puede ser menos del 0,3 % de la señal total. En esas condiciones, el ruido electrónico del sensor, la luz ambiental, las interferencias eléctricas, los temblores, el movimiento del paciente y las pulsaciones de la sangre venosa tienen un tamaño comparable al de la señal arterial. El algoritmo del monitor puede confundir ese ruido con el pulso y calcular un valor de R erróneo.

**2. El ruido tiende a llevar la razón R hacia 1, y R ≈ 1 equivale a una SpO2 cercana a 85 %.**
El ruido y los artefactos de movimiento suelen afectar de forma parecida a los canales rojo e infrarrojo. Cuando el ruido domina, las variaciones de ambos canales se parecen y la razón R se acerca a 1. En la mayoría de curvas de calibración, **R = 1 corresponde a una SpO2 aproximada de 85 %**. Por eso, cuando la señal es tan débil que el ruido domina, el oxímetro tiende a mostrar valores bajos (≈ 80–85 %) aunque el paciente esté bien oxigenado, y se dispara la alarma de SpO2 baja.

**3. La medición es periférica y no refleja la oxigenación central.**
El pulsioxímetro mide en el dedo o el lóbulo de la oreja. En la vasoconstricción periférica (frío, hipotermia, hipovolemia, shock, dolor, uso de vasopresores, enfermedad vascular periférica, Raynaud) llega muy poca sangre al sitio del sensor. La medición local se degrada, aunque la sangre arterial central esté bien saturada. El problema está en la **perfusión del tejido**, no en la **oxigenación** del paciente.

**4. La sangre venosa pulsátil contamina la medición.**
Con mala perfusión o movimiento, la sangre venosa (menos saturada) también puede "pulsar" dentro del lecho de medición. Como la pulsioximetría convencional asume que solo pulsa la sangre arterial, incluye esa sangre desoxigenada en el cálculo y subestima la SpO2.

**5. Promediado, congelamiento y pérdida de señal.**
Para compensar el ruido, los monitores alargan los tiempos de promediado o retienen el último valor válido. Esto produce lecturas inestables, valores que suben y bajan bruscamente o caídas momentáneas por debajo del límite que generan alarmas transitorias sin significado clínico.

**Consecuencias clínicas: la fatiga de alarmas.**
Las falsas alarmas tienen consecuencias importantes. Estudios sobre pulsioximetría convencional reportan que el movimiento y la baja perfusión pueden explicar hasta el **90 % de las falsas alarmas** en unidades de cuidado intensivo y salas de recuperación. El exceso de falsas alarmas lleva a la **fatiga de alarmas**: el personal se acostumbra al sonido, tarda en responder, baja el volumen o desactiva las alarmas, y puede pasar por alto un evento real de hipoxemia. Por esta razón, los fabricantes han desarrollado algoritmos avanzados de procesamiento de señal (por ejemplo, Masimo SET o el algoritmo antiinterferencias de Mindray) para separar la señal arterial del ruido y reducir las falsas alarmas.

Además, la mala perfusión no solo produce falsos positivos: también puede producir **falsos negativos**. Estudios recientes muestran que un índice de perfusión bajo aumenta el error de la SpO2 y que, combinado con una pigmentación oscura de la piel, puede llevar a que el oxímetro **sobrestime** la saturación y no detecte una hipoxemia real.

**¿Cómo identificar una falsa alarma en la práctica clínica?**
Antes de actuar ante una alarma de desaturación, se recomienda:
1. **Revisar la onda pletismográfica:** una onda plana, irregular, con ruido o de amplitud muy baja indica artefacto; una onda limpia y regular respalda que la lectura es real.
2. **Revisar el índice de perfusión:** un PI menor a 0,3 indica que la lectura no es confiable.
3. **Comparar la frecuencia de pulso del oxímetro con la frecuencia cardíaca del ECG:** si no coinciden, el oxímetro probablemente está leyendo ruido.
4. **Evaluar al paciente clínicamente** (coloración, estado de conciencia, frecuencia respiratoria) y, si hay duda, confirmar con gases arteriales.
5. **Mejorar la señal:** calentar la extremidad, reposicionar el sensor, cambiar el sitio de medición (por ejemplo, al lóbulo de la oreja) o usar un sensor adecuado para baja perfusión.

**Relación con los resultados de la Parte B:**
En la prueba de *Low Perfusion* (OxSim modo 5: SpO2 = 99 %, PR = 80 lpm, PI ≈ 0,2), el uMEC 100 mostró la única diferencia en SpO2 de toda la práctica: un error absoluto de 1 punto (1,01 %). Ese error está dentro del EMP de ±2 % declarado por Mindray, pero confirma lo explicado arriba: al reducirse la perfusión, la señal pulsátil es más débil, la medición se vuelve menos estable y aumentan el error y la probabilidad de lecturas o alarmas falsas. En esta condición también se espera una onda pletismográfica de menor amplitud y más distorsionada que en los demás modos.

## Conclusiones
La práctica buscó determinar si el monitor de signos vitales Mindray uMEC 100 mide correctamente la saturación de oxígeno (SpO2) y la frecuencia de pulso frente a los valores generados por el simulador óptico Pronk OxSim OX-1, y si activa las alarmas cuando los valores cruzan los límites configurados. Para ello se simularon cuatro condiciones (bradicardia, saturación baja, baja perfusión y taquicardia), en las que se registraron los valores del monitor, se calcularon los errores y se midió el tiempo hasta la alarma sonora. Los errores fueron nulos o muy pequeños en todas las condiciones y se mantuvieron dentro de las tolerancias declaradas por el fabricante, por lo que el equipo cumple el criterio de aceptación. La única desviación apareció en baja perfusión, la condición en la que la señal pulsátil es más débil, lo que coincide con lo discutido sobre la pérdida de estabilidad de la medición y el aumento de falsas alarmas. Los tiempos de respuesta de la alarma variaron bastante entre pruebas, lo que sugiere que dependen no solo del valor simulado, sino también de los límites configurados y del retardo propio del monitor.

Estos resultados son importantes porque permiten verificar el funcionamiento de la cadena completa de medición (sensor, cable y monitor) y confirmar que el equipo detecta condiciones de desaturación y de límites superados. Sin embargo, como un simulador no sustituye un estudio in vivo con CO-oxímetro, los resultados deben interpretarse como una verificación funcional y no como una calibración. Para mejorar la práctica, se podrían repetir las mediciones varias veces por condición para tener una base estadística más sólida, evaluar también la alarma de frecuencia cardíaca, registrar el índice de perfusión y la onda Pleth en cada modo, y medir los tiempos con un método más preciso partiendo siempre del mismo estado del monitor. Finalmente, sería útil comparar con otro monitor o con un simulador que permita valores intermedios, arritmias y artefactos de movimiento, para acercarse más a condiciones clínicas reales.

# Bibliografía
[1] Instituto de Salud Pública de Chile (ISP), "Guía para la Clasificación de Dispositivos Médicos según Riesgo," ISPCH, Santiago, Chile, Guía técnica, 2021. [En línea]. Disponible: https://www.ispch.cl/sites/default/files/Guia_de_Clasificacion_de_Dispositivos_Medicos_Segun_riesgo_Formato_Institucional.pdf

[2] Instituto Nacional de Vigilancia de Medicamentos y Alimentos (INVIMA), *ABC de Dispositivos Médicos – Guía Reguladora*, Bogotá, Colombia. [En línea]. Disponible: https://www.invima.gov.co/

[3] Medical IT, "Metrología Biomédica – OxSim," [En línea]. Disponible: https://www.medicalitech.com/producto/ox-sim/

[4] Shenzhen Mindray Bio-Medical Electronics Co., Ltd., *uMEC Series Patient Monitor Operator's Manual (uMEC 60/70/80/100/120/150)*, Shenzhen, China. [En línea]. Disponible: https://www.mindray.com/content/dam/xpace/en/site/mdr-sscp/patient-monitor/umec-series-60-70-80-100-120-150-safety-and-performance-information.pdf

[5] Shenzhen Mindray Bio-Medical Electronics Co., Ltd., *uMEC 100/120/150 Patient Monitor – Data Sheet*, P/N ENG-uMEC 100/120/150-210285X4P-20230628, 2023.

[6] Pronk Technologies Inc., *OX-1 OxSim® Optical SpO2 Pulse Oximeter Tester – Especificaciones técnicas*. [En línea]. Disponible: https://www.medwrench.com/equipment/3862/pronk-technologies-ox-1-oxsim

[7] McKesson Medical-Surgical, "Pronk Technologies OX-1 OxSim Pulse Oximeter Simulator – Product Specifications." [En línea]. Disponible: https://mms.mckesson.com/product/1252995/Pronk-Technologies-Inc-OX-1

[8] K. A. Ruiter (Pronk Technologies Inc.), "Light transmission simulator for pulse oximeter," Patente US 7,346,378 B2, 2008. [En línea]. Disponible: https://patents.google.com/patent/US7346378

[9] ISO 80601-2-61:2017, *Medical electrical equipment — Part 2-61: Particular requirements for basic safety and essential performance of pulse oximeter equipment*, International Organization for Standardization, Ginebra, 2017.

[10] IEC 60601-1-8, *Medical electrical equipment — Part 1-8: General requirements, tests and guidance for alarm systems in medical electrical equipment and medical electrical systems*, International Electrotechnical Commission.


