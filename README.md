# 🌸 Edén Rosa Software — Distribución Oficial de Instaladores y Versiones

<div align="center">

[![Latest Release](https://img.shields.io/badge/Release-v2.4.1-E02475?style=for-the-badge&logo=windows&logoColor=white)](https://github.com/CoriosMwRaw/eden-rosa-releases/releases/latest)
[![Plataforma](https://img.shields.io/badge/Plataforma-Windows%2010%20%2F%2011%20(x64)-1B365D?style=for-the-badge&logo=microsoft&logoColor=white)](https://github.com/CoriosMwRaw/eden-rosa-releases)
[![Arquitectura](https://img.shields.io/badge/Arquitectura-Local--First%20%7C%20Cloud%20Sync-2B6CB0?style=for-the-badge&logo=sqlite&logoColor=white)](https://github.com/CoriosMwRaw/eden-rosa-releases)
[![Licencia](https://img.shields.io/badge/Licencia-Comercial%20Privada-4A5568?style=for-the-badge)](https://github.com/CoriosMwRaw/eden-rosa-releases)

**Repositorio público oficial para la descarga de instaladores ejecutables (`.exe`), manifiestos de actualización y notas de lanzamiento de Edén Rosa Software (ERP / POS Floral Boutique).**

[📥 Descargar Última Versión Oficial (v2.4.1)](https://github.com/CoriosMwRaw/eden-rosa-releases/releases/latest) • [📋 Historial Completo de Cambios](CHANGELOG.md) • [⚙️ Guía de Publicación](#-guía-para-el-equipo-de-desarrollo-publicación-de-versiones)

</div>

---

## 📌 Descripción del Software

**Edén Rosa Software** es una plataforma integral de grado empresarial diseñada a la medida para optimizar y controlar al 100% las operaciones de **Florería Edén Rosa Boutique**:

* **Punto de Venta de Mostrador (POS Táctil & Teclado):** Cobro ágil en menos de 4 clics, atajos rápidos de teclado (`F1`-`F12`), búsqueda instantánea (`Ctrl+B`), soporte para venta de arreglos catalogados e insumos sueltos, y bloqueo automático de venta ante existencias agotadas.
* **Soporte de Impresión Mini-Printer Térmica (80mm / 58mm):** Impresión directa de tickets de compra para clientes sin revelar costos internos de flor ni desgloses de recetas; selector de formato de ancho de papel y modo de prueba rápida.
* **Caja Chica, Arqueos de Turno y Doble Corte (Corte X y Corte Z):**
  * **Corte X (Auditoría Parcial):** Consulta rápida de acumulados a mitad de jornada por método de pago (efectivo, tarjeta, transferencia) sin cerrar turno ni alterar saldos.
  * **Corte Z (Cierre Oficial Definitivo):** Acta en PDF con desglose fiscal/operativo completo, arqueo ciego, bitácora de salidas con motivos y **resumen botánico del consumo de flores e insumos** despachados durante el turno.
  * **Candado de Turno Vencido:** Detección de turnos abiertos hace más de 18 horas para forzar el arqueo antes de iniciar una nueva jornada.
* **Taller Floral y Tablero Kanban:** Flujo operativo multicanal en 7 estados, captura obligatoria de dedicatorias, ficha técnica de ensamble y **anulación segura de pedidos** que revierte automáticamente las flores e insumos al inventario físico.
* **Inventario Perecedero, Escandallo BOM & Rotación de Ventas:** Control de stock físico en tiempo real con registro de mermas (marchitamiento, rotura, plaga), costeo automático de mano de obra y ordenamiento visual por **"Mayor Rotación de Ventas"**.
* **Aislamiento Multi-Sucursal Estricto:** Cada sucursal física opera de forma privada y autónoma. Las 5 categorías canónicas base se preservan para toda la red, mientras que las categorías e insumos personalizados pertenecen estrictamente a su sucursal de origen.
* **Seguridad y Jerarquía RBAC:** Matriz inviolable de 5 roles (`superadmin`, `administrador`, `cajero`, `florista`, `repartidor`), con protección estricta que impide que administradores de sucursal escalen privilegios o manipulen cuentas de Superadministrador.
* **Arquitectura Local-First Resiliente:** Operación ininterrumpida sin internet gracias al motor local SQLite (WAL mode), con auto-sincronización bidireccional y transparente en segundo plano hacia PostgreSQL Cloud (Aiven).

---

## 💻 Requisitos del Sistema

| Componente | Requisito Mínimo | Requisito Recomendado |
| :--- | :--- | :--- |
| **Sistema Operativo** | Windows 10 (64 bits, versión 1909+) | Windows 11 (64 bits, última compilación) |
| **Procesador** | Intel Core i3 / AMD Ryzen 3 (2.0 GHz) | Intel Core i5 / AMD Ryzen 5 o superior |
| **Memoria RAM** | 4 GB | 8 GB o superior |
| **Espacio en Disco** | 500 MB libres para aplicación y base de datos | 2 GB libres en unidad de estado sólido (SSD) |
| **Mini-Printer de Tickets** | Opcional (Impresora térmica USB ESC/POS 58mm o 80mm) | Impresora térmica 80mm con autocorte |
| **Resolución de Pantalla** | 1366 × 768 píxeles | 1920 × 1080 píxeles (Soporte táctil) |

---

## 🚀 Guía de Instalación Rápida

1. **Descargar el Instalador Oficial:** Dirígete a la sección de [Última Versión (Releases)](https://github.com/CoriosMwRaw/eden-rosa-releases/releases/latest) y descarga el archivo `EdenRosa_Setup_v2.4.1.exe`.
2. **Ejecutar como Administrador:** Haz doble clic sobre el instalador. Si Windows SmartScreen muestra una advertencia al ser un software privado nuevo, haz clic en *Más información* y luego en *Ejecutar de todas formas*.
3. **Asistente de Instalación Guiado:** El instalador registrará la aplicación en `%LOCALAPPDATA%\EdenRosa\`, creará los accesos directos en el Escritorio y el Menú Inicio, y configurará el motor de base de datos local seguro.
4. **Inicio de Sesión:** Inicia el software e ingresa con las credenciales correspondientes a tu rol:
   * **Superadministrador:** Control global del sistema, multi-tienda y soporte de alto nivel.
   * **Administrador de Sucursal:** Operación total de la tienda asignada, inventarios, compras, cortes de caja y personal de sucursal.
   * **Cajero:** Cobro en punto de venta, arqueo de turno y abonos de pedidos.
   * **Florista:** Tablero Kanban de taller, recetas botánicas y preparación de pedidos.
   * **Repartidor:** Consulta de entregas, hojas de ruta y confirmación de despacho.

---

## 🛠️ Guía para el Equipo de Desarrollo: Publicación de Versiones

Tanto **César Alberto López Martínez** ([@CoriosMwRaw](https://github.com/CoriosMwRaw)) como **Kevin de Jesús Ramírez López** ([@KeVINj29](https://github.com/KeVINj29)) cuentan con permisos de escritura y mantenimiento en este repositorio.

### Paso 1: Generar el Paquete Instalador
Desde la carpeta raíz del código fuente (`eden-floreria-software`):
```powershell
# 1. Asegurar que la suite completa de pruebas pase al 100% (93/93)
.venv\Scripts\python.exe -m pytest

# 2. Compilar el instalador ejecutable de producción con Inno Setup
python scripts/build_installer.py
```
El instalador resultante se ubicará en: `installer/Output/EdenRosa_Setup_v2.4.1.exe`.

### Paso 2: Crear el Tag y Release en GitHub
Desde la interfaz web de GitHub:
1. Accede a [https://github.com/CoriosMwRaw/eden-rosa-releases/releases/new](https://github.com/CoriosMwRaw/eden-rosa-releases/releases/new).
2. Asigna la etiqueta semántica: `v2.4.1` (creando un nuevo tag al publicar).
3. Asigna el título oficial: `Edén Rosa Software v2.4.1`.
4. Añade el resumen de notas de la versión (*Release Notes* / *Changelog*).
5. Adjunta el archivo instalador `EdenRosa_Setup_v2.4.1.exe` generado en el Paso 1.
6. Haz clic en **Publish release**.

### Paso 3: Actualizar el Manifiesto de Versión
Actualiza el archivo `release-manifest.json` en la rama `main` de este repositorio con la versión `2.4.1` y la URL del release. El servicio de actualización automática en segundo plano de las terminales instaladas detectará el nuevo release y ofrecerá la actualización en 1 clic.

---

## 👥 Colaboradores del Proyecto

* **César Alberto López Martínez** ([@CoriosMwRaw](https://github.com/CoriosMwRaw)) — Líder de Proyecto & Desarrollador Backend
* **Kevin de Jesús Ramírez López** ([@KeVINj29](https://github.com/KeVINj29)) — Co-Desarrollador, Líder Técnico Frontend & Base de Datos

---

<div align="center">
  <sub>Edén Rosa Boutique Floral • Software de Alta Disponibilidad para Floristerías Premium.</sub>
</div>
