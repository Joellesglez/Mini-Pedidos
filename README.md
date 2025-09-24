🏪 Mini Pedidos – Kotlin




#  Descripción

Mini Pedidos es una aplicación de consola en Kotlin que simula la gestión de pedidos de una cafetería.
Permite crear pedidos, avanzar su estado, calcular totales y cobrar siguiendo reglas de negocio.

Es un proyecto de práctica para conceptos clave de Kotlin:

enum class para estados del pedido.

interface para capacidades como cobro.

companion object para fábrica de pedidos y contador de IDs.

Validación de flujo de estados.

#  Características

Creación de pedidos: Pedido.crear(cliente, items)

Avance de estado: CREADO → EN_PREPARACION → LISTO → ENTREGADO

Cobro seguro: solo se puede cobrar un pedido si está LISTO

Resumen de pedidos: muestra id, cliente, estado y total

Items de pedido: cada pedido puede tener múltiples items (nombre, precio, cantidad)

#  Estructura del proyecto

MiniPedidos/
├─ src/
│  └─ main/
│     └─ kotlin/
│        ├─ Item.kt           // Data class Item
│        ├─ EstadoPedido.kt   // Enum class con estados
│        ├─ Cobrable.kt       // Interface de cobro
│        ├─ Pedido.kt         // Clase principal con companion object y lógica
│        └─ Main.kt           // Demo de uso y pruebas
├─ build.gradle.kts            // Configuración de Gradle
└─ settings.gradle.kts         // Configuración de proyecto

#  Instalación y ejecución
Requisitos

JDK 17 o superior (se recomienda para Gradle 8+)

IntelliJ IDEA

Gradle sincronizado

Comandos de Gradle

# Construir el proyecto
./gradlew build

# Ejecutar la aplicación
./gradlew run

# Ejemplo de uso en Main.kt
fun main() {
    val items1 = listOf(Item("Café", 1.5, 2), Item("Donut", 2.0, 1))
    val pedido1 = Pedido.crear("Ana", items1)
    
    pedido1.avanzarEstado() // CREADO -> EN_PREPARACION
    pedido1.avanzarEstado() // EN_PREPARACION -> LISTO
    val cobrado = pedido1.cobrar() // true si está listo
    
    println("Pedido ${pedido1.id} cobrado: $cobrado")
    println("Resumen: ${pedido1}")
}


# Salida esperada:

Pedido 1 cobrado: true
Resumen: Pedido(id=1, cliente=Ana, estado=ENTREGADO, total=5.0)

Capturas de pantalla (simuladas y con nombres modificados)

Vista de la consola:

Creando pedidos...
Pedido 1: Amador, estado CREADO, total 5.0
Pedido 2: Luisa, estado CREADO, total 3.5
Avanzando estados...
Cobro de pedido 1: OK
Resumen final de pedidos:
ID:1 Cliente: Ana Estado: ENTREGADO Total: 5.0
ID:2 Cliente: Luis Estado: CREADO Total: 3.5

#  Retos opcionales para este repositorio

Implementar descuentos VIP usando otra interface Descontable

Mejorar toString() para un resumen más legible

Añadir parsing desde texto para crear pedidos desde input del usuario



#                                                                                   Este proyecto está bajo la licencia MIT.
