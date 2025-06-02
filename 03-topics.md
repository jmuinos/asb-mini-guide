# Azure Service Bus Topics

## ¿Qué es un Topic?

Un **Topic** (tema) es un mecanismo de publicación-suscripción (pub/sub) en el que **un productor envía un mensaje** y **múltiples consumidores pueden recibirlo** a través de **subscriptions independientes**.

Cada suscripción es como una “cola virtual” que recibe una copia del mensaje.

---

## Ejemplo visual

```text
[ OrderService ] ---> [ Topic: order-created ]
                           |
        ┌──────────────────┼──────────────────┐
        ▼                  ▼                  ▼
[ EmailService ]   [ InventoryService ]   [ CRMService ]
```

---

## ✅ Ventajas

- Desacopla completamente a los consumidores entre sí.
- Cada consumidor puede escalar, procesar y fallar independientemente.
- Permite aplicar **filtros por suscripción** (ej. solo mensajes de tipo `Critical`).
- Escalable, resiliente y orientado a eventos.
- Compatible con múltiples suscriptores paralelos.

---

## 🔧 Componentes clave

| Componente          | Descripción                                          |
|---------------------|------------------------------------------------------|
| `Topic`             | Canal central de publicación                         |
| `Subscription`      | Cola lógica asociada a un Topic                      |
| `Rule` / `Filter`   | Condición opcional para filtrar qué recibe la suscripción |
| `ServiceBusSender`  | Envia mensajes al Topic                              |
| `ServiceBusProcessor` | Escucha mensajes desde una Subscription            |

---

## Cuándo usar Topics

Usa Topics cuando:

- Varios servicios deben reaccionar a un mismo evento.
- Necesitas aplicar lógica de filtrado por consumidor.
- Quieres desacoplamiento total entre productor y consumidores.
- Estás diseñando una arquitectura basada en eventos (event-driven).
