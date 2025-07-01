# **Proyecto:** Mapeo y Navegación de Espacios Conceptuales en Modelos de Lenguaje: De Ideologías Políticas a Actitudes Emergentes

## **Objetivo General:**
Investigar la factibilidad de identificar, aplicar y trazar "transformaciones" vectoriales en el espacio de activación de Modelos de Lenguaje Grandes (LLMs) para mapear cambios conceptuales entre posturas políticas, como conservadora y liberal, y revelar la arquitectura de estas actitudes dentro del modelo.

## **Justificación y Relevancia:**
Los Modelos de Lenguaje Grandes (LLMs) son capaces de inferir y representar propiedades de "agentes" (como autores o personas) a partir de texto. Esto incluye la capacidad de modelar intenciones comunicativas y creencias abstractas. Además, los LLMs pueden simular comportamientos humanos y adoptar distintas "personas", lo cual es crucial para diversas aplicaciones, desde la investigación en ciencias sociales hasta la generación de datos sintéticos.

Investigaciones recientes han demostrado que las representaciones internas de los LLMs no solo codifican el significado del texto, sino también información sobre el "estado del mundo" y las "intenciones comunicativas" de los agentes. Un hallazgo clave es que **las ideologías políticas, como el conservadurismo y el liberalismo, se representan en regiones más "distintas" dentro del espacio de activación del LLM**, a diferencia de, por ejemplo, las perspectivas éticas, que muestran un mayor solapamiento (poliosemia).

La interpretability mecánica, especialmente a través del uso de **autoencoders dispersos (SAEs)**, ha avanzado significativamente, permitiendo descomponer las activaciones internas de los modelos en "características" (features) que son "altamente interpretables y monosemánticas" (es decir, corresponden a conceptos únicos y comprensibles). Estas características han demostrado ser **causalmente importantes** para el comportamiento del modelo, y su manipulación directa, a través de lo que se conoce como "vectores de dirección" (steering vectors), puede controlar propiedades y comportamientos del modelo, como el sentimiento o incluso la "alineación". La "realineación emergente" ha demostrado que pequeñas cantidades de datos benignos pueden restaurar eficientemente un modelo desalineado.

Este proyecto se basa en la premisa de que, si los LLMs representan estas ideologías como "direcciones" o "características" interpretables, podríamos identificar y manipular estas representaciones para comprender cómo se interconectan los conceptos dentro de estas posturas.

## **Fases del Proyecto:**

**Fase 1: Identificación de la Transformación entre Posturas Políticas**

1.  **Objetivo:** Averiguar la transformación que define la posición de una postura política conservadora frente a una posición liberal.
    *   **Metodología:**
        *   **Selección de Modelos:** Se utilizarán LLMs de última generación, como Llama3-8B-Instruct o GPT-4o, conocidos por su capacidad para seguir instrucciones y codificar información detallada sobre personas y actitudes.
        *   **Recopilación de Datos:** Se curarán o generarán datasets de "persona-específicos" que contengan declaraciones y textos que reflejen explícitamente actitudes políticas conservadoras y liberales. Estos statements estarán etiquetados según la actitud que representen ("MATCHINGBEHAVIOR" o "NOTMATCHINGBEHAVIOR"). Se buscará diversidad cultural y geográfica en los datos, aunque las limitaciones de los datasets actuales (a menudo centrados en perspectivas WEIRD y política estadounidense) se reconocerán como un factor a considerar.
        *   **Análisis de Activaciones con SAEs:** Se entrenarán **autoencoders dispersos (SAEs)** sobre las activaciones internas de los LLMs. Los SAEs descompondrán estas activaciones en un conjunto de características subyacentes que son más interpretables que las neuronas individuales.
        *   **Localización de Ideologías:** Utilizando técnicas como **Deep Scan** y análisis de componentes principales (PCA), se identificarán las capas y subespacios de activación donde las ideologías políticas están más distintamente localizadas. La investigación de Cintas et al. ya indica que las ideologías políticas se encuentran en regiones "más distintas" dentro del espacio de representación.
        *   **Definición de la Transformación:** La "transformación" entre una postura conservadora y una liberal se definirá como un conjunto específico de características SAE o un "vector de dirección" en el espacio de activación que capture la diferencia conceptual entre ambas. Esto se logrará identificando las características que se activan diferencialmente o que cambian de magnitud al pasar de contextos conservadores a liberales.

**Fase 2: Aplicación y Exploración de Conceptos Relacionados**

2.  **Objetivo:** Dada la transformación identificada, aplicarla a conceptos básicos relacionados con la postura política original, y revelar cuáles son los conceptos a los que se llega.
    *   **Metodología:**
        *   **Intervenciones Causales ("Steering"):** Una vez que el "vector de transformación" (o el conjunto de SAE latentes) que representa la transición de "conservador" a "liberal" (o viceversa) ha sido identificado, se utilizarán técnicas de "steering" o manipulación de activaciones. Esto implica agregar una "múltiple" del vector de decodificación de los SAE latentes relevantes a las activaciones de los tokens en las capas identificadas.
        *   **Aplicación a Conceptos Base:** Se seleccionarán conceptos clave asociados a la política (ej., "economía", "educación", "salud", "seguridad") y se generarán representaciones de estos conceptos bajo la influencia de la postura política original (ej., "economía conservadora"). Luego, se aplicará la transformación identificada.
        *   **Revelación de Conceptos Resultantes:** Se utilizarán métodos de **autointerpretación**, donde un LLM se encarga de generar explicaciones legibles de las características que se activan en las nuevas representaciones. Esto permitirá entender cómo los conceptos como "economía" cambian de "economía conservadora" a "economía liberal" en el modelo, y cuáles son las nuevas ideas o asociaciones que emergen. Se buscarán descripciones del modelo sobre sus propias "creencias" y "deseos" subyacentes.
        *   **Análisis de Comportamiento:** Se evaluará si el modelo, al ser "steered" hacia la nueva postura, cambia su comportamiento al responder preguntas sobre esos conceptos, por ejemplo, si un modelo previamente conservador ahora genera respuestas con un sesgo liberal sobre "salud".

**Fase 3: Mapeo Conceptual y Rutas de Transformación**

3.  **Objetivo:** Determinar si estas transiciones suponen el camino de menor resistencia, y componiendo las transformaciones de diferentes componentes, construir un mapa conceptual dinámico de las actitudes.
    *   **Metodología:**
        *   **Eficiencia de la Transformación:** Se cuantificará la "resistencia" o "eficiencia" de la transformación mediante la minimización de la magnitud de la intervención necesaria para lograr un cambio conceptual significativo. La literatura ya muestra la eficiencia de las intervenciones de "steering" y de la "realineación" con datos mínimos, sugiriendo que existen caminos de "menor resistencia" inherentes a la forma en que los modelos organizan la información.
        *   **Mapeo de la Arquitectura Conceptual:**
            *   Se utilizará un enfoque de **"model-diffing"**, comparando las activaciones del modelo en diferentes puntos a lo largo de la "transformación" (ej., 0% liberal, 25% liberal, 50% liberal, etc.). Esto permitirá identificar qué características SAE se activan o modifican en cada etapa, construyendo una "trayectoria conceptual".
            *   La descomposición de activaciones en un gran número de características interpretables por los SAEs permitirá una visión granular de cómo los diferentes "componentes" conceptuales (ej., la perspectiva sobre impuestos, la regulación ambiental, etc.) se desplazan.
            *   Se generarán visualizaciones (potencialmente utilizando métodos como UMAP para la reducción de dimensionalidad) que representen este **"mapa conceptual"**, mostrando no solo la arquitectura de la actitud original y la de destino, sino también los puntos intermedios y las relaciones entre los conceptos que evolucionan durante la transformación. Esto podría revelar fenómenos como el "feature splitting" (donde características amplias se refinan en otras más específicas) a medida que la postura se desplaza.
