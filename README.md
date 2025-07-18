# **Proyecto:** Mapeo y navegación de espacios conceptuales en modelos de lenguaje: De ideologías políticas a actitudes emergentes

## **Objetivo General:**
Investigar la factibilidad de identificar, aplicar y trazar "transformaciones" vectoriales en el espacio de activación de Grandes Modelos de Lenguaje (LLMs) para mapear cambios conceptuales entre posturas políticas, como conservadora y liberal, y revelar la arquitectura de estas actitudes dentro del modelo.

## **Justificación y Relevancia:**
Los Grandes Modelos de Lenguaje (LLMs) son capaces de inferir y representar propiedades de "agentes" (como autores o personas) a partir de texto. Esto incluye la capacidad de modelar intenciones comunicativas y creencias abstractas. Además, los LLMs pueden simular comportamientos humanos y adoptar distintas "personas", lo cual es crucial para diversas aplicaciones, desde la investigación en ciencias sociales hasta la generación de datos sintéticos.

Investigaciones recientes han demostrado que las representaciones internas de los LLMs no solo codifican el significado del texto, sino también información sobre el "estado del mundo" y las "intenciones comunicativas" de los agentes. Un hallazgo clave es que **las ideologías políticas, como el conservadurismo y el liberalismo, se representan en regiones más "distintas" dentro del espacio de activación del LLM**, a diferencia de, por ejemplo, las perspectivas éticas, que muestran un mayor solapamiento (poliosemia).

La interpretabilidad mecánica, especialmente a través del uso de **autoencoders dispersos (SAEs)**, ha avanzado significativamente, permitiendo descomponer las activaciones internas de los modelos en "características" (features) que son "altamente interpretables y monosemánticas" (es decir, corresponden a conceptos únicos y comprensibles). Estas características han demostrado ser **causalmente importantes** para el comportamiento del modelo, y su manipulación directa, a través de lo que se conoce como "vectores de dirección" (steering vectors), puede controlar propiedades y comportamientos del modelo, como el sentimiento o incluso la "alineación". La "realineación emergente" ha demostrado que pequeñas cantidades de datos benignos pueden restaurar eficientemente un modelo desalineado.

Este proyecto se basa en la premisa de que, si los LLMs representan estas ideologías como "direcciones" o "características" interpretables, podríamos identificar y manipular estas representaciones para comprender cómo se interconectan los conceptos dentro de estas posturas.

## **Fases del Proyecto:**

### **Fase 1: Identificación de la Transformación entre Posturas Políticas**

1.  **Objetivo:** Averiguar la transformación que define la posición de una postura política conservadora frente a una posición liberal.
    *   **Metodología:**
        *   **Selección de Modelos:** Se utilizarán LLMs de última generación, como Llama3-8B-Instruct o GPT-4o, conocidos por su capacidad para seguir instrucciones y codificar información detallada sobre personas y actitudes.
        *   **Recopilación de Datos:** Se curarán o generarán datasets de "persona-específicos" que contengan declaraciones y textos que reflejen explícitamente actitudes políticas conservadoras y liberales. Estos statements estarán etiquetados según la actitud que representen ("MATCHINGBEHAVIOR" o "NOTMATCHINGBEHAVIOR"). Se buscará diversidad cultural y geográfica en los datos, aunque las limitaciones de los datasets actuales (a menudo centrados en perspectivas WEIRD y política estadounidense) se reconocerán como un factor a considerar.
        *   **Análisis de Activaciones con SAEs:** Se entrenarán **autoencoders dispersos (SAEs)** sobre las activaciones internas de los LLMs. Los SAEs descompondrán estas activaciones en un conjunto de características subyacentes que son más interpretables que las neuronas individuales.
        *   **Localización de Ideologías:** Utilizando técnicas como **Deep Scan** y análisis de componentes principales (PCA), se identificarán las capas y subespacios de activación donde las ideologías políticas están más distintamente localizadas. La investigación de Cintas et al. ya indica que las ideologías políticas se encuentran en regiones "más distintas" dentro del espacio de representación.
        *   **Definición de la Transformación:** La "transformación" entre una postura conservadora y una liberal se definirá como un conjunto específico de características SAE o un "vector de dirección" en el espacio de activación que capture la diferencia conceptual entre ambas. Esto se logrará identificando las características que se activan diferencialmente o que cambian de magnitud al pasar de contextos conservadores a liberales.

### **Fase 2: Aplicación y Exploración de Conceptos Relacionados**

2.  **Objetivo:** Dada la transformación identificada, aplicarla a conceptos básicos relacionados con la postura política original, y revelar cuáles son los conceptos a los que se llega.
    *   **Metodología:**
        *   **Intervenciones Causales ("Steering"):** Una vez que el "vector de transformación" (o el conjunto de SAE latentes) que representa la transición de "conservador" a "liberal" (o viceversa) ha sido identificado, se utilizarán técnicas de "steering" o manipulación de activaciones. Esto implica agregar una "múltiple" del vector de decodificación de los SAE latentes relevantes a las activaciones de los tokens en las capas identificadas.
        *   **Aplicación a Conceptos Base:** Se seleccionarán conceptos clave asociados a la política (ej., "economía", "educación", "salud", "seguridad") y se generarán representaciones de estos conceptos bajo la influencia de la postura política original (ej., "economía conservadora"). Luego, se aplicará la transformación identificada.
        *   **Revelación de Conceptos Resultantes:** Se utilizarán métodos de **autointerpretación**, donde un LLM se encarga de generar explicaciones legibles de las características que se activan en las nuevas representaciones. Esto permitirá entender cómo los conceptos como "economía" cambian de "economía conservadora" a "economía liberal" en el modelo, y cuáles son las nuevas ideas o asociaciones que emergen. Se buscarán descripciones del modelo sobre sus propias "creencias" y "deseos" subyacentes.
        *   **Análisis de Comportamiento:** Se evaluará si el modelo, al ser "steered" hacia la nueva postura, cambia su comportamiento al responder preguntas sobre esos conceptos, por ejemplo, si un modelo previamente conservador ahora genera respuestas con un sesgo liberal sobre "salud".

### **Fase 3: Mapeo Conceptual y Rutas de Transformación**

3.  **Objetivo:** Determinar si estas transiciones suponen el camino de menor resistencia, y componiendo las transformaciones de diferentes componentes, construir un mapa conceptual dinámico de las actitudes.
    *   **Metodología:**
        *   **Eficiencia de la Transformación:** Se cuantificará la "resistencia" o "eficiencia" de la transformación mediante la minimización de la magnitud de la intervención necesaria para lograr un cambio conceptual significativo. La literatura ya muestra la eficiencia de las intervenciones de "steering" y de la "realineación" con datos mínimos, sugiriendo que existen caminos de "menor resistencia" inherentes a la forma en que los modelos organizan la información.
        *   **Mapeo de la Arquitectura Conceptual:**
            *   Se utilizará un enfoque de **"model-diffing"**, comparando las activaciones del modelo en diferentes puntos a lo largo de la "transformación" (ej., 0% liberal, 25% liberal, 50% liberal, etc.). Esto permitirá identificar qué características SAE se activan o modifican en cada etapa, construyendo una "trayectoria conceptual".
            *   La descomposición de activaciones en un gran número de características interpretables por los SAEs permitirá una visión granular de cómo los diferentes "componentes" conceptuales (ej., la perspectiva sobre impuestos, la regulación ambiental, etc.) se desplazan.
            *   Se generarán visualizaciones (potencialmente utilizando métodos como UMAP para la reducción de dimensionalidad) que representen este **"mapa conceptual"**, mostrando no solo la arquitectura de la actitud original y la de destino, sino también los puntos intermedios y las relaciones entre los conceptos que evolucionan durante la transformación. Esto podría revelar fenómenos como el "feature splitting" (donde características amplias se refinan en otras más específicas) a medida que la postura se desplaza.

### **Fase 4: Transferencia y Validación de Transformaciones Vectoriales para Intervenciones Persuasivas Humanas**

4. **Objetivo:** Desarrollar y validar técnicas de persuasión humana basadas en las transformaciones vectoriales identificadas en las fases anteriores, estableciendo rutas empíricamente fundamentadas para el cambio de actitudes que repliquen los caminos de menor resistencia descubiertos en el espacio conceptual de los LLMs.
    *   **Metodología:**
        *   **Traducción de Vectores de Transformación:** Se mapearán las transformaciones vectoriales identificadas en las Fases 1-3 hacia "vectores de persuasión" aplicables a cognición humana. Utilizando datos de neuroimagen de estudios previos de persuasión, se calibrarán las transformaciones del LLM con patrones de activación cerebral humana en regiones críticas (corteza prefrontal medial, polos temporales, unión temporo-parietal). La evidencia de Google Research demuestra que las representaciones internas de LLMs se alinean con patrones neurales humanos en procesamiento del lenguaje, proporcionando la base científica para esta transferencia
        *   **Diseño de Intervenciones Persuasivas Algorítmicas:** Basándose en los perfiles psicológicos individuales y las rutas de transformación conceptual identificadas, se generarán mensajes persuasivos personalizados que implementen las transformaciones vectoriales específicas. La secuenciación seguirá las "rutas de menor resistencia" mapeadas en la Fase 3, respetando la arquitectura conceptual natural del cambio de actitudes. Los estudios multicéntricos confirman que mensajes generados algorítmicamente exhiben mayor probabilidad de persuasión que intervenciones humanas cuando se utiliza personalización basada en transformaciones vectoriales.
        *   **Validación Experimental Controlada:** Se implementará un protocolo experimental con grupos experimentales y control. Las medidas incluirán evaluación basal de actitudes políticas, neuroimagen funcional en submuestras, exposición a intervenciones diseñadas según transformaciones vectoriales, y seguimiento longitudinal. La validación neural utilizará análisis de conectividad para evaluar cambios en redes cerebrales de persuasión, y algoritmos de machine learning para decodificar estados de actitud desde patrones cerebrales.
        *   **Análisis de Correspondencia Vector-Neural:** Se verificará la hipótesis central de que las transformaciones vectoriales identificadas en LLMs predicen cambios neurales medibles en redes de persuasión humana. Utilizando análisis de similaridad representacional y decodificación neural, se establecerá la correspondencia cuantitativa entre direcciones vectoriales del modelo y modificaciones en patrones de activación cerebral, validando así la transferibilidad computacional entre sistemas artificiales y biológicos de procesamiento conceptual.
        *   **Optimización mediante Retroalimentación Adaptativa:** Se desarrollarán sistemas de retroalimentación que ajusten las intervenciones basándose en respuestas fisiológicas y comportamentales en tiempo real. Los algoritmos de aprendizaje por refuerzo optimizarán la secuencia e intensidad de transformaciones vectoriales según la respuesta individual, estableciendo protocolos de personalización que superen aproximaciones genéricas tradicionales en eficacia persuasiva.
     

### Bibliografía

* Betley, J., Bao, X., Soto, M., Sztyber-Betley, A., Chua, J., & Evans, O. (2025). Tell me about yourself: LLMs are aware of their learned behaviors. *arXiv preprint arXiv:2501.11120*. http://arxiv.org/abs/2501.11120

* Betley, J., Tan, D., Warncke, N., Sztyber-Betley, A., Bao, X., Soto, M., Labenz, N., & Evans, O. (2025). Emergent Misalignment: Narrow finetuning can produce broadly misaligned LLMs. *arXiv preprint arXiv:2502.17424*. http://arxiv.org/abs/2502.17424

* Bhandari, P., Fay, N., Wise, M., Datta, A., Meek, S., Naseem, U., & Nasim, M. (2025). Can LLM Agents Maintain a Persona in Discourse? *arXiv preprint arXiv:2502.11843*. http://arxiv.org/abs/2502.11843

* Bricken, T., Templeton, A., Batson, J., Chen, B., Jermyn, A., Conerly, T., ... & Olah, C. (2023). Towards Monosemanticity: Decomposing Language Models With Dictionary Learning. *Transformer Circuits Thread*. https://transformer-circuits.pub/2023/monosemantic-features

* Chua, J., Betley, J., Taylor, M., & Evans, O. (2025). Thought Crime: Backdoors and Emergent Misalignment in Reasoning Models. *arXiv preprint arXiv:2506.13206*. http://arxiv.org/abs/2506.13206

* Cintas, C., Rateike, M., Miehling, E., Daly, E., & Speakman, S. (2025). Localizing Persona Representations in LLMs. *arXiv preprint arXiv:2505.24539*. http://arxiv.org/abs/2505.24539

* Cunningham, H., Ewart, A., Riggs, L., Huben, R., & Sharkey, L. (2023). Sparse Autoencoders Find Highly Interpretable Features in Language Models. *arXiv preprint arXiv:2309.08600*. http://arxiv.org/abs/2309.08600

* Gao, L., la Tour, T. D., Tillman, H., Goh, G., Troll, R., Radford, A., Sutskever, I., Leike, J., & Wu, J. (2024). Scaling and evaluating sparse autoencoders. *arXiv preprint arXiv:2406.04093*. http://arxiv.org/abs/2406.04093

* Li, A., Chen, H., Namkoong, H., & Peng, T. (2025). LLM Generated Persona is a Promise with a Catch. *arXiv preprint arXiv:2503.16527*. http://arxiv.org/abs/2503.16527

* Treutlein, J., Choi, D., Betley, J., Marks, S., Anil, C., Grosse, R., & Evans, O. (2024). Connecting the Dots: LLMs can Infer and Verbalize Latent Structure from Disparate Training Data. *arXiv preprint arXiv:2406.14546*. http://arxiv.org/abs/2406.14546

* Wang, M., la Tour, T. D., Watkins, O., Makelov, A., Chi, R. A., Miserendino, S., Heidecke, J., Patwardhan, T., & Mossing, D. (2025). Persona Features Control Emergent Misalignment. *arXiv preprint arXiv:2506.19823*. http://arxiv.org/abs/2506.19823
