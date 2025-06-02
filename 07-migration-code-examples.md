# Ejemplos prácticos de migración a Azure.Messaging.ServiceBus

## Enviar mensaje a un **Topic**

### Antes (Microsoft.Azure.ServiceBus)
```csharp
var client = new TopicClient(connectionString, topicName);
await client.SendAsync(new Message(Encoding.UTF8.GetBytes("Hello")));
```

### Después (Azure.Messaging.ServiceBus)
```csharp
var client = new ServiceBusClient(connectionString);
var sender = client.CreateSender(topicName);
await sender.SendMessageAsync(new ServiceBusMessage("Hello"));
```

---

## Escuchar mensajes de una **Subscription**

### Antes (SubscriptionClient)
```csharp
var client = new SubscriptionClient(connectionString, topicName, subscriptionName);
client.RegisterMessageHandler(async (msg, token) =>
{
    var body = Encoding.UTF8.GetString(msg.Body);
    await Process(body);
}, new MessageHandlerOptions(args => Task.CompletedTask));
```

### Después (ServiceBusProcessor)
```csharp
var processor = client.CreateProcessor(topicName, subscriptionName, new ServiceBusProcessorOptions
{
    AutoCompleteMessages = false
});

processor.ProcessMessageAsync += async args =>
{
    var body = args.Message.Body.ToString();
    await Process(body);
    await args.CompleteMessageAsync(args.Message);
};

processor.ProcessErrorAsync += args =>
{
    Console.WriteLine(args.Exception);
    return Task.CompletedTask;
};

await processor.StartProcessingAsync();
```

---

## Finalizar procesamiento

```csharp
await processor.StopProcessingAsync();
await processor.DisposeAsync();
await client.DisposeAsync();
```

---

⬅️ [Anterior](./06-migration-overview.md) | 🧭 [Índice](./README.md)

