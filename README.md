# Sistema de Entregas a Domicilio

Proyecto desarrollado en Java aplicando patrones de diseño para la gestión de pedidos y notificaciones en tiempo real.

## Patrones implementados

- **Singleton** → Configuración global del sistema.
- **Strategy** → Diferentes estrategias de envío.
- **Factory** → Creación de pedidos según el tipo.
- **Observer** → Notificación a clientes y logística.
- **Decorator** → Agregado de funcionalidades a las notificaciones.

## Estructura de carpetas

```bash
src/
│
├── singleton/
│   └── ConfiguracionSistema.java
│
├── strategy/
│   ├── EstrategiaEnvio.java
│   ├── EnvioEstandar.java
│   ├── EnvioExpress.java
│   └── EnvioProgramado.java
│
├── factory/
│   ├── Pedido.java
│   ├── PedidoNacional.java
│   ├── PedidoInternacional.java
│   └── PedidoFactory.java
│
├── observer/
│   ├── ObservadorPedido.java
│   ├── NotificadorCliente.java
│   └── NotificadorLogistica.java
│
├── decorator/
│   ├── Notificador.java
│   ├── NotificadorBase.java
│   ├── DecoradorNotificador.java
│   ├── DecoradorLogging.java
│   ├── DecoradorCifrado.java
│   └── DecoradorReintento.java
│
├── Main.java
│
└── README.md


## Ejemplo de salida

```bash
=== CONFIGURACION DEL SISTEMA ===
Impuesto : 0.19
Moneda   : COP
Descuento: 0.05

=== CREACION DE PEDIDOS ===
Creado: PedidoNacional{id='P001', descripcion='Electrodomestico', pesoKg=5.0, distanciaKm=100.0, estado='creado'}
Creado: PedidoInternacional{id='P002', descripcion='Repuesto automotriz', pesoKg=2.5, distanciaKm=3000.0, estado='creado', paisDestino='Por definir'}

=== SUSCRIPCION DE OBSERVADORES ===
Observadores suscritos al pedido P001

=== CALCULO DE COSTO DE ENVIO ===
Costo Estandar  : 11900.00 COP
Costo Express   : 23800.00 COP
Costo Programado: 9044.00 COP

=== CAMBIOS DE ESTADO DEL PEDIDO NACIONAL ===
[CLIENTE] Pedido P001: estado actualizado a 'en preparación'
[LOGISTICA] Pedido P001: requiere acción para estado 'en preparación'
[CLIENTE] Pedido P001: estado actualizado a 'enviado'
[LOGISTICA] Pedido P001: requiere acción para estado 'enviado'
[CLIENTE] Pedido P001: estado actualizado a 'entregado'
[LOGISTICA] Pedido P001: requiere acción para estado 'entregado'

=== NOTIFICADOR DECORADO (Logging + Cifrado) ===
[LOG] Enviando notificación: Pedido P001 entregado exitosamente
[NOTIFICACION] UGVkaWRvIFAwMDEgZW50cmVnYWRvIGV4aXRvc2FtZW50ZQ==
```

> El mensaje cifrado es la codificación en Base64 de:
> `Pedido P001 entregado exitosamente`
