| Nombre | Cuenta de GitHub |
| --- | --- |
| Luisa Toro | @30-Luisaatoro9 |
| Antonia Améstica | @04-antoniaamc |
| Sebastián Guevara | @14-sebastianguevaralarotta |
| Catalina Jeria | @15-catalinajeria |
| Catalina Balboa | @05-Catabalboa |

## 1. Criterios de diseño del sistema

El presente proyecto fue desarrollado en el marco del Taller de Máquinas y Electrónica, una asignatura cuyo desafío principal consistió en diseñar y fabricar un sintetizador modular mediante el trabajo colaborativo. Bajo esta modalidad, cada grupo del curso asumió la tarea de desarrollar un módulo electrónico distinto, los cuales finalmente se integrarían para conformar un único instrumento musical. Nuestro proceso se adaptó estrictamente a la realidad material y económica del curso en Chile, gestionando un presupuesto acotado mediante la organización de cuotas de $15.000 y, en ciertos casos, de $8.000 para distribuir los costos a lo largo del semestre. Los componentes se adquirieron principalmente en locales especializados del sector de San Diego, en Santiago, y se complementaron con materiales facilitados por el Laboratorio de Investigación y Desarrollo (LID) para la fase de pruebas y prototipos.

Desde el punto de vista conceptual, la propuesta formal del sistema nace de una narrativa poética y de una analogía geológica: la llegada de un objeto desconocido proveniente del espacio. Un meteorito aterrizó en la Tierra desatando interrogantes inmediatas: ¿Por qué tiene cables? ¿Las luces significan algo? ¿Qué nos está tratando de decir? ¿Es solo ruido o algo más?

Para comprender su naturaleza, el diseño se inspiró en las geodas del desierto. Las geodas son formaciones rocosas que presentan un exterior simple, sobrio y rústico, pero que al abrirse revelan un interior parcialmente o totalmente cristalizado y brillante. Esta dualidad define el eje estético del proyecto: los cristales y la luz interna del meteorito parecen pugnar por salir a través de los orificios de la carcasa para no pasar desapercibidos. De este modo, el concepto de observación se convierte en la directriz del diseño. La luz emerge desde el centro de la estructura, revelando gradualmente sus componentes y estableciendo una relación íntima entre la exploración espacial, la contemplación de los fenómenos naturales y la experimentación sonora. La tecnología no se oculta, se expone deliberadamente para invitar al usuario a descubrir cómo cada módulo transforma el sonido y cómo la interacción física modifica la experiencia musical, transformando la electrónica en un paisaje visualmente contemplable.

## 2. Placas Utilizadas 

Durante el proceso de ensamble y pruebas en el taller, el proyecto decantó en dos grupos de circuitos: los que lograron integrarse exitosamente para formar el instrumento final, y los que, pese a haber sido soldados, debieron ser descartados del montaje por fallas o inestabilidad.

### Placas en funcionamiento (Sistema Final)

| Módulo | Origen / Grupo | Función Principal |
| --- | --- | --- |
| *Reloj (RELO)* | Cátedra / Profesores | Generador de pulsos de sincronía temporizados. |
| *Secuenciador CD4017* | Primer Circuito | Control de pasos rítmicos distribuidos (Ver Nota Final). |
| *Lub-dub* | Grupo 06 | *Oscilador* (Fuente principal de señal de audio activa). |
| *Filtro Paso Bajo Activo* | Grupo 05 | Filtro Analógico VCF soldado sobre cobre desnudo. |

### Placas soldadas pero no utilizadas (Descartadas)

| Módulo | Origen / Grupo | Estado / Observación |
| --- | --- | --- |
| *Secuenciador* | Grupo 02 | Descartado por inestabilidad en la cadena general. |
| *Comando Estelar* | Grupo 03 | Soldado, pero no integrado al flujo definitivo. |
| *Chirigüe Mecanizado* | Grupo 04 | Oscilador original descartado por fallas en placa. |
| *PARLA* | LID | Módulo de salida descartado. |

<img width="4284" height="5712" alt="placassoldadas (1)" src="https://github.com/user-attachments/assets/7a6c7361-5821-4a31-b6c8-485b19ad3d10" />

## 3. Funcionamiento de las placas

### Placa 1: RELO 

<img width="457" height="452" alt="Captura de pantalla 2026-07-07 103418" src="https://github.com/user-attachments/assets/f5a45aad-1e66-4a6a-b226-b7a545588fac" />


Este módulo funciona como el reloj del sistema, es el encargado de dictar el "tiempo" o la velocidad de todo el sintetizador. Sin él, el sistema no tendría una referencia para avanzar y, por lo tanto, no habría ritmo. Su función es generar constantemente una señal eléctrica llamada "onda cuadrada" (un pulso que sube y baja de voltaje a un ritmo constante), que sale hacia el secuenciador para marcarle el paso a cada uno de sus movimientos. Esta placa fue diseñada por nuestros profesores de cátedra.

* *Señal de Salida:* Emite una onda cuadrada que es el pulso maestro del sintetizador.
* *Recepción y Envío:* Actúa como la fuente emisora que alimenta directamente al Secuenciador CD4017, sincronizando todos los procesos temporales del instrumento.

### Placa 2: Oscilador

<img width="502" height="742" alt="Captura de pantalla 2026-07-07 103206" src="https://github.com/user-attachments/assets/8555494d-ce35-4d63-a36f-764804ab63ba" />

### Placa 3: Secuenciador

<img width="739" height="1600" alt="secuenciadorprocesoplaca" src="https://github.com/user-attachments/assets/6150ad38-d900-4894-bb25-28eb2d001fc4" />


El secuenciador toma el pulso rítmico que viene del RELO y, con cada pulso, activa un marcador. Apenas llega al cuarto paso, vuelve a empezar inmediatamente sin pausas. Así, transformamos un simple pulso eléctrico en un bucle rítmico continuo, indicándole a la máquina exactamente en qué momento debe actuar.

Para entender este módulo de forma sencilla, imaginen un contador de cuatro tiempos. El secuenciador no genera ningún sonido por sí mismo, su trabajo es ir activando luces y marcando ritmos uno tras otro siguiendo el "tic-tac" del metrónomo. 

Originalmente, nuestro plan era utilizar la PCB diseñada por el *Grupo 06 (Contador Binario)* para cumplir con esta función. Sin embargo, tras ensamblar la placa, el circuito no funcionó. Frente a este imprevisto, tomamos la decisión técnica de descartarla y construir una solución alternativa desde cero. Para ello, decidimos utilizar el esquemático original entregado por nuestro profesor de cátedra y *soldar los componentes directamente a mano sobre una placa de contacto (PCB genérica perforada) que teníamos a libre disposición en el taller. Estructurando el circuito en torno al integrado **CD4017* (un contador de década).

> * *Diseño Original:* Documentación técnica y esquemático base provisto por la Cátedra del Taller de Máquinas Electrónicas.

## 4. Proceso de armado de cada placa (prueba y error)

Rediseño completo de la placa filtro:

### Filtro Paso Bajo Activo — Grupo 05

El circuito que realizamos corresponde a un *filtro pasabajos activo*. Su función es dejar pasar principalmente las frecuencias bajas, que corresponden a los graves, mientras que reduce las frecuencias altas o agudos. Este tipo de circuito se utiliza en equipos de audio cuando se quiere obtener un sonido más grave, por ejemplo en un subwoofer.

Se llama filtro *activo* porque utiliza un componente electrónico activo, que en este caso es el integrado *JRC4558, el cual necesita alimentación para poder funcionar. En nuestro montaje decidimos utilizar una alimentación de **5 V*, obtenida desde una salida USB de una batería recargable. Aunque el esquema original suele alimentarse con un voltaje mayor, durante las pruebas comprobamos que con 5 V el circuito funcionó correctamente para la aplicación que necesitábamos.

#### Recorrido de la señal
La señal de audio entra por el terminal llamado *Audio Input*. Esa señal puede venir desde un teléfono, un computador o cualquier dispositivo que entregue audio. Antes de llegar al integrado, la señal pasa por una combinación de resistencias, capacitores y el potenciómetro de frecuencia. Todos estos componentes trabajan juntos para determinar qué frecuencias van a pasar y cuáles se van a atenuar.

Después de ser procesada por el integrado, la señal pasa por el potenciómetro de volumen y finalmente sale por *Audio Output*, lista para conectarse a un amplificador o a un parlante.

#### Alimentación
El circuito necesita alimentación porque el JRC4558 no puede funcionar por sí solo. En nuestro caso decidimos utilizar una fuente de *5 V* desde un adaptador de corriente AC/DC. El terminal positivo entrega la energía al integrado y el terminal G corresponde a la tierra o negativo común del circuito. Todos los componentes utilizan esa referencia para funcionar correctamente.

# Carcasa

### 5. Influencias y referentes para la carcasa

Para el diseño de nuestras carcasas, estos fueron nuestros referentes:

1. *Bleep Labs:* Firma icónica en la manufactura de sintetizadores experimentales. Su filosofía operativa plantea que la electrónica debe hablar el mismo idioma que la interfaz visual. El circuito no debe ser un secreto técnico confinado a una caja ciega; debe ser un elemento vivo que explica de forma transparente el origen del flujo eléctrico y sonoro, estrechando el vínculo entre el músico, la máquina y la onda sonora resultante.
   <img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/f1e88226-c6fa-4811-ad29-7b0e547f98be" />


3. Sled Dog, de 2001, un reproductor de CD modificado que permite rascarlo con la mano. Imagen © Simon Lonergan, 2001.
   <img width="1200" height="998" alt="image" src="https://github.com/user-attachments/assets/17bed07c-aa80-412d-8adb-1c1cfaf87233" />

4. *Yoko Ono (Composición Activa):* La disposición de los controles y la apertura de las carcasas dialogan con las teorías de participación artística planteadas por Yoko Ono. En sus postulados teóricos, el valor del arte no descansa en la rigidez del objeto estático, sino en las dinámicas humanas y las experiencias que se desencadenan cuando el espectador interactúa con él. Bajo este enfoque, nuestro sintetizador modular renuncia a la caja cerrada tradicional para invitar activamente al usuario a un viaje de descubrimiento perceptivo.

## 6. Arquitectura Estructural de las Carcasas

La carcasa de nuestro instrumento trasciende la idea de ser un simple contenedor protector. Se concibe como un manifiesto formal y material cuya meta es resguardar, estructurar, revelar y comunicar de manera clara la trama electrónica que ocurre en su interior. En perfecta sincronía con nuestra metáfora de la Tierra y el Cielo (el meteorito y el telescopio), decidimos que el sistema final no habitara en una sola caja ciega, sino en *dos carcasas físicas diferenciadas* que dialogan entre sí a través del contraste de sus materiales y procesos de fabricación.


<img width="3000" height="4000" alt="carcasa02" src="https://github.com/user-attachments/assets/f77e9826-d338-4d34-a972-3229a855df4f" />


### Carcasa 1: Geoda

Esta unidad funciona como el "núcleo rítmico" y sonoro del sistema. Contiene dos placas interconectadas que operan de forma conjunta:
* El módulo *Secuenciador* 
* El módulo *Lub-Dub (Oscilador/Percutor, Grupo 06)*.

Para representar la caída del meteorito, el caos y su conexión con la Tierra, esta carcasa fue *construida completamente a mano*, alejándonos por completo de la fabricación digital. Su base se conforma por una estructura alámbrica recubierta con papel aluminio para generar el soporte estructural. Sobre esto, se modeló el volumen con cerámica en frío para lograr la textura rocosa, finalizando con un trabajo de pintura. 

El detalle más íntimo de esta pieza se encuentra en su interior: cristales adheridos a mano que simulan el corazón cristalizado de una geoda real. Las luces LED de los circuitos actúan como indicadores visuales del "latido" del sistema, brillando y refractándose a través de estos cristales internos para asomarse hacia el exterior, invitando al observador a mirar dentro de la roca.

### Carcasa 2: Filtro

Esta segunda carcasa está dedicada exclusivamente al módulo del *Filtro Paso Bajo (VCF) del Grupo 05*. A diferencia de la rusticidad orgánica de la Geoda, esta unidad representa la precisión, el "cielo" y la observación estructurada.

Su arquitectura se compone de placas de acrílico transparente cortadas mediante tecnología láser. El vector de corte sigue fielmente el contorno perimetral de la PCB, respetando la silueta inspirada en las líneas de un tocadiscos y la expansión de ondas sonoras, presente desde nuestras primeras etapas de diseño. La placa inferior actúa como base del chasis y la superior como panel de control e interfaz. Ambas caras se mantienen firmemente unidas y distanciadas mediante pernos M3 y espaciadores.

<img width="1280" height="1280" alt="image" src="https://github.com/user-attachments/assets/3592eb42-8975-4571-bfc5-819c5a324e97" />


## Partitura

Un meteorito llegó desde el espacio ¿por qué tiene cables? ¿las luces significan algo?¿que nos están tratando de decir?¿es solo ruido o algo mas?... Los científicos intentan capturar este sonido y necesitan descifrarlo ¿seremos capaces?¿será que aún no estamos listos?... 

Primero necesitamos entender su forma, en la tierra hay unas rocas que se llaman “Geodas”, estas son rocas son una formación geológica en el cual su interior está parcialmente o totalmente cristalizado. Los cristales de este meteorito son parecidos a una Geoda, será que… la luz en su interior y los cristales, ¿están tratando de salir por los orificios para que no pase desapercibida?

## bibliografía

https://econtact.ca/20_3/collins_cdhacking.html 
