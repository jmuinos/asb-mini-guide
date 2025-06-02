# Migración a Azure.Messaging.ServiceBus (7.x)

## Contexto

Los paquetes antiguos:

- `WindowsAzure.ServiceBus` (4.x)
- `Microsoft.Azure.ServiceBus` (5.x)

📅 **Serán obsoletos el 30 de septiembre de 2026**.

Se recomienda migrar cuanto antes a:

- ✅ `Azure.Messaging.ServiceBus` (7.x)

## Cambios clave en el SDK

| Concepto                    | SDK antiguo                         | Nuevo SDK (7.x)                        |
|-----------------------------|--------------------------------------|----------------------------------------|
| Namespace                   | `Microsoft.Azure.ServiceBus`        | `Azure.Messaging.ServiceBus`          |
| Cliente de topic/queue      | `QueueClient`, `TopicClient`        | `ServiceBusSender`                    |
| Cliente de suscripción      | `SubscriptionClient`                | `ServiceBusProcessor` (para eventos)  |
| Clase de mensaje            | `Message`                           | `ServiceBusMessage`                   |
| Clase recibida              | `Message`                           | `ServiceBusReceivedMessage`           |
| Recepción manual            | `MessageReceiver`                   | `ServiceBusReceiver`                  |
| Manejo de errores           | `MessageHandlerOptions`             | `ProcessErrorAsync`                   |
| Autocompletado              | `AutoComplete = true`               | `AutoCompleteMessages = true`         |

## Recomendaciones

- Cambiar el paquete NuGet (`Azure.Messaging.ServiceBus`)
- Centralizar el uso de `ServiceBusClient`
- Usar `ServiceBusProcessor` para Topics y Subscripciones
- Implementar `ProcessMessageAsync` y `ProcessErrorAsync`
