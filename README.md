# Simulación y Monitoreo de Variables Cardiovasculares y Hemodinámicas

Instrumentación Biomédica y Biosensores, Ingeniería Biomédica, UMNG (Semestre VII).

## Integrantes
- María José Peña Velandia - 5600876
- Antonia Garzón Vanegas - 5600843
- Ana Sofia Conde Porras - 5600770

## Objetivo general

## Objetivos específicos

## Resumen de la práctica 

## Estructura del repositorio

## Conclusión general

# Parte A — 
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

## 7. Análisis de la señal fotopletismográfica
La señal fotopletismográfica permite observar las variaciones del volumen sanguíneo periférico durante cada pulsación cardíaca.

Durante las pruebas se pueden relacionar sus características con las condiciones simuladas:
- **Bradicardia:** los pulsos aparecen más separados debido a la menor frecuencia cardíaca.
- **Saturación baja:** permite observar la señal mientras el simulador representa una condición de menor oxigenación.
- **Low Perfusion:** se espera una reducción de la amplitud de la onda debido a la menor intensidad del componente pulsátil.
- **Taquicardia:** los pulsos aparecen más próximos entre sí debido al incremento de la frecuencia cardíaca.

# Parte C — 

## Preguntas para la discusión

## Conclusiones

# Bibliografía
[1]

[2] 

