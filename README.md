# CDE Truck & Car Repair — Sistema de Taller (mecsys)

Aplicación web de gestión interna para control de órdenes de trabajo, control de inventario por rack, catálogo de partes y solicitudes de compra para taller mecánico de camiones y trailers.

---

## 📌 Enlaces y Cuentas Vinculadas

*   **Repositorio GitHub:** [https://github.com/cdetruck/mecsys](https://github.com/cdetruck/mecsys) (rama `main`)
*   **Página activa (GitHub Pages):** [https://cdetruck.github.io/mecsys/](https://cdetruck.github.io/mecsys/)
*   **Proyecto Firebase:** `cdetruck-mecsys-18472`
*   **Cuenta de Firebase vinculada:** `chris-ai-teck@gmail.com`

---

## ⚠️ Arquitectura de Datos y Almacenamiento

> ### Declaración de Privacidad y Almacenamiento Externo
> **Esta aplicación NO guarda ningún archivo, documento ni PDF en el servidor Firebase.**
>
> 1. **Uso de Firebase:**
>    * Firebase Realtime Database se utiliza **únicamente como puente de conexión y sincronización en tiempo real** entre los dispositivos del taller (computadoras, teléfonos celulares y tablets).
>    * Solo viaja texto y metadatos ligeros (número de orden, descripción, servicios seleccionados, cantidad de piezas en rack y estados del trabajo).
>
> 2. **Almacenamiento de Archivos y Documentos:**
>    * Todos los documentos generados (Órdenes de Trabajo, Hojas de Firma de Clientes, Órdenes de Compra a Proveedor y respaldos CSV/JSON) **se descargan o imprimen directamente de forma externa dentro de la memoria del dispositivo del usuario**.
>    * No se utiliza Firebase Storage ni almacenamiento en la nube para retener archivos pesados, garantizando un servicio 100% libre de costos de almacenamiento y evitando saturación de cuotas.
>
> 3. **Firmas de Clientes (Work Signed):**
>    * La confirmación de firma se gestiona mediante comprobación de estado (`Work Signed`) con registro de fecha y hora.
>    * Las hojas físicas o digitales firmadas son custodiadas en la memoria local de la computadora o teléfono que genera la orden.

---

## Estructura del Sistema

1. **Tablero (Board):**
   * Control de cola de trabajo (*En fila*, *En progreso*, *Terminado*).
   * Asignación de mecánico líder y compañeros de equipo.
   * Gestión de piezas por orden y retiro del rack.
   * Visualización de Work Order e impresión directa para firma del cliente.

2. **Bodega (Warehouse):**
   * Inventario de piezas con ubicación por estante/rack (A1, B2, etc.).
   * Carrito de piezas activas por mecánico.
   * Entradas y salidas de stock con historial de movimientos.

3. **Comprar (Vendor):**
   * Catálogo de proveedor integrado.
   * Flujo de requisiciones: Solicitado $\rightarrow$ Aprobado $\rightarrow$ Enviado $\rightarrow$ Recibido en bodega.
   * Impresión directa de Orden de Compra (PO).

4. **Servicios (Services):**
   * Catálogo de tarifas planas y mano de obra por hora.

5. **Equipo (Team):**
   * Estado de mecánicos (*Working* / *Idle*), especialidades y piezas pendientes de retorno.
