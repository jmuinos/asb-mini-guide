# 🟫 Azure Service Bus Queues (Colas)

## 🧠 ¿Qué es una Queue?

Una cola es una estructura FIFO (First In, First Out) donde los mensajes se entregan a **un solo consumidor**.

## 📦 Ejemplo

```text
[ OrderService ] ---> [ Queue: order-processing ]
                           |
                           v
                   [ BillingService ]
```

## ✅ Ventajas

- Simplicidad
- Alta fiabilidad
- Ideal para tareas únicas (procesamiento de facturas, generación de reportes, envío de emails)

## ❌ Limitaciones

- Solo un consumidor por mensaje
- No permite que múltiples servicios reaccionen al mismo evento
- No admite filtros
- No es adecuada para sistemas de eventos donde varios subsistemas deben reaccionar a la vez
