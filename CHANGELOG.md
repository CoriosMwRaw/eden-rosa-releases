# 📜 Historial de Versiones — Edén Rosa Software

Todas las versiones notables de esta aplicación están documentadas en este archivo siguiendo los principios de [Semantic Versioning (SemVer)](https://semver.org/spec/v2.0.0.html).

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
- **Seguridad RBAC:** Matriz de permisos inviolable para los 4 roles de trabajo (`superadmin`, `cajero`, `florista`, `repartidor`), impidiendo fugas de información o manipulación de contraseñas de administradores.
- **Rescate de Contraseña en Login:** Flujo desacoplado e independiente que permite recuperar contraseñas sin requerir sesión iniciada previa.

---

## [v1.0.0] — 2026-09-15
### 📦 Versión Inicial: Arquitectura Local-First SQLite & FastAPI

#### ✨ Características Fundacionales
- Punto de Venta táctil para mostrador con cálculo de mano de obra y cobro en menos de 4 clics.
- Catálogo y recetario de arreglos florales con explosión de materiales (BOM).
- Tablero Kanban de pedidos y taller floral con 7 estados operativos en tiempo real.
- Control de inventario perecedero con registro de mermas por marchitamiento, plaga o daño mecánico.
- Módulo de compras a mayoristas con costeo por lote.
- Generación de comprobantes y documentos operativos en formato PDF (tickets térmicos de 80 mm, hojas de taller y guías de despacho).
- Motor de sincronización asíncrona hacia PostgreSQL en Aiven Cloud para continuidad Local-First.
