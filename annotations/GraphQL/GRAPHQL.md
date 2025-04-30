# GraphQL - Fundamentos

## ¿Qué es GraphQL?

GraphQL es un lenguaje de consultas para APIs y un runtime para ejecutarlas. Fue creado por Facebook en 2012 y liberado en 2015 como código abierto.

Permite a los clientes **definir exactamente qué datos quieren** y los servidores responden con solo eso.

---

## 📌 Comparativa: GraphQL vs REST vs gRPC

| Característica         | REST                         | GraphQL                                | gRPC                                      |
|------------------------|------------------------------|-----------------------------------------|-------------------------------------------|
| Tipo de protocolo      | HTTP                         | HTTP                                    | HTTP/2                                     |
| Formato de datos       | JSON                         | JSON                                    | Protocol Buffers (binario)                |
| Número de endpoints    | Múltiples (por recurso)      | Uno solo                                | Uno por RPC (pero bien definidos)         |
| Definición de contrato | Implícito (OpenAPI a veces)  | Explícito (schema.graphqls)             | Muy estricto (proto files)                |
| Overfetching           | Frecuente                    | Evitado (cliente pide lo necesario)     | No aplica, se define lo justo             |
| Underfetching          | También común                | No, todo en una sola consulta           | No aplica                                 |
| Streaming              | Complicado                   | Solo vía Subscription                   | Nativo con HTTP/2 (excelente para streams)|
| Código generado        | Manual u OpenAPI             | No estándar                             | Sí, autogenerado a partir del `.proto`    |
| Ideal para             | CRUD clásico y web pública   | APIs complejas y ricas (apps, frontend) | Comunicación eficiente entre microservicios|
| Soporte de herramientas| Maduras y amplias            | En crecimiento                          | Requiere tooling específico               |

---

## 📦 Overfetching y Underfetching

### 📥 Overfetching (sobrecarga de datos)

Sucede cuando una API REST entrega **más información de la que necesitas**.

```json
{
  "id": 42,
  "name": "Adrián",
  "email": "adrian@email.com",
  "phone": "1234567890",
  "address": "{...}"
} 
```

### 📤 Underfetching (falta de datos)

Ocurre cuando la API te da menos datos de los que necesitas, y terminas haciendo varias llamadas:

```
GET /users/42
GET /users/42/orders
GET /orders/123/items
```

➡️ Múltiples viajes al servidor, más latencia, más código.

---

## 🧠 Conceptos Clave en GraphQL

- **Schema**: El contrato que define los tipos de datos y operaciones disponibles.
- **Query**: Para obtener datos.
- **Mutation**: Para modificar datos (crear, actualizar, eliminar).
- **Subscription**: Para recibir datos en tiempo real.
- **Resolver**: Función que ejecuta una operación (Query, Mutation, etc.).

---

## 🏆 Ventajas de GraphQL

- El cliente define la forma exacta de la respuesta.
- Permite obtener datos relacionados en una sola consulta.
- Solo un endpoint.
- Elimina underfetching y overfetching.
- Buen fit para aplicaciones móviles o SPA.

---

## 🧱 Desventajas o Retos

- Curva de aprendizaje inicial.
- Difícil cacheo en comparación con REST.
- Puede abrir la puerta a consultas costosas si no se limita adecuadamente.
- Necesita definir y mantener un schema.

---

# Paso 2: Setup de Proyecto - Spring Boot + WebFlux + GraphQL

## 🎯 Objetivo

Crear un proyecto base con Spring Boot 3, WebFlux y GraphQL, donde probaremos todas las queries usando **Postman** al endpoint `/graphql`.

---

## 📁 1. Crear Proyecto

Usa [Spring Initializr](https://start.spring.io):

- **Project**: Maven  
- **Language**: Java  
- **Spring Boot**: 3.x.x  
- **Dependencies**:
  - Spring Reactive Web
  - Spring for GraphQL
  - Lombok
  - Spring Boot DevTools (opcional)

---

## ⚙️ 2. Agregar dependencias al `pom.xml`

```xml
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-graphql</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-webflux</artifactId>
    </dependency>
    <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
        <optional>true</optional>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-devtools</artifactId>
        <scope>runtime</scope>
        <optional>true</optional>
    </dependency>
</dependencies>
 ```

---

# Paso 3: Tipos Complejos y Mapeo en Java con UUID

## 🎯 Objetivo

Definir un tipo complejo (`Product`) en el schema GraphQL, mapearlo a una clase Java y retornar una lista de objetos con UUID.

---

## 📄 1. Schema `schema.graphqls`

```graphql
type Product {
  id: ID
  name: String
  price: Float
}
type Query {
  products: [Product]
}
```

---

## 💾 2. Modelo en Java

```java
@Data
@NoArgsConstructor
@AllArgsConstructor
public class Product {
    private UUID id;
    private String name;
    private double price;
}
```

---

## 🎯 3. Resolver

```java
@Controller
public class ProductResolver {
    @QueryMapping
    public List<Product> products() {
        return List.of(
            new Product(UUID.randomUUID(), "Laptop", 1999.99),
            new Product(UUID.randomUUID(), "Monitor", 299.99),
            new Product(UUID.randomUUID(), "Teclado mecánico", 89.99)
        );
    }
}
```

---

## 🚀 Etapa 3: Query con R2DBC + PostgreSQL

### `ProductEntity`

```java
@Table("product")
@Data
@NoArgsConstructor
@AllArgsConstructor
public class ProductEntity {
  @Id
  private UUID id;
  private String name;
  private double price;
}
```

### `ProductRepository`

```java
public interface ProductRepository extends ReactiveCrudRepository<ProductEntity, UUID> {}
```

### `ProductService`

```java
@Service
@RequiredArgsConstructor
public class ProductService {
  private final ProductRepository productRepository;

  public Flux<ProductEntity> findAll() {
    return productRepository.findAll();
  }
}
```

### `ProductResolver`

```java
@Component
@RequiredArgsConstructor
public class ProductResolver {
  private final ProductService productService;

  @QueryMapping
  public Flux<ProductEntity> products() {
    return productService.findAll();
  }
}
```

---

### `schema.graphqls`

```graphql
type Product {
  id: ID!
  name: String!
  price: Float!
}
type Query {
  products: [Product!]!
}
```

---

### Seeder

```java
@Component
@RequiredArgsConstructor
public class ProductDataSeeder implements CommandLineRunner {
  private final ProductRepository productRepository;

  @Override
  public void run(String... args) {
    List<ProductEntity> products = List.of(
      new ProductEntity(UUID.randomUUID(), "Laptop", 1999.99),
      new ProductEntity(UUID.randomUUID(), "Monitor", 299.99),
      new ProductEntity(UUID.randomUUID(), "Teclado mecánico", 89.99)
    );
    productRepository.saveAll(products).subscribe();
  }
}
```

---

### Consulta en Postman

```
POST http://localhost:8080/graphql

{
  "query": "query { products { id name price } }"
}
```

---

## 🧠 Nota final

Esta etapa es solo **lectura** (query). Mutations, validaciones y seguridad vienen en la siguiente etapa.

---