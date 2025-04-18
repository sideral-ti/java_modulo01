# Contenido Hora 1: Introducción al módulo y repaso de conceptos básicos de POO

## 1. Presentación del curso y metodología (15 minutos)

### Bienvenida (3 min)
¡Bienvenidos al curso de Java 21! En este módulo exploraremos las características más recientes de Java y cómo pueden mejorar nuestra productividad como desarrolladores. Antes de comenzar, me gustaría presentarme y conocer un poco sobre ustedes y sus expectativas.

### Objetivos del curso (5 min)
Este curso está diseñado para:

- **Dominar las nuevas características de Java 21**: Aprenderemos a utilizar eficientemente las últimas adiciones al lenguaje, como Virtual Threads, Pattern Matching, Records, Sealed Classes y las mejoras en colecciones.

- **Reforzar las mejores prácticas de POO**: Revisaremos los fundamentos de la programación orientada a objetos con un enfoque en su aplicación moderna.

- **Desarrollar habilidades prácticas**: Cada concepto teórico será acompañado de ejercicios y proyectos prácticos que simulan situaciones del mundo real.

- **Prepararse para la certificación**: El contenido está alineado con los requisitos para la certificación Oracle Certified Professional: Java SE 21 Developer.

### Evaluación y criterios de éxito (4 min)

La evaluación del curso se basará en:

1. **Proyectos prácticos (50%)**: Desarrollarán tres proyectos incrementales aplicando los conceptos aprendidos.
    - Proyecto 1: API REST con características modernas de Java 21
    - Proyecto 2: Aplicación concurrente utilizando Virtual Threads
    - Proyecto 3: Sistema de procesamiento de datos utilizando el nuevo API de Colecciones

2. **Quizzes diarios (20%)**: Breves evaluaciones al final de cada día para reforzar el aprendizaje.

3. **Proyecto final (30%)**: Implementación de una aplicación completa que incorpore todas las características aprendidas.

Los criterios de éxito incluyen:
- Implementación correcta de las características de Java 21
- Adherencia a las mejores prácticas de POO
- Eficiencia y rendimiento del código
- Legibilidad y mantenibilidad

### Recursos disponibles (3 min)

Para este curso contarán con:

- **Repositorio GitHub**: Todos los ejemplos, ejercicios y soluciones estarán disponibles en nuestro repositorio: [github.com/java21-masterclass](https://github.com/java21-masterclass)

- **Entorno de desarrollo**: Utilizaremos IntelliJ IDEA (Community Edition es suficiente) con JDK 21 instalado.

- **Documentación**:
    - JavaDocs oficiales de Java 21
    - Guías y tutoriales seleccionados
    - Notas del curso en formato Markdown

- **Foro de discusión**: Plataforma para resolver dudas fuera del horario de clase.

## 2. Revisión histórica de Java (20 minutos)

### Evolución desde Java 8 hasta Java 21 (8 min)

La historia reciente de Java ha estado marcada por cambios significativos:

**Java 8 (2014)** - La revolución funcional:
- Introducción de expresiones lambda y Stream API
- Interface funcionales y métodos default
- Nuevo API de fecha y hora
- Nashorn JavaScript Engine

**Java 9 (2017)** - Modularización:
- Sistema de módulos (Proyecto Jigsaw)
- Factory methods para colecciones
- JShell (REPL)
- Mejoras en Process API

**Java 10 (2018)**:
- Inferencia de tipo local (var)
- Garbage Collector G1 como predeterminado
- APIs paralelas para colecciones

**Java 11 (2018)** - LTS:
- Ejecución de archivos fuente con un solo comando
- Métodos nuevos en String (isBlank, lines, strip)
- HttpClient estandarizado

**Java 12-16 (2019-2021)**:
- Switch expressions (Java 12, estándar en Java 14)
- Text blocks (Java 13, estándar en Java 15)
- Records (Preview en Java 14, estándar en Java 16)
- Pattern matching for instanceof (Preview en Java 14, estándar en Java 16)
- Sealed classes (Preview en Java 15)

**Java 17 (2021)** - LTS:
- Pattern matching for switch (Preview)
- Sealed Classes (Estándar)
- Foreign Function & Memory API (Incubator)
- Restauración de Always-Strict Floating-Point Semantics

**Java 18-20 (2022-2023)**:
- UTF-8 por defecto
- Simple Web Server
- Foreign Function & Memory API (avances)
- Vector API (Incubator)

**Java 21 (2023)** - LTS:
- Virtual Threads (Proyecto Loom)
- Record Patterns
- Pattern Matching para switch (Estándar)
- Scoped Values
- Sequenced Collections
- Foreign Function & Memory API (Estándar)

### Cambios significativos en el ciclo de lanzamiento de versiones (5 min)

A partir de 2017, Oracle cambió radicalmente la estrategia de lanzamiento de Java:

**Antes (Java 1.0 - Java 8)**:
- Ciclos de desarrollo impredecibles (2-5 años)
- Grandes actualizaciones con muchas características

**Ahora (Java 9+)**:
- Ciclo de lanzamiento semestral (marzo y septiembre)
- LTS (Long-Term Support) cada 2 años aproximadamente:
    - Java 8 (Marzo 2014)
    - Java 11 (Septiembre 2018)
    - Java 17 (Septiembre 2021)
    - Java 21 (Septiembre 2023)
- Características introducidas gradualmente:
    - **Incubator**: Características experimentales
    - **Preview**: Casi finalizadas pero sujetas a cambios
    - **Permanent**: Estabilizadas y garantizadas

Este nuevo modelo permite:
- Retroalimentación más rápida de la comunidad
- Adopción gradual de características
- Mayor estabilidad en versiones LTS

### Características principales añadidas en cada versión relevante (7 min)

Vamos a analizar las características más impactantes añadidas a Java en cada versión LTS desde Java 8:

**Java 8**:
```java
// Expresiones lambda
List<String> names = Arrays.asList("Ana", "Carlos", "Berta");
names.sort((s1, s2) -> s1.compareTo(s2));

// Stream API
long count = names.stream()
                 .filter(s -> s.startsWith("A"))
                 .count();
```

**Java 11**:
```java
// Métodos de String
String text = "  Hola\nMundo  ";
System.out.println(text.strip());  // "Hola\nMundo"
System.out.println(text.lines().count());  // 2

// HttpClient
HttpClient client = HttpClient.newHttpClient();
HttpRequest request = HttpRequest.newBuilder()
      .uri(URI.create("https://ejemplo.com"))
      .build();
client.sendAsync(request, HttpResponse.BodyHandlers.ofString())
      .thenApply(HttpResponse::body)
      .thenAccept(System.out::println);
```

**Java 17**:
```java
// Sealed Classes
public sealed class Shape permits Circle, Rectangle, Triangle {
    // código común
}

public final class Circle extends Shape {
    private final double radius;
    // implementación
}

// instanceof Pattern Matching
Object obj = "Hello";
if (obj instanceof String s && s.length() > 0) {
    // Podemos usar 's' directamente
    System.out.println(s.toUpperCase());
}
```

**Java 21**:
```java
// Virtual Threads
try (var executor = Executors.newVirtualThreadPerTaskExecutor()) {
    IntStream.range(0, 10_000).forEach(i -> {
        executor.submit(() -> {
            Thread.sleep(Duration.ofSeconds(1));
            return i;
        });
    });
}  // Podemos manejar miles de hilos sin problemas

// Pattern Matching para switch
Object obj = "Hello";
String result = switch (obj) {
    case Integer i -> "Es un entero: " + i;
    case String s -> "Es un String: " + s;
    case null -> "Es null";
    default -> "Otro tipo: " + obj.getClass();
};

// Record Patterns
record Point(int x, int y) {}
record Rectangle(Point upperLeft, Point lowerRight) {}

Rectangle r = new Rectangle(new Point(1, 2), new Point(3, 4));

if (r instanceof Rectangle(Point(int x1, int y1), Point(int x2, int y2))) {
    int width = x2 - x1;
    int height = y2 - y1;
    System.out.println("Área: " + width * height);
}
```

## 3. Principios fundamentales de POO (25 minutos)

### Abstracción (5 min)

La abstracción permite centrarse en lo que hace un objeto en lugar de cómo lo hace.

**Concepto:**
- Identificar las características esenciales de un objeto
- Ignorar detalles irrelevantes
- Crear modelos simplificados

**En Java 21:**
```java
// Ejemplo de abstracción con interfaces
interface PaymentProcessor {
    boolean processPayment(double amount);
    PaymentStatus checkStatus(String paymentId);
    Receipt generateReceipt(String paymentId);
}

// Implementaciones concretas
class CreditCardProcessor implements PaymentProcessor {
    @Override
    public boolean processPayment(double amount) {
        // Lógica específica para tarjetas de crédito
        return connectToPaymentGateway(amount);
    }
    
    @Override
    public PaymentStatus checkStatus(String paymentId) {
        // Verificar estado en la pasarela de pago
        return queryGatewayStatus(paymentId);
    }
    
    @Override
    public Receipt generateReceipt(String paymentId) {
        // Generar recibo de tarjeta de crédito
        return new Receipt(paymentId, LocalDateTime.now(), "Credit Card");
    }
    
    // Métodos específicos de implementación
    private boolean connectToPaymentGateway(double amount) {
        // Detalles de implementación ocultos
        return true;
    }
    
    private PaymentStatus queryGatewayStatus(String id) {
        // Detalles de implementación ocultos
        return PaymentStatus.COMPLETED;
    }
}
```

### Encapsulamiento (5 min)

El encapsulamiento consiste en ocultar los detalles internos de una clase y exponer solo lo necesario.

**Concepto:**
- Ocultar la implementación interna
- Proteger el estado del objeto
- Proporcionar interfaces controladas

**En Java 21:**
```java
// Encapsulamiento moderno con Records
public record BankAccount(
    String accountNumber,
    BigDecimal balance
) {
    // Constructor compacto con validación
    public BankAccount {
        if (accountNumber == null || accountNumber.isBlank()) {
            throw new IllegalArgumentException("El número de cuenta no puede estar vacío");
        }
        if (balance == null || balance.compareTo(BigDecimal.ZERO) < 0) {
            throw new IllegalArgumentException("El saldo no puede ser negativo");
        }
    }
    
    // Métodos que modifican el estado devolviendo una nueva instancia
    public BankAccount deposit(BigDecimal amount) {
        if (amount.compareTo(BigDecimal.ZERO) <= 0) {
            throw new IllegalArgumentException("El monto del depósito debe ser positivo");
        }
        return new BankAccount(accountNumber, balance.add(amount));
    }
    
    public BankAccount withdraw(BigDecimal amount) {
        if (amount.compareTo(BigDecimal.ZERO) <= 0) {
            throw new IllegalArgumentException("El monto del retiro debe ser positivo");
        }
        if (amount.compareTo(balance) > 0) {
            throw new IllegalStateException("Fondos insuficientes");
        }
        return new BankAccount(accountNumber, balance.subtract(amount));
    }
}
```

### Herencia (5 min)

La herencia permite a una clase heredar atributos y comportamientos de otra clase.

**Concepto:**
- Extensión de clases existentes
- Reutilización de código
- Relación "es un"

**En Java 21:**
```java
// Herencia con clases selladas (sealed)
public sealed abstract class Employee permits FullTimeEmployee, PartTimeEmployee, Contractor {
    private final String id;
    private final String name;
    protected double baseSalary;
    
    public Employee(String id, String name, double baseSalary) {
        this.id = id;
        this.name = name;
        this.baseSalary = baseSalary;
    }
    
    // Getters
    public String getId() { return id; }
    public String getName() { return name; }
    public double getBaseSalary() { return baseSalary; }
    
    // Método abstracto que las subclases deben implementar
    public abstract double calculateMonthlySalary();
    
    // Método común a todas las subclases
    public final String generatePayslip() {
        return """
               Employee ID: %s
               Name: %s
               Monthly Salary: $%.2f
               """.formatted(id, name, calculateMonthlySalary());
    }
}

// Subclases permitidas
public final class FullTimeEmployee extends Employee {
    private final double bonusPercentage;
    
    public FullTimeEmployee(String id, String name, double baseSalary, double bonusPercentage) {
        super(id, name, baseSalary);
        this.bonusPercentage = bonusPercentage;
    }
    
    @Override
    public double calculateMonthlySalary() {
        return baseSalary + (baseSalary * bonusPercentage / 100);
    }
}

public non-sealed class PartTimeEmployee extends Employee {
    private final int hoursWorked;
    private final double hourlyRate;
    
    public PartTimeEmployee(String id, String name, double baseSalary, 
                           int hoursWorked, double hourlyRate) {
        super(id, name, baseSalary);
        this.hoursWorked = hoursWorked;
        this.hourlyRate = hourlyRate;
    }
    
    @Override
    public double calculateMonthlySalary() {
        return baseSalary + (hoursWorked * hourlyRate);
    }
}
```

### Polimorfismo (5 min)

El polimorfismo permite que objetos de diferentes clases respondan de manera distinta al mismo mensaje.

**Concepto:**
- Diferentes comportamientos bajo una interfaz común
- Permite extender sistemas sin modificar código existente
- Facilita el principio Open/Closed

**En Java 21:**
```java
// Polimorfismo con pattern matching para switch
public double calculateTax(Employee employee) {
    return switch (employee) {
        case FullTimeEmployee fte -> fte.calculateMonthlySalary() * 0.25;
        case PartTimeEmployee pte when pte.calculateMonthlySalary() > 2000 -> 
            pte.calculateMonthlySalary() * 0.15;
        case PartTimeEmployee pte -> pte.calculateMonthlySalary() * 0.10;
        case Contractor c -> c.calculateMonthlySalary() * 0.30;
    };
}

// Uso
List<Employee> employees = List.of(
    new FullTimeEmployee("E001", "Ana López", 5000, 10),
    new PartTimeEmployee("E002", "Pedro Gómez", 1000, 80, 15),
    new Contractor("C001", "Laura Pérez", 0, 120, 50)
);

double totalTax = employees.stream()
    .mapToDouble(this::calculateTax)
    .sum();
```

### Composición vs. Herencia (5 min)

La composición y la herencia son dos formas de reutilizar código, cada una con sus propias ventajas y desventajas.

**Herencia:**
- Establece una relación "es un"
- Permite reutilizar código y extender comportamiento
- Puede llevar a jerarquías complejas y frágiles

**Composición:**
- Establece una relación "tiene un"
- Mayor flexibilidad y menor acoplamiento
- Favorece la delegación sobre la extensión

**Ejemplo moderno en Java 21:**
```java
// Enfoque de composición
public record Address(String street, String city, String postalCode, String country) {}

public record ContactInfo(String email, String phone, Address address) {}

public record Customer(
    String id, 
    String name, 
    ContactInfo contactInfo,
    List<Order> orders
) {
    // Constructor que garantiza inmutabilidad de la lista
    public Customer(String id, String name, ContactInfo contactInfo, List<Order> orders) {
        this.id = id;
        this.name = name;
        this.contactInfo = contactInfo;
        this.orders = List.copyOf(orders); // Crea una copia inmutable
    }
    
    // Método que utiliza composición en lugar de herencia
    public boolean isEligibleForDiscount() {
        return orders.size() >= 5 || 
               orders.stream().mapToDouble(Order::total).sum() > 1000.0;
    }
    
    // Métodos que crean nuevas instancias en vez de modificar estado
    public Customer addOrder(Order newOrder) {
        List<Order> updatedOrders = new ArrayList<>(orders);
        updatedOrders.add(newOrder);
        return new Customer(id, name, contactInfo, updatedOrders);
    }
    
    public Customer updateContactInfo(ContactInfo newContactInfo) {
        return new Customer(id, name, newContactInfo, orders);
    }
}

record Order(String orderId, LocalDateTime orderDate, List<OrderItem> items) {
    // Método que delega a los componentes
    public double total() {
        return items.stream()
            .mapToDouble(item -> item.price() * item.quantity())
            .sum();
    }
}

record OrderItem(String productId, String description, double price, int quantity) {}
```

## 4. Aplicación al mundo real (15 minutos)

### Análisis de sistemas empresariales modernos basados en Java (8 min)

**Microservicios con Spring Boot**
- Arquitectura distribuida basada en servicios pequeños y especializados
- Cada microservicio encapsula su propia lógica y datos
- Comunicación a través de APIs bien definidas

```java
// Ejemplo: Microservicio de pedidos con Spring Boot + Java 21
@RestController
@RequestMapping("/orders")
public class OrderController {
    private final OrderService orderService;
    
    public OrderController(OrderService orderService) {
        this.orderService = orderService;
    }
    
    @GetMapping("/{id}")
    public ResponseEntity<OrderDTO> getOrderById(@PathVariable String id) {
        return orderService.findById(id)
            .map(ResponseEntity::ok)
            .orElse(ResponseEntity.notFound().build());
    }
    
    @PostMapping
    public ResponseEntity<OrderDTO> createOrder(@RequestBody @Valid OrderRequest request) {
        return ResponseEntity
            .status(HttpStatus.CREATED)
            .body(orderService.createOrder(request));
    }
}

// Servicio utilizando virtual threads para operaciones bloqueantes
@Service
public class OrderServiceImpl implements OrderService {
    private final OrderRepository orderRepository;
    private final PaymentClient paymentClient;
    
    // Constructor...
    
    @Override
    public Optional<OrderDTO> findById(String id) {
        return orderRepository.findById(id)
            .map(this::mapToDTO);
    }
    
    @Override
    public OrderDTO createOrder(OrderRequest request) {
        // Crear la orden
        Order order = new Order(
            UUID.randomUUID().toString(),
            request.customerId(),
            request.items().stream()
                .map(item -> new OrderItem(item.productId(), item.quantity(), item.price()))
                .toList(),
            OrderStatus.PENDING,
            LocalDateTime.now()
        );
        
        Order savedOrder = orderRepository.save(order);
        
        // Procesar el pago de forma asíncrona con virtual threads
        try (var executor = Executors.newVirtualThreadPerTaskExecutor()) {
            CompletableFuture.supplyAsync(() -> {
                PaymentRequest paymentRequest = new PaymentRequest(
                    savedOrder.getId(),
                    savedOrder.getCustomerId(),
                    calculateTotal(savedOrder.getItems())
                );
                return paymentClient.processPayment(paymentRequest);
            }, executor).thenAccept(paymentResult -> {
                if (paymentResult.success()) {
                    savedOrder.setStatus(OrderStatus.PAID);
                } else {
                    savedOrder.setStatus(OrderStatus.PAYMENT_FAILED);
                }
                orderRepository.save(savedOrder);
            });
        }
        
        return mapToDTO(savedOrder);
    }
    
    // Otros métodos...
}
```

**Sistemas de Big Data**
- Procesamiento masivo de datos con Apache Kafka y Java Streams
- Aprovechamiento de programación funcional para análisis de datos
- Inmutabilidad para mejorar el rendimiento y la escalabilidad

```java
// Procesamiento de flujo de eventos con Kafka
@Service
public class TransactionAnalyzerService {
    
    public void processTransactions(Stream<Transaction> transactions) {
        // Agrupar transacciones por tipo y calcular estadísticas
        Map<TransactionType, TransactionStats> statsByType = transactions
            .collect(Collectors.groupingBy(
                Transaction::type,
                Collectors.teeing(
                    Collectors.counting(),
                    Collectors.summingDouble(Transaction::amount),
                    (count, sum) -> new TransactionStats(count, sum)
                )
            ));
        
        // Detectar patrones de fraude
        List<Transaction> suspiciousTransactions = transactions
            .filter(t -> t.amount() > 10000)
            .filter(t -> t.timestamp().isAfter(LocalDateTime.now().minusHours(1)))
            .sorted(Comparator.comparing(Transaction::timestamp).reversed())
            .limit(10)
            .toList();
    }
}

record Transaction(
    String id,
    String accountId, 
    double amount, 
    TransactionType type,
    LocalDateTime timestamp
) {}

record TransactionStats(long count, double totalAmount) {}

enum TransactionType { DEPOSIT, WITHDRAWAL, TRANSFER, PAYMENT }
```

### Discusión sobre cómo los principios de POO han evolucionado en la industria (7 min)

**De Herencia a Composición**
- Movimiento desde jerarquías profundas hacia composición
- Preferencia por interfaces y delegación
- Records de Java 21 facilitan este patrón

**Inmutabilidad como principio fundamental**
- Mayor énfasis en objetos inmutables
- Beneficios para concurrencia y razonamiento sobre código
- Apoyo del lenguaje con records, Collectors.toUnmodifiableList(), etc.

**Programación Funcional complementando POO**
- Interfaces funcionales y streams
- Combinación de paradigmas funcionales y orientados a objetos
- Pattern matching para expresar lógica condicional

**Principios SOLID en la era de los microservicios**
- Single Responsibility más importante que nunca
- Dependency Inversion a través de inyección de dependencias
- Open/Closed facilitado por interfaces y composición

## Conclusión (5 minutos)

En esta primera hora hemos:
- Comprendido el alcance y metodología del curso de Java 21
- Explorado la evolución de Java desde la versión 8 hasta la 21
- Revisado los principios fundamentales de la POO y cómo se aplican con las características modernas de Java
- Analizado cómo estos principios se utilizan en sistemas empresariales reales

En las próximas sesiones profundizaremos en cada uno de estos temas, aplicándolos a través de ejercicios prácticos y casos de estudio. La base sólida que hemos establecido hoy nos permitirá aprovechar al máximo las características avanzadas de Java 21 que veremos a continuación.

¿Hay alguna pregunta sobre los temas que hemos cubierto o sobre cómo se relacionan con lo que veremos en el resto del curso?


He desarrollado el contenido completo para la primera hora del curso de Java 21, siguiendo la estructura que solicitaste. El contenido incluye:

### 1. Presentación del curso y metodología (15 min)
- Una bienvenida personalizada
- Objetivos claros del curso, incluyendo dominio de características de Java 21 y preparación para certificación
- Sistema de evaluación basado en proyectos prácticos, quizzes y proyecto final
- Recursos disponibles como repositorio GitHub y documentación relevante

### 2. Revisión histórica de Java (20 min)
- Evolución detallada desde Java 8 hasta Java 21, con las principales características de cada versión
- Explicación de los cambios en el ciclo de lanzamiento de versiones (modelo semestral y LTS)
- Ejemplos de código que muestran la evolución de características clave como expresiones lambda, HttpClient, sealed classes y virtual threads

### 3. Principios fundamentales de POO (25 min)
- Explicación detallada de cada principio (abstracción, encapsulamiento, herencia, polimorfismo)
- Ejemplos modernos usando características de Java 21 como records, sealed classes y pattern matching
- Comparación entre composición y herencia con ejemplos prácticos

### 4. Aplicación al mundo real (15 min)
- Análisis de sistemas empresariales modernos como microservicios con Spring Boot
- Ejemplos de sistemas de Big Data con programación funcional
- Discusión sobre la evolución de principios POO en la industria actual

Cada sección incluye ejemplos de código relevantes y prácticos que muestran cómo los conceptos teóricos se aplican usando características modernas de Java 21.

¿Deseas que desarrolle alguna sección adicional o que profundice en algún aspecto específico del contenido?