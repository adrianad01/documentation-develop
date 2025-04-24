
# 🌐 ¿Qué es gRPC?

**gRPC** (Google Remote Procedure Call) es un sistema de comunicación de alto rendimiento que permite que diferentes aplicaciones o servicios (incluso en distintos lenguajes) se comuniquen de forma rápida, segura y eficiente. Fue desarrollado por **Google** y es ampliamente utilizado en sistemas de microservicios.

---

## 🛠️ ¿Cómo funciona gRPC?

1. **Se define una interfaz** con métodos y tipos de datos en un archivo `.proto` usando Protocol Buffers.
2. **Se genera código** a partir de ese archivo para cliente y servidor en cualquier lenguaje compatible.
3. **El cliente llama** a métodos remotos del servidor como si fueran funciones locales.

---

## 📁 Ejemplo de archivo `.proto`

```proto
syntax = "proto3";

package saludos;

service SaludoService {
  rpc DiHola (SaludoRequest) returns (SaludoResponse);
}

message SaludoRequest {
  string nombre = 1;
}

message SaludoResponse {
  string mensaje = 1;
}
```

Este archivo define un servicio `SaludoService` con un método remoto `DiHola` que recibe un nombre y responde con un mensaje de saludo.

---

## 🧪 Ejemplo práctico en Java

### 1. Implementación del servidor

```java
public class SaludoServiceImpl extends SaludoServiceGrpc.SaludoServiceImplBase {
    @Override
    public void diHola(SaludoRequest request, StreamObserver<SaludoResponse> responseObserver) {
        String nombre = request.getNombre();
        String mensaje = "¡Hola, " + nombre + "!";
        SaludoResponse response = SaludoResponse.newBuilder().setMensaje(mensaje).build();
        responseObserver.onNext(response);
        responseObserver.onCompleted();
    }
}
```

### 2. Cliente que llama al servicio

```java
ManagedChannel channel = ManagedChannelBuilder.forAddress("localhost", 50051)
    .usePlaintext()
    .build();

SaludoServiceGrpc.SaludoServiceBlockingStub stub = SaludoServiceGrpc.newBlockingStub(channel);

SaludoRequest request = SaludoRequest.newBuilder().setNombre("Adrián").build();
SaludoResponse response = stub.diHola(request);

System.out.println(response.getMensaje());
```

---

## 🚀 ¿Por qué usar gRPC?

| Ventaja                 | Explicación                                                             |
|-------------------------|-------------------------------------------------------------------------|
| ⚡ Rápido               | Usa Protocol Buffers (binario, más ligero que JSON o XML).              |
| 💬 Multilenguaje        | Genera clientes y servidores en Java, Go, Python, C#, etc.              |
| 🔐 Contrato claro       | El `.proto` actúa como documentación y contrato de la API.              |
| 🔁 Soporta streaming     | Comunicación en tiempo real con `stream` y `bidirectional stream`.     |
| 🔒 Seguridad            | Soporta TLS y autenticación integrada.                                  |

---

## 🧩 Casos de uso comunes

- Comunicación eficiente entre microservicios
- APIs internas en sistemas distribuidos
- Servicios móviles de baja latencia

---

¿Listo para probar gRPC en tu proyecto? Solo necesitas:

1. Definir tu `.proto`
2. Generar el código con `protoc`
3. Implementar cliente y servidor
