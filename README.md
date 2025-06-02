# asb-mini-guide

Azure Service Bus introduction guide.

## Índice

1. [Monolito vs Azure Service Bus](./01-monolith-vs-servicebus.md)  
   Comparativa de una arquitectura monolítica frente al uso de Azure Service Bus.

2. [Azure Service Bus Queues](./02-queues.md)  
   Explicación sobre colas, sus características y cuándo utilizarlas.

3. [Azure Service Bus Topics](./03-topics.md)  
   Explicación sobre topics, subscripciones y su uso en arquitectura pub/sub.

4. [Queues vs Topics](./04-queues-vs-topics.md)  
   Comparativa directa entre colas y topics para ayudar en la toma de decisiones.

5. [Casos prácticos y patrones comunes](./05-use-cases.md)  
   Ejemplos comunes de uso en aplicaciones reales, incluyendo pedidos, facturación, notificaciones, etc.

6. [Guía de migración - Visión general](./06-migration-overview.md)  
   Resumen de los cambios entre el SDK antiguo y el nuevo paquete `Azure.Messaging.ServiceBus`.

7. [Guía de migración - Ejemplos básicos](./07-migration-code-examples.md)  
   Ejemplos simples de cómo migrar el código base de envío y recepción de mensajes.

8. [Guía de migración - Ejemplos avanzados](./08-advanced-migration-examples.md)  
   Casos más avanzados como DLQ, TTL, sesiones, Azure Identity e integración con ASP.NET.
