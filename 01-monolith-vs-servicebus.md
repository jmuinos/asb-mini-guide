# Monolito vs Azure Service Bus

## Escenario clásico

Una aplicación de gestión de pedidos realiza múltiples acciones:

- Guardar el pedido
- Enviar un email
- Actualizar stock
- Registrar cliente en CRM

```csharp
public void PlaceOrder(Order order)
{
    SaveOrder(order);
    SendConfirmationEmail(order);
    UpdateStock(order);
    RegisterInCRM(order);
}
```

## ❌ Problemas del monolito

- Alto acoplamiento entre responsabilidades.
- Fallos en una parte interrumpen todo el proceso.
- Escalado difícil y poco granular.
- Baja mantenibilidad y dificultad para aplicar pruebas unitarias.

---

## ✅ Enfoque con Azure Service Bus

Desacoplas las responsabilidades. El pedido se guarda y se publica un evento en el bus. Cada servicio se suscribe y responde a ese evento.

```text
[ OrderService ] ---> [ Azure Service Bus ]
                             |
            ┌────────────────┼───────────────┐
            ▼                ▼               ▼
      EmailService     InventoryService    CRMService
```
---

🧭 [Índice](./README.md) | ➡️ [Siguiente](./02-queues.md)
