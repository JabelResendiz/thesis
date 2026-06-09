# Corregir en el CAP3


## Generales 

- [ ] Oraciones excesvimante largas de + 40 palabras
- [ ] Uso de "se" impersonal excesvio, alternar con voz activa cuando el sujeto es claro

## Metodología

- [X] Definición de Scrum incompleta (no se menciona artefactos, product blacklog, srping backlog, increment)
- [X] Anonimización de datos(sprint 2): sin especificar técnicas ni algoritmos, solo se menciona que se hizo


- [X] Imprecisión en algunos términos:
  · “Alta. Soporta cambios mediante refactorización continua” (Tabla 1.1) – Si bien es correcto, en XP la refactorización es una práctica continua, pero no es la única habilitante de cambios; sería mejor “cambios mediante ciclos cortos y refactorización constante”.

## Requerimientos

- [X] Incosistencias en numeración de requisitos
- [X] Ambigüedad  en usuarios familiazarizados RNF-01 establece menor a 2 mintuos por parte de un uusario familizarizado (qué es un familiarizado)
- [X] RNF-04 menor a 3 segundos sin especfiicar percentil ni condiciones de red
- [] RNF-01 sobre usabilidad (pág. 7): “completarse en un tiempo promedio menor a 3 minutos” – no se especifica cómo se mide (¿desde la carga del formulario hasta el envío? ¿incluyendo la validación?). Tampoco se define el tamaño de la muestra ni el método de medición
- [] Ejemplificar un poco más y detallar los requerimientos

## Diagramas de casos de uso

- [X]Ambiguedad en catalogs predefinidos, se menciona pero nunca se dice cuales son ni quien los administra
- [] Ejemplificar un poco más y detallar los casos de uso


## Arquitectura 

- [X] Definción técnica incompleta de arquitectura
- [X] Uso de anglicismo innecesario (Time-to-market, poner la traducción)
- [X] Cambiar el título de "Filosofías candidatas" a "Alternativas Arquitectonicas evaluadas" o "candidatos arquitectornicos"
- [X] Sustituir "favorece la aplicación de los principios SOLID" por "facilita la aplicación" o "propicia el cumplimiento"
- [X] Término de "anillo" para Clean sin precisión (donde los anillo internos es el más estable y el exterior es más volátil)

- [X] Patrón de CQRS sin definción previa
- [X] Analizar la transición entre monolito y microservicios
- [X] Incosistcnai en descripcion de capas: La capa de infraestruca dpende de domainy de aplicacion , pero en clean solo de depende de apliacion
- [X] JWT mencionado sin profundidad
- [X] EntityFrameworkCOre como UnitOfWork : se afrima que DbCOntext.SaveChangeAsync ya actpua como unidad de trabajo sin advertir sus limitaciones.
- [X] CORS y Swagger mencionados sin contexto: mencionadas como coniguración tecnica sin mencionar por qué son necesarias.






- [X] Fácil de gestionar inicialmente” para monolito (Tabla 1.2) – gestionar es vago; debería decir “desplegar y depurar”
- [] Inconsistencia en nombres de patrones – “Mapper” (pág. 17) vs. “Data Mapper” (no se especifica si es el patrón de Fowler o un simple DTO mapper).
- [X] · Justificación de la arquitectura monolítica (pág. 12-13): El argumento “en un monolito las llamadas a funciones son instantáneas y predecibles” es correcto en teoría, pero en la práctica una aplicación web monolítica también sufre latencia de red entre cliente y servidor, y el overhead de serialización en la capa de presentación. La frase puede inducir a error si se interpreta como que no hay latencia alguna.
- [X] Transición abrupta entre 1.4.3 y 1.5 (pag 17). Tras explicar las capas de Clean Architecture, el texto pasa directamente al diseño de base de datos sin un párrafo de enlace que explique cómo el modelo relacional se integra con la capa de Infraestructura y el patrón Repository.
- [X] Inconsistencia en nombres de patrones – “Mapper” (pág. 17) vs. “Data Mapper” (no se especifica si es el patrón de Fowler o un simple DTO mapper).
Sugerencias:Especificar que el Mapper utilizado es un DTO Mapper (como AutoMapper) o un Data Mapper (como el de Doctrine), según corresponda. En el contexto de Clean Architecture suele ser un mapper entre entidades de dominio y modelos de persistencia.
- [X] · Falta de profundidad en patrones arquitectónicos (pág. 17): Se mencionan Repository, Unit of Work, Inyección de dependencias y Mapper, pero no se explica cómo se implementan concretamente en el contexto de Clean Architecture (por ejemplo, si el Repository retorna entidades de dominio o modelos de persistencia). Tampoco se aclara si se utiliza un ORM (Entity Framework Core, NHibernate) o acceso directo.
Sugerencia lo puedes explicar aquí o dejarlo para el.siguiente capítulo de detalles de implementación. Si te vas por esa opción entonces mencionas que en el capítulo 4 se explicará en más detalles
- [] : Critica
No se menciona el manejo de sesiones o transacciones distribuidas – Aunque el sistema es monolítico, el uso de Unit of Work sugiere transacciones con la base de datos. No se especifica el nivel de aislamiento ni cómo se manejan los conflictos de concurrencia (ej. dos médicos intentando asignar el mismo reporte).

## Diseño de base de datos

- [X] Quitar GUID o int de todo tipo solo dejar que son de tipo llave primaria
- [X] Quitar toda relación con .NET.
- [] La sección 1.5.7 “Normalización” es muy técnica y detallada, pero la definición de dependencias funcionales (pág. 33) se presenta en una enumeración densa que podría resumirse en una tabla.  Convertir la lista de dependencias funcionales en una tabla de dos columnas (Atributo determinante → Atributos dependientes) para mejorar la legibilidad.



