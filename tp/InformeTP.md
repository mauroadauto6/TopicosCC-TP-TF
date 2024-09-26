**UNIVERSIDAD PERUANA DE CIENCIAS APLICADAS**


**TÓPICOS EN CIENCIAS DE LA COMPUTACIÓN**

**Sección CC82**

**PROFESOR**

Canaval Sanchez, Luis Martín

**INFORME DE TRABAJO PARCIAL**


**Agosto, 2024**      


# **Problemática y Motivación**
## **Problemática**
En el entorno educativo, una de las tareas más complejas y críticas es la planificación y asignación de horarios para los diferentes cursos que se imparten. Esta planificación implica coordinar a profesores, estudiantes y aulas disponibles, asegurando que no existan conflictos de horario y que se cumplan con todas las restricciones operativas de la institución. La complejidad de esta tarea aumenta proporcionalmente con el número de cursos, profesores y aulas disponibles, y cualquier error en la asignación puede tener consecuencias significativas, como:

**Conflictos de Horarios:**
   1. Un profesor asignado a dos cursos en el mismo horario.
   1. Un aula asignada a más de un curso al mismo tiempo.
   1. Estudiantes que deben asistir a dos clases diferentes en el mismo horario.  

**Subutilización de Recursos:**
   1. Aulas vacías durante gran parte del horario lectivo.
   1. Profesores con cargas horarias desbalanceadas, con algunos sobrecargados y otros subutilizados.

**Sobrecapacidad en Aulas:**
   1. Asignación de un aula pequeña a un curso con muchos estudiantes, superando la capacidad física y logística del espacio.

**Dificultad para Ajustar Cambios:**
   1. Cualquier cambio, como la adición de un nuevo curso o la modificación de la disponibilidad de un profesor, puede requerir una reestructuración significativa de todo el horario.


Estas dificultades, además de afectar la operatividad diaria de la institución, impactan negativamente en la experiencia educativa de estudiantes y docentes. La tarea de asignación de horarios se suele realizar manualmente o utilizando herramientas básicas como hojas de cálculo, lo cual es ineficiente y propenso a errores, especialmente en instituciones con un gran número de cursos y restricciones.




# **Motivación**
La asignación de horarios es un problema típico de optimización que puede ser abordado mediante técnicas de programación con restricciones (Constraint Programming, CSP), ya que estas permiten modelar de manera explícita todas las restricciones del problema y buscar una solución que las satisfaga de manera óptima.

**Razones para utilizar CSP en la asignación de horarios:**

1. **Automatización de la Asignación:**

   Utilizar CSP para la asignación de horarios permite automatizar un proceso que de otra manera sería tedioso y propenso a errores. Con la definición adecuada de las restricciones, el sistema puede generar un horario completo y consistente en cuestión de segundos.
1. **Optimización de Recursos:**

   El uso de CSP permite no solo cumplir con todas las restricciones, sino también optimizar el uso de recursos, como asegurar que no haya aulas vacías en horarios pico o balancear la carga horaria entre los profesores.

1. **Flexibilidad y Adaptabilidad:**

   Un modelo CSP bien diseñado permite realizar cambios en las restricciones de manera sencilla. Por ejemplo, si un profesor cambia su disponibilidad o se añade un nuevo curso, el sistema puede reajustar el horario completo sin necesidad de rehacerlo desde cero.
1. **Reducción de Conflictos:**

   Al modelar explícitamente todas las restricciones, el sistema asegura que no haya conflictos de horarios entre profesores, estudiantes y aulas. Esto reduce significativamente los problemas operativos que suelen surgir al inicio de cada ciclo lectivo.
1. **Mejora en la Calidad Educativa:**

   
   Al evitar problemas de sobrecarga de profesores y aulas, y al asegurar que los estudiantes puedan asistir a todas sus clases sin conflictos, se mejora la calidad del entorno educativo, permitiendo una mejor experiencia tanto para estudiantes como para profesores.


# **Objetivos**
## **Objetivo General**
Desarrollar un modelo de programación con restricciones (CSP) para la asignación óptima de horarios en una escuela, asegurando que todas las restricciones de disponibilidad de profesores, capacidad de aulas y conflictos de horarios entre cursos sean respetadas, y que se minimicen los conflictos y la subutilización de recursos.
## **Objetivos Específicos**
1. **Modelar las restricciones del problema en un modelo CSP:**
   Definir las variables, dominios y restricciones necesarias para representar el problema de asignación de horarios, asegurando que se contemplen la disponibilidad de profesores, capacidad de aulas y evitar conflictos de horarios.
1. **Implementar el modelo CSP en Python utilizando la biblioteca python-constraint:**
   Desarrollar el modelo en código, integrando todas las restricciones identificadas y generando soluciones válidas para la asignación de horarios que respeten todas las condiciones del problema.
1. **Validar y optimizar las soluciones generadas:**
   Probar el modelo CSP con datos de prueba, verificar que no existan conflictos en las soluciones obtenidas y optimizar el uso de recursos (aulas y profesores), buscando el balance óptimo entre las restricciones y la eficacia del horario generado.









# **Diseño de Solución**
El diseño de solución se centra en la implementación de un modelo de Programación con Restricciones (CSP) para la asignación óptima de horarios en una institución educativa. El objetivo principal es asegurar que todas las restricciones de disponibilidad de profesores, capacidad de aulas y conflictos de horarios entre cursos sean respetadas. A continuación, se detallan los pasos y componentes clave del diseño de solución:
## **Modelado del Problema con CSP**
- **Definición de Variables:**

  Se definen variables para cada curso, las cuales representan la asignación de un aula, un horario y un día específico.
- **Dominios:**

  Cada variable tiene un dominio que incluye todas las combinaciones posibles de aulas, horarios y días en los que se puede asignar el curso.
- **Restricciones:**

  Se modelan varias restricciones para garantizar que las soluciones generadas sean válidas y óptimas:
    - **Capacidad de Aulas:** Asegura que la cantidad de estudiantes no exceda la capacidad máxima del aula asignada.
    - **Conflictos de Horarios:** Evita que más de un curso se asigne al mismo aula, horario y día.
    - **Distribución Equitativa:** Garantiza que se utilicen todas las aulas disponibles y que no se concentren todos los cursos en un solo día o aula.
    - **Disponibilidad de Profesores:** Asegura que los profesores no se asignen a más de un curso al mismo tiempo.
  
## **Implementación en Python usando python-constraint**
- **Configuración del Modelo:**

  Se utiliza la biblioteca python-constraint para modelar el problema con todas las restricciones identificadas.
- **Definición del Problema:**

  Se crea un objeto Problem() y se añaden variables, dominios y restricciones mediante funciones addVariable() y addConstraint().
- **Validación de Soluciones:**

  Se utiliza el método getSolutions() para obtener todas las soluciones posibles que cumplan con las restricciones definidas.
## **Optimización de la Solución**
- **Evaluación de Soluciones:**

  Se aplica un criterio de evaluación para seleccionar la mejor solución en función de la distribución equilibrada de aulas y horarios.
- **Penalización y Selección:**

  Se utiliza una función de puntaje para penalizar las soluciones que no cumplen con la distribución ideal de horarios y aulas. La solución con el puntaje más bajo es seleccionada como la mejor.
## **Validación y Pruebas**
- **Pruebas de Consistencia:**

  Se prueban diferentes combinaciones de cursos, aulas y horarios para asegurar que el modelo puede manejar casos complejos y garantizar la validez de las soluciones generadas.
- **Evaluación de Escenarios de Cambio:**

  Se simulan cambios en la disponibilidad de profesores o la adición de nuevos cursos para evaluar la adaptabilidad del modelo CSP.

## **Resultados Esperados**
- **Optimización el Uso de Recursos:**

  Se espera una utilización óptima de las aulas y una distribución balanceada de la carga horaria de los profesores.
- **Reducción de Conflictos:**

  Al modelar explícitamente todas las restricciones, se minimizan los conflictos de horario y se evita la sobrecarga o subutilización de recursos.
- **Adaptabilidad a Cambios:**

  El modelo puede ajustarse fácilmente a cambios en las restricciones o a la adición de nuevas variables sin necesidad de reestructurar completamente el horario.






# **Desarrollo de Solución**
Se definieron tres aulas con capacidades variables, y se generaron aleatoriamente la cantidad de estudiantes para cada curso, asegurando que el total de estudiantes se imprimiera en consola. 

Luego, se establecieron restricciones para garantizar que ningún curso excediera la capacidad de su aula asignada y que no se usara un aula por más de un curso a la vez en el mismo horario y día. 

Después de buscar todas las soluciones posibles, se calculó el uso de aulas en cada asignación y se identificó la mejor solución, que minimiza la cantidad de aulas utilizadas, presentando finalmente la asignación óptima de cursos junto con sus respectivas aulas, horarios y días.
## **Definición del Problema y Variables**
Tomamos en cuenta las variables Cursos, Aulas, Horarios y Días.


## **Definición de Restricciones**
Se definen las siguientes restricciones:

- Un curso no puede ser asignado a un aula que tenga menos capacidad que el número de estudiantes inscritos en el curso.
- Un aula no puede ser utilizada por más de un curso al mismo tiempo en el mismo día.
- Se busca que los cursos se asignen de manera que se utilicen el máximo número posible de aulas diferentes.

## **Búsqueda de Soluciones y Selección de la Mejor Opción**
Búsqueda de soluciones:

- Se exploran todas las posibles combinaciones de asignaciones de aulas, horarios y días para cada curso, considerando las restricciones impuestas.
- Cada combinación generada se evalúa para verificar que cumpla con todas las restricciones definidas.

Selección de la mejor opción:

- Se selecciona la solución que maximiza el uso de diferentes aulas para mejorar la distribución de los cursos y evitar la concentración en un mismo espacio.
- La solución que utiliza el mayor número de aulas distintas se considera la mejor opción para evitar sobrecargas en aulas específicas.


# **Conclusión**
El diseño de solución propuesto garantiza la asignación eficiente de horarios mediante la utilización de técnicas de programación con restricciones. La implementación en Python facilita la validación y optimización de las soluciones, asegurando un modelo flexible y robusto capaz de manejar las complejidades típicas del entorno educativo. Este enfoque no solo resuelve la problemática inicial, sino que también proporciona una herramienta adaptable para futuras necesidades y cambios.

La programación con restricciones (CSP) es una herramienta eficaz para resolver problemas complejos de asignación, como la distribución de cursos en aulas. Utilizando variables y restricciones precisas, se logran soluciones óptimas que maximizan el uso de los recursos disponibles y optimizan la planificación académica. CSP permite explorar múltiples combinaciones y seleccionar la mejor opción, demostrando su aplicabilidad en contextos educativos y logísticos.