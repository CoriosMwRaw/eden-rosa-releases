# 📜 Historial de Versiones — Edén Rosa Software

Todas las versiones notables de esta aplicación están documentadas en este archivo siguiendo los principios de [Semantic Versioning (SemVer)](https://semver.org/spec/v2.0.0.html).

---

## [v2.4.1] — 2026-10-24
### 🛡️ Aislamiento Multi-Sucursal, Disponibilidad Dinámica en POS, Auditoría de Pedidos y Jerarquía RBAC

#### ✨ Novedades y Mejoras
- **Aislamiento de Categorías por Tienda:** Las categorías nuevas del catálogo e inventario ahora están estrictamente asociadas a su `sucursal_id`, impidiendo que categorías de pruebas o exclusivas de una sucursal se filtren al catálogo de otras tiendas físicas.
- **Protección de Categorías Canónicas Base:** Las 5 categorías canónicas del sistema (Flores principales, Arreglos, Follajes, Materiales y Accesorios) quedan blindadas contra eliminación accidental y disponibles de forma oficial para toda la red de sucursales.
- **Jerarquía Estricta en Registro de Empleados:** Un `administrador` de sucursal únicamente puede registrar o modificar roles de su nivel hacia abajo (`administrador`, `cajero`, `florista`, `repartidor`). Queda bloqueada a nivel visual en frontend y con código `403 Forbidden` en backend la asignación o manipulación de usuarios `superadmin`.
- **Auditoría y Edición Completa de Pedidos en Taller:** Botones directos de edición, cancelación y documentos en la tabla de todos los pedidos, permitiendo modificar destinatarios, logística, fechas y montos con recálculo dinámico de saldo pendiente.
- **Disponibilidad Dinámica de Recetas en Mostrador (POS):** Los arreglos calculan en tiempo real cuántas piezas pueden elaborarse (`Disponibilidad: X ramos`) según los tallos disponibles en almacén, permitiendo vender arreglos bajo demanda descontando automáticamente los insumos botánicos de la floristería.
- **Modal de Vista Rápida Botánica en POS:** Previsualización instantánea de fotografía, precio, desglose de receta floral (BOM) e inventario con clic derecho o botón de ojo exclusivo para arreglos y recetas florales (los insumos y productos individuales no lo muestran).
- **Ordenamiento por Stock y Filtro de Agotados en POS:** Los productos disponibles se muestran primero y los agotados al final, con un botón conmutador `[Ocultar Agotados]` para agilizar la venta.
- **Secuencia Numérica Estricta F1 a F9:** Menú lateral completamente ordenado y ergonómico, reubicando Compras y Proveedores (`F9`) en su módulo administrativo natural.
- **Panel de Acciones en Barra de Catálogo:** Separador visual y tarjeta contenedora para "Gestión" y "+ Nuevo Producto", evitando desalineaciones con filtros multilinea.
- **Sincronización de Imágenes de Proveedores Vía Render Proxy:** Subida transparente de recibos y logotipos a Cloudinary desde cualquier estación de trabajo sin requerir llaves locales.
- **Preservación Total de Datos Productivos:** Migraciones no destructivas (`ALTER TABLE ADD COLUMN IF NOT EXISTS`) que garantizan la integridad de existencias, órdenes y ventas del cliente.

---

## [v2.4.0] — 2026-10-23
### 🧾 Corte Z Botánico Detallado, Mini-Printer Térmica, Candado de Turno Vencido y Corte X

#### ✨ Novedades y Características
- **Corte Z Ultra-Detallado en PDF:** Generación oficial de acta de cierre con desglose de ingresos por método de pago (efectivo, tarjetas, transferencias), bitácora de salidas y gastos menores, y resumen del consumo botánico de flores e insumos despachados durante el turno.
- **Soporte de Impresión Mini-Printer Térmica (80mm / 58mm):** Impresión directa de tickets de compra para clientes sin revelar costos internos ni fórmulas de ensamble; selector de formato de ancho y prueba rápida.
- **Corte X (Auditoría Parcial en Vivo):** Consulta ágil de acumulados de ventas y arqueo esperado a mitad de turno sin cerrar la caja chica ni alterar saldos.
- **Candado de Turno Vencido:** Detección de turnos abiertos hace más de 18 horas; bloqueo preventivo que solicita asentar el corte del día anterior antes de iniciar una nueva jornada.
- **Organización de Catálogo por Rotación de Ventas:** Opción en catálogo para ordenar por "Más Vendidos (Mayor Rotación)" con insignias dinámicas sin modificar la base de datos.
- **Anulación Segura de Pedidos en Taller:** Cancelación controlada de órdenes erróneas que devuelve automáticamente flores e insumos reservados al inventario físico.

---

## [v2.3.0] — 2026-10-22
### 🔄 Aislamiento Multi-Sucursal y Blindaje Zero-Trust

- **Aislamiento Multi-Sucursal:** Filtrado inteligente en descarga para que cada terminal opere de forma privada con sus pedidos, cajas, compras e inventario físico.
- **Cambio de Tienda Resiliente:** Detección automática al iniciar sesión con usuario de otra sucursal; subida de cambios pendientes, purga de datos locales y descarga limpia.
- **Zero-Trust Proxy Gateway:** Eliminación de variables de entorno con credenciales expuestas en terminales cliente.

---

## [v2.0.0] — 2026-10-07
### 🚀 Lanzamiento Mayor 2.0: Blindaje de Caja, Kiosko y Suite Visual

#### ✨ Novedades y Características
- **Caja Chica Obligatoria:** Validación estricta que exige apertura de turno de caja antes de cobrar tickets o registrar ventas en el Punto de Venta (POS).
- **Selector Reactivo de Montos:** Accesos rápidos con un solo clic para montos habituales de apertura de turno ($300, $500, $1,000, $1,500 MXN).
- **Transición Cinematográfica de Cierre de Sesión:** Animación visual de 2.7 segundos con Remotion y partículas botánicas dinámicas al cerrar sesión.
- **Favicon Adaptativo para Pestañas:** Logotipo dinámico con canal alfa 100% transparente que alterna automáticamente según el tema del sistema operativo (modo claro / modo oscuro).
- **Avatar Personalizado de Administrador:** Integración de insignia visual `LogoAdmin.jpeg` en proporciones exactas para el usuario Administrador General.
- **Panel de Configuración Integral:** Ajustes para usuarios, matriz de permisos RBAC, personalización de sonido de bienvenida y modo kiosko.

#### 🛡️ Resiliencia y Correcciones
- **Auto-Sanación de Recetas:** Reconciliación idempotente de catálogo canónico (34 insumos y 14 recetas BOM) para terminales secundarias con bases de datos locales preexistentes.
- **Seguridad RBAC:** Matriz de permisos inviolable para los roles de trabajo, impidiendo fugas de información o manipulación de contraseñas de administradores.
- **Rescate de Contraseña en Login:** Flujo desacoplado e independiente que permite recuperar contraseñas sin requerir sesión iniciada previa.

---

## [v1.0.0] — 2026-09-15
### 📦 Versión Inicial: Arquitectura Local-First SQLite & FastAPI

- Punto de Venta táctil para mostrador con cálculo de mano de obra y cobro en menos de 4 clics.
- Catálogo y recetario de arreglos florales con explosión de materiales (BOM).
- Tablero Kanban de pedidos y taller floral con 7 estados operativos en tiempo real.
- Control de inventario perecedero con registro de mermas por marchitamiento, plaga o daño mecánico.
- Módulo de compras a mayoristas con costeo por lote.
- Generación de comprobantes y documentos operativos en formato PDF (tickets térmicos de 80 mm, hojas de taller y guías de despacho).
- Motor de sincronización asíncrona hacia PostgreSQL en Aiven Cloud para continuidad Local-First.
