# [Extensibilidad del depurador de Visual Studio](visual-studio-debugger-extensibility.md)
# [Elección de una estrategia de implementación del motor de depuración](choosing-a-debug-engine-implementation-strategy.md)
# [Creación de un motor de depuración personalizado](creating-a-custom-debug-engine.md)
## [Registro de un motor de depuración personalizado](registering-a-custom-debug-engine.md)
## [Habilitación de un programa que se desea depurar](enabling-a-program-to-be-debugged.md)
### [Obtención de un puerto](getting-a-port.md)
### [Registro del programa](registering-the-program.md)
### [Asociación al programa](attaching-to-the-program.md)
### [Adjunto basado en el inicio](launch-based-attachment.md)
### [Envío de los eventos necesarios](sending-the-required-events.md)
## [Control de ejecución y evaluación de estado](execution-control-and-state-evaluation.md)
### [Control de programas](program-control.md)
### [Métodos relacionados con el punto de interrupción](breakpoint-related-methods.md)
### [Evaluación de la pila de llamadas](call-stack-evaluation.md)
### [Evaluación de expresiones](expression-evaluation-visual-studio-debugging-sdk.md)
### [Eventos de control](control-events.md)
## [Envío de eventos](sending-events.md)
### [Orígenes de eventos](event-sources-visual-studio-sdk.md)
### [Tipos de evento compatibles](supported-event-types.md)
### [Descripciones de eventos](event-descriptions.md)
## [Terminación y separado](termination-and-detaching.md)
## [Llamada a eventos del depurador](calling-debugger-events.md)
### [Asociación y desasociación a un programa](attaching-and-detaching-to-a-program.md)
### [Inicio del depurador](launching-the-debugger.md)
### [Terminación de un programa](terminating-a-program.md)
### [Creación de un punto de interrupción](creating-a-breakpoint.md)
### [Cuando un punto de interrupción se enlaza o pasa a estar desenlazado](when-a-breakpoint-binds-or-becomes-unbound.md)
### [Errores de punto de interrupción](breakpoint-errors.md)
### [Llegada a un punto de interrupción](hitting-a-breakpoint.md)
### [Eliminación de un punto de interrupción](deleting-a-breakpoint.md)
### [Especificación de modo de interrupción](entering-break-mode.md)
### [Escalonado en modo de interrupción](stepping-in-break-mode.md)
### [Evaluación de expresiones en el modo de interrupción](expression-evaluation-in-break-mode.md)
### [Control de excepciones](exception-handling-visual-studio-sdk.md)
## [Depuración de un motor de depuración personalizado](how-to-debug-a-custom-debug-engine.md)
# [Introducción](getting-started-with-debugger-extensibility.md)
## [Guía básica para ampliar el depurador](roadmap-for-extending-the-debugger.md)
## [Componentes del depurador](debugger-components.md)
### [Depuración de paquete](debug-package.md)
### [Administrador de depuración del proceso](process-debug-manager.md)
### [Administrador de depuración de sesión](session-debug-manager.md)
### [Motor de depuración](debug-engine.md)
### [Modos de funcionamiento](operational-modes.md)
### [Evaluador de expresiones](expression-evaluator.md)
### [Proveedor de símbolos](symbol-provider.md)
### [Visualizador de tipo y visor personalizado](type-visualizer-and-custom-viewer.md)
## [Conceptos del depurador](debugger-concepts.md)
### [Sesión de depuración](debug-session.md)
### [Servidores](servers-visual-studio-sdk.md)
### [Proveedores de puertos](port-suppliers.md)
### [Puertos](ports.md)
### [Procesos](processes.md)
### [Nodos de programa](program-nodes.md)
### [Programas](programs.md)
### [Subprocesos](threads.md)
### [Marcos de pila](stack-frames.md)
### [Módulos](modules.md)
### [Puntos de interrupción](breakpoints-visual-studio-sdk.md)
## [Contextos de depurador](debugger-contexts.md)
### [Contexto del código](code-context.md)
### [Posición de documento](document-position.md)
### [Contexto de documento](document-context.md)
### [Contexto de evaluación de expresiones](expression-evaluation-context.md)
## [Tareas de depuración](debugging-tasks.md)
### [Problemas de seguridad](security-issues.md)
### [Inicio de un programa](launching-a-program.md)
#### [Notificación del puerto](notifying-the-port.md)
#### [Asociación después de un lanzamiento](attaching-after-a-launch.md)
### [Asociación directamente a un programa](attaching-directly-to-a-program.md)
### 
  [Envío de eventos de inicio después de un lanzamiento](sending-startup-events-after-a-launch.md)
### [Control de ejecución](control-of-execution.md)
### [Enlace de puntos de interrupción](binding-breakpoints.md)
### [Evaluación de expresiones](evaluating-expressions.md)
### [Visualización de datos](visualizing-and-viewing-data.md)
# [Escritura de un evaluador de expresiones CLR](writing-a-common-language-runtime-expression-evaluator.md)
## [Common Language Runtime y la evaluación de expresiones](common-language-runtime-and-expression-evaluation.md)
## [Arquitectura del evaluador de expresiones](expression-evaluator-architecture.md)
### [Contexto de evaluación](evaluation-context.md)
### [Interfaces de evaluador de expresión de claves](key-expression-evaluator-interfaces.md)
## [Registro de un evaluador de expresiones](registering-an-expression-evaluator.md)
## [Implementación de un evaluador de expresiones](implementing-an-expression-evaluator.md)
### [Estrategia de implementación del evaluador de expresiones](expression-evaluator-implementation-strategy.md)
## [Visualización de variables locales](displaying-locals.md)
### [Implementación de ejemplo de variables locales](sample-implementation-of-locals.md)
#### [Implementación de GetMethodProperty](implementing-getmethodproperty.md)
#### [Enumeración de variables locales](enumerating-locals.md)
#### [Obtención de propiedades locales](getting-local-properties.md)
#### [Obtención de valores locales](getting-local-values.md)
#### [Evaluación de variables locales](evaluating-locals.md)
## [Evaluación de una expresión de la ventana Inspección](evaluating-a-watch-window-expression.md)
### [Implementación de ejemplo de la evaluación de expresiones](sample-implementation-of-expression-evaluation.md)
### [Evaluación de una expresión de inspección](evaluating-a-watch-expression.md)
## [Cambio del valor de una variable local](changing-the-value-of-a-local.md)
### [Implementación de ejemplo del cambio de valores](sample-implementation-of-changing-values.md)
## [Implementación de visualizadores de tipo y visores personalizados](implementing-type-visualizers-and-custom-viewers.md)
# [Implementación de un proveedor de puerto](implementing-a-port-supplier.md)
## [Implementación y registro de un proveedor de puerto](implementing-and-registering-a-port-supplier.md)
## [Interfaces de proveedor de puerto requeridas](required-port-supplier-interfaces.md)
# [Datos internos de extensiones paralelas para .NET Framework](parallel-extension-internals-for-the-dotnet-framework.md)
## [Clase Task](task-class-internal-members.md)
### [m_action (Campo)](m-action-field.md)
### [m_contingentProperties (Campo)](m-contingentproperties-field.md)
### [m_parent (Campo)](m-parent-field.md)
### [m_stateFlags (Campo)](m-stateflags-field.md)
### [m_stateObject (Campo)](m-stateobject-field.md)
### [m_taskId (Campo)](m-taskid-field.md)
### [s_taskIdCounter (Campo)](s-taskidcounter-field.md)
### [TASK_STATE_CANCELED (Campo)](task-state-canceled-field.md)
### [TASK_STATE_EXECUTED (Campo)](task-state-executed-field.md)
### [TASK_STATE_FAULTED (Campo)](task-state-faulted-field.md)
### [TASK_STATE_RAN_TO_COMPLETION (Campo)](task-state-ran-to-completion-field.md)
### [TASK_STATE_WAITING_ON_CHILDREN (Campo)](task-state-waiting-on-children-field.md)
### [SetNotificationForWaitCompletion (Método)](setnotificationforwaitcompletion-method.md)
### [NotifyDebuggerOfWaitCompletion (Método)](notifydebuggerofwaitcompletion-method.md)
## [Clase TaskScheduler](taskscheduler-class-internal-members.md)
### [GetScheduledTasksForDebugger (Método)](getscheduledtasksfordebugger-method.md)
### [GetTaskSchedulersForDebugger (Método)](gettaskschedulersfordebugger-method.md)
## [Clase ContingentProperties](contingentproperties-class-internal-members.md)
### [m_children (Campo)](m-children-field.md)
## [Estructura AsyncTaskMethodBuilder](asynctaskmethodbuilder-structure-internal-members.md)
### [Propiedad ObjectIdForDebugger](asynctaskmethodbuilder-objectidfordebugger-property.md)
### [Campo m_builder](asynctaskmethodbuilder-m-builder-field.md)
## [Estructura AsyncTaskMethodBuilder<TResult>](asynctaskmethodbuilder-tresult-structure-internal-members.md)
### [Propiedad ObjectIdForDebugger](asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)
### [Campo m_task](asynctaskmethodbuilder-tresult-m-task-field.md)
## [Estructura AsyncVoidMethodBuilder](asyncvoidmethodbuilder-structure-internal-members.md)
### [Propiedad ObjectIdForDebugger](asyncvoidmethodbuilder-objectidfordebugger-property.md)
### [Campo m_objectIdForDebugger](asyncvoidmethodbuilder-m-objectidfordebugger-field.md)
# [Referencia](reference/reference-visual-studio-debugging-apis.md)
# [Ejemplos](visual-studio-debugging-samples.md)
