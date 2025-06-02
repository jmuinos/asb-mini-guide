# 📦 Casos prácticos y patrones comunes

## 📌 1. Procesamiento de pedidos

- **Productor:** OrderService
- **Consumidores:** EmailService, InventoryService, CRMService
- **Tipo recomendado:** Topic + Subscriptions

```text
[ OrderService ] ---> [ Topic: order-created ]
                           |
        ┌──────────────────┼──────────────────┐
        ▼                  ▼                  ▼
[ EmailService ]   [ InventoryService ]   [ CRMService ]
```

---

## 📌 2. Facturación por lote

- **Productor:** API / WebApp
- **Consumidor:** BillingService
- **Tipo recomendado:** Queue

```text
[ WebApp ] ---> [ Queue: billing-jobs ] ---> [ BillingService ]
```

---

## 📌 3. Auditoría de eventos críticos

- **Productor:** Cualquier microservicio
- **Consumidor:** AuditService
- **Tipo recomendado:** Topic + Subscription con filtro

```text
[ AnyService ] ---> [ Topic: events ]
                          |
                          ▼
              [ AuditSubscription (filter: CriticalOnly) ]
                          |
                          ▼
                    [ AuditService ]
```

---

## 📌 4. Notificaciones masivas

- **Productor:** NotificationService
- **Consumidor:** Worker de envío de notificaciones
- **Tipo recomendado:** Queue con múltiples instancias consumidoras (para escalar)

```text
[ NotificationService ] ---> [ Queue: notifications ]
                                     |
                       ┌─────────────┴─────────────┐
                       ▼                           ▼
              [ WorkerInstance1 ]          [ WorkerInstance2 ]
```

---

## 🧠 Reglas generales de decisión

| Necesidad                                 | Tipo recomendado |
|------------------------------------------|------------------|
| Un consumidor por mensaje                | Queue            |
| Varios consumidores por mensaje          | Topic            |
| Procesamiento paralelo de tareas         | Queue            |
| Publicación de eventos (event-driven)    | Topic            |
| Filtro de mensajes por tipo o contenido  | Topic (con filtro) |

---

⬅️ [Anterior](./04-queues-vs-topics.md) | 🧭 [Índice](./README.md) | ➡️ [Siguiente](./06-migration-overview.md)

