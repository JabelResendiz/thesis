Revisa lo siguiente: 
Definición del problema científico 

Problema actual (pág. 19):
"La ausencia de una plataforma automatizada para el autorreporte de ESAVI en el IFV, que permita la gestión estructurada y oportuna de los datos clínicos de seguridad."

Problemas con esta definición:

1. No es falsable ni medible desde la computación. ¿”Ausencia” es el problema o la consecuencia? El problema real debería expresarse en términos de pérdida de información, retraso en la detección de señales o infranotificación cuantificable.
2. No establece umbrales. ¿Qué significa “oportuna”? ¿Minutos, horas, días? Compárelo con el estándar actual (15 días).
3. Confunde causa (falta de plataforma) con efecto (mala gestión). Un problema científico debe describir el fenómeno indeseado, no la solución de ingeniería.

Sugerencia de reformulación (ejemplo):

“El proceso actual de notificación de ESAVI en el IFV introduce una demora media de X días entre la ocurrencia del evento y su análisis, y se estima que al menos el Y% de los eventos no se registra por barreras en la captura de datos. No existe un mecanismo automatizado que garantice la integridad referencial de las 75 variables clínicas ni que permita al fabricante consultar reportes en tiempo real.”


Pregunta científica – Redundante y poco técnica

Pregunta actual (pág. 19):

“¿Cómo diseñar e implementar una solución informática para el autorreporte y gestión de ESAVI que permita el manejo estructurado de los datos clínicos de seguridad?”

Crítica:

· Es una repetición del objetivo general. Una pregunta científica debe abrir interrogantes de investigación, no reformular el objetivo.
· No hay hipótesis ni variable independiente.

Sugerencia: Reformule como:

“¿Qué arquitectura de software (cliente-servidor, PWA con sincronización offline, etc.) y qué modelo de datos permiten reducir la latencia de notificación de ESAVI de 15 días a menos de 24 horas, manteniendo la integridad de las 75 variables del estándar FarmaVigiC, en condiciones de conectividad intermitente?”

Objetivos específicos – Evaluación técnica

Objetivo actual Crítica Sugerencia
1. Investigar el estado del arte de sistemas de farmacovigilancia Aceptable. Pero no menciona qué aspectos del estado del arte (rendimiento, interoperabilidad, estándares HL7/FHIR, privacidad). Especifique: “comparar al menos 3 sistemas (VAERS, v-safe, VigiBase) en términos de modelo de datos y flujo de notificación”.
2. Analizar los procesos actuales en el IFV Vago. “Analizar” no es un verbo de diseño de software. Use: “Modelar el proceso actual de gestión de ESAVI mediante diagramas BPMN e identificar al menos 3 cuellos de botella cuantificables”.
3. Diseñar un modelo de datos Correcto. Pero no dice qué estándares seguir (¿relacional? ¿documentos? ¿cumple con los 75 campos de FarmaVigiC?). Agregue: “que normalice las 75 variables documentadas en el Anexo B.1 y sea compatible con la exportación a VigiBase”.
4. Definir la arquitectura siguiendo SOLID Aceptable, pero SOLID es solo para diseño de clases OO, no para arquitectura de sistemas. Distinga: “Arquitectura de capas (presentación, lógica, persistencia) con principios SOLID en la capa de dominio”.
5. Implementar prototipo funcional Vago. “Prototipo” sugiere algo descartable, pero la tesis habla de plataforma productiva. Decida: ¿es un prototivo validado o un sistema productivo? Use “mínimo producto viable (MVP)” si es el caso.
6. Validar mediante pruebas No especifica tipos de prueba (unidad, integración, aceptación, carga). Agregue: “pruebas de integridad referencial (100% de los campos), pruebas de sincronización offline y pruebas de usabilidad con al menos 5 usuarios finales”.

Actualidad, novedad e importancia – Inflación retórica

· Problema: Usa términos como “ecosistema digital centralizado”, “arquitectura de autorreporte reactiva”, “resiliencia ante conectividad limitada” sin definir qué significan técnicamente.



Ejemplo: “Resiliencia” en computación tiene un significado preciso (capacidad de recuperación ante fallos). No basta decir que “permite crear reportes offline”. Explique cómo (¿IndexedDB? ¿localStorage? ¿sincronización con cola de mensajes?).
· Novedad científica: Declara elementos innovadores, pero no compara con soluciones existentes en Cuba (¿FarmaVigiC ya permite autorreporte? ¿Por qué la diferencia es novedosa?). El tribunal necesita una tabla comparativa con el estado actual.
· Importancia: La frase “habilitador esencial para técnicas de ciencia de datos y aprendizaje automático” es especulativa si no hay un plan concreto en los capítulos posteriores. Modere o incluya métrica

Didas

· No se mencionan las restricciones legales y éticas: Notificación de ESAVI involucra datos sensibles de salud. ¿Qué ley cubana (¿de protección de datos?) aplica? ¿Se requiere consentimiento informado digital?
· No hay estimación del volumen de datos: ¿Cuántos reportes anuales espera procesar? Sin eso, no puede justificar si Excel es “rudimentario”.
· No se define el alcance del sistema: ¿Solo para vacunas del IFV? ¿Solo para Cuba? ¿Integración con FarmaVigiC?

[4/5, 8:26 p. m.] Pr. Joanna (Tutora): A la profesora Carmen no le gusta el término problematica
[4/5, 8:32 p. m.] Pr. Joanna (Tutora): Une el 1.3 con el 1.4