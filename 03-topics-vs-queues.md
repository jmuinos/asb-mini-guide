# 📬 Azure Service Bus Topics vs Queues

## 🔄 Diferencia clave

| Característica         | Queue                          | Topic + Subscriptions              |
|------------------------|--------------------------------|------------------------------------|
| Tipo de entrega        | Uno a uno                      | Uno a muchos                       |
| Nº de consumidores     | Solo uno                       | Múltiples                          |
| Uso típico             | Tareas individuales            | Publicación de eventos             |
| Filtros por mensaje    | ❌ No                          | ✅ Sí                              |
| Escalabilidad          | ✅                              | ✅ Por suscripción                 |
| Complejidad            | 🔹 Baja                        | 🔸 Media                           |

---

## 🧪 Ejemplo visual

### Queue

```text
[ OrderService ] ---> [ Queue: order-created ]
                           |
                           v
                  [ EmailService ]
```

Solo un servicio puede procesar el mensaje.

---

### Topic + Subscriptions

```text
[ OrderService ] ---> [ Topic: order-created ]
                           |
        ┌──────────────────┼──────────────────┐
        ▼                  ▼                  ▼
[ EmailService ]   [ InventoryService ]   [ CRMService ]
```

Cada servicio recibe su **propia copia** del mensaje y lo procesa de forma independiente.

---

## ✅ Cuándo usar cada uno

- Usa **Queue** cuando **solo un servicio** necesita procesar cada mensaje.
- Usa **Topic** cuando **varios servicios** necesitan reaccionar al mismo evento (ej. arquitectura orientada a eventos).
