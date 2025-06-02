# Queues vs Topics en Azure Service Bus

## Diferencia principal

| Característica         | Queue                          | Topic + Subscriptions              |
|------------------------|--------------------------------|------------------------------------|
| Tipo de entrega        | Uno a uno                      | Uno a muchos                       |
| Nº de consumidores     | Solo uno                       | Múltiples                          |
| Uso típico             | Tareas individuales            | Publicación de eventos             |
| Filtros por mensaje    | ❌ No                          | ✅ Sí                              |
| Escalabilidad          | ✅ Escalable                   | ✅ Escalable individualmente       |
| Complejidad            | 🔹 Baja                        | 🔸 Media                           |

---

## Ejemplo visual

### Queue

```text
[ OrderService ] ---> [ Queue: order-created ]
                           |
                           v
                  [ EmailService ]
```

### Topic + Subscriptions

```text
[ OrderService ] ---> [ Topic: order-created ]
                           |
        ┌──────────────────┼──────────────────┐
        ▼                  ▼                  ▼
[ EmailService ]   [ InventoryService ]   [ CRMService ]
```

---

## ✅ Reglas generales de decisión

| Necesidad                                 | Tipo recomendado |
|------------------------------------------|------------------|
| Un consumidor por mensaje                | Queue            |
| Varios consumidores por mensaje          | Topic            |
| Procesamiento paralelo de tareas         | Queue            |
| Publicación de eventos (event-driven)    | Topic            |
| Filtro de mensajes por tipo o contenido  | Topic (con filtro) |
