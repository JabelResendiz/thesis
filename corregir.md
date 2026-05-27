Para la seccion 2.1 (Estado del arte) se identifican los siguientes problemas y sugerencias de mejora:
1. Algunas oraciones son excesivamente largas y complejas (promedio > 35-40 palabras), lo que dificulta la lectura fluida. Ejemplo en la sección 2.1.5 un solo párrafo de más de 70 palabras con múltiples subordinadas. 
2.También se repiten ideas casi idénticas entre la descripción individual de cada sistema y el análisis comparativo (p. ej., limitaciones de la vigilancia pasiva se repiten en 2.1.1, 2.1.2 y 2.1.4).  
Sugerencia: Aplicar la regla “una idea principal por oración”. Dividir párrafos largos y eliminar redundancias mediante frases de transición más concisas (“Como se observó anteriormente…”).
3. Problema:  
- Uso repetitivo de frases (“En este sentido…”, “De manera global…”, “Asimismo…”).  
- Algunas construcciones pasivas excesivas (“se evidencia que…”, “se considera que…”) que diluyen la voz del autor.
Sugerencia: Variar las expresiones de transición y preferir voz activa cuando el sujeto es el estudiante (“El análisis revela…” en lugar de “Se revela…”). Revisar todas las listas con viñetas para que sigan exactamente el mismo formato.
4. Problema principal: 
- Las descripciones individuales de VAERS, NotificaRAM y V-safe (páginas 2-8) son muy extensas y descriptivas; el lector debe leer más de 6 páginas para luego encontrar el análisis comparativo.
5.  Sugerencia en la seccion 2.1.4 incluir Tabla 2.1: Comparación de sistemas de autorreporte con columnas: Sistema, Modelo de vigilancia, Nivel de digitalización, Actores, Fortalezas principales, Limitaciones principales, Grado de adecuación al sistema propuesto.
Después llegas a una conclusión parcial resumida  porque en la tabla se sintetiza




# Corregir en el CAP3


## Generales 

- [ ] Oraciones excesvimante largas de + 40 palabras
- [ ] Uso de "se" impersonal excesvio, alternar con voz activa cuando el sujeto es claro

## Metodología

- [X] Definición de Scrum incompleta (no se menciona artefactos, product blacklog, srping backlog, increment)
- [X] Anonimización de datos(sprint 2): sin especificar técnicas ni algoritmos, solo se menciona que se hizo

## Requerimientos

- [X] Incosistencias en numeración de requisitos
- [X] Ambigüedad  en usuarios familiazarizados RNF-01 establece menor a 2 mintuos por parte de un uusario familizarizado (qué es un familiarizado)
- [X] RNF-04 menor a 3 segundos sin especfiicar percentil ni condiciones de red


## Diagramas de casos de uso

- [X]Ambiguedad en catalogs predefinidos, se menciona pero nunca se dice cuales son ni quien los administra


## Arquitectura 

- [X] Definción técnica incompleta de arquitectura
- [X] Uso de anglicismo innecesario (Time-to-market, poner la traducción)
- [X] Cambiar el título de "Filosofías candidatas" a "Alternativas Arquitectonicas evaluadas" o "candidatos arquitectornicos"
- [X] Sustituir "favorece la aplicación de los principios SOLID" por "facilita la aplicación" o "propicia el cumplimiento"
- [ ] Falta de transiciones entre secciones : Salto abrupto de 1.4.3 y 1.4.4

- [X] Término de "anillo" para Clean sin precisión (donde los anillo internos es el más estable y el exterior es más volátil)

- [ ] Patrón de CQRS sin definción previa
- [X] Analizar la transición entre monolito y microservicios
- [X] Incosistcnai en descripcion de capas: La capa de infraestruca dpende de domainy de aplicacion , pero en clean solo de depende de apliacion
- [X] JWT mencionado sin profundidad
- [X] EntityFrameworkCOre como UnitOfWork : se afrima que DbCOntext.SaveChangeAsync ya actpua como unidad de trabajo sin advertir sus limitaciones.
- [X] CORS y Swagger mencionados sin contexto: mencionadas como coniguración tecnica sin mencionar por qué son necesarias.




## Diseño de base de datos

- [ ]Falta especificar algoritmo de hashing unidireccional sin nombrar cuál es.
- [ ] Perfeccionar sección de normalización con los nuevos datos de las tablas







```csharp

