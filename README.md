# 🌸 Edén Rosa Software — Distribución Oficial de Instaladores y Versiones

<div align="center">

[![Latest Release](https://img.shields.io/badge/Release-v2.0.0-E02475?style=for-the-badge&logo=windows&logoColor=white)](https://github.com/CoriosMwRaw/eden-rosa-releases/releases/latest)
[![Plataforma](https://img.shields.io/badge/Plataforma-Windows%2010%20%2F%2011%20(x64)-1B365D?style=for-the-badge&logo=microsoft&logoColor=white)](https://github.com/CoriosMwRaw/eden-rosa-releases)
[![Arquitectura](https://img.shields.io/badge/Arquitectura-Local--First%20%7C%20Cloud%20Sync-2B6CB0?style=for-the-badge&logo=sqlite&logoColor=white)](https://github.com/CoriosMwRaw/eden-rosa-releases)
[![Licencia](https://img.shields.io/badge/Licencia-Comercial%20Privada-4A5568?style=for-the-badge)](https://github.com/CoriosMwRaw/eden-rosa-releases)

**Repositorio público oficial para la distribución de instaladores ejecutables (`.exe`), paquetes de actualización y notas de lanzamiento de Edén Rosa Software (ERP / POS Floral).**

[📥 Descargar Última Versión (v2.0.0)](https://github.com/CoriosMwRaw/eden-rosa-releases/releases/latest) • [📋 Historial de Cambios](CHANGELOG.md) • [⚙️ Guía de Publicación](#-guía-para-el-equipo-de-desarrollo-publicación-de-versiones)

</div>

---

## 📌 Descripción del Software

**Edén Rosa Software** es una solución integral personalizada diseñada para optimizar y controlar todas las operaciones clave de Florería Edén Rosa:
- **Punto de Venta (POS Mostrador):** Cobro táctil rápido en menos de 4 clics, cálculo de cambio, multipago y emisión de tickets térmicos de 80 mm.
- **Taller Floral y Tablero Kanban:** Gestión multicanal de pedidos en 7 estados operativos con captura obligatoria de dedicatorias y hojas de taller.
- **Inventario Perecedero y Escandallo BOM:** Kardex automatizado de tallos, follajes y bases, con control de vida útil, registro obligatorio de mermas y fórmulas de recetas botánicas con cálculo de mano de obra.
- **Caja Chica y Arqueos de Turno:** Validación obligatoria de apertura de caja, registro de gastos menores de emergencia y cortes de caja Z con arqueo ciego.
- **CRM y Fechas Especiales:** Radar de aniversarios y cumpleaños de clientes frecuentes con enlace directo a WhatsApp en 1 clic.
- **Arquitectura Local-First:** Operación 100% ininterrumpida sin conexión a internet (SQLite local) con auto-sincronización bidireccional en segundo plano hacia PostgreSQL en Aiven Cloud.

---

## 💻 Requisitos del Sistema

| Componente | Requisito Mínimo | Requisito Recomendado |
| :--- | :--- | :--- |
| **Sistema Operativo** | Windows 10 (64 bits, versión 1909+) | Windows 11 (64 bits) |
| **Procesador** | Intel Core i3 / AMD Ryzen 3 (2.0 GHz) | Intel Core i5 / AMD Ryzen 5 o superior |
| **Memoria RAM** | 4 GB | 8 GB o superior |
| **Espacio en Disco** | 500 MB libres para aplicación y BD | 2 GB libres en unidad de estado sólido (SSD) |
| **Impresora de Tickets** | Opcional (Impresora térmica USB 80mm ESC/POS) | Impresora térmica 80mm con autocorte |
| **Resolución de Pantalla** | 1366 × 768 píxeles | 1920 × 1080 píxeles |

---

## 🚀 Guía de Instalación Rápida

1. **Descarga el instalador:** Ve a la sección de [Última Versión (Releases)](https://github.com/CoriosMwRaw/eden-rosa-releases/releases/latest) y descarga el archivo `EdenRosa-Setup-vX.X.X.exe`.
2. **Ejecutar como Administrador:** Haz doble clic sobre el archivo ejecutable. Si Windows SmartScreen muestra un aviso, presiona *Más información* y luego *Ejecutar de todas formas*.
3. **Asistente de Instalación:** Sigue los pasos en pantalla. El instalador creará el acceso directo en el Escritorio y registrará la base de datos local en `%LOCALAPPDATA%\EdenRosa\`.
4. **Inicio de Sesión:** Abre la aplicación e ingresa con las credenciales asignadas por tu rol operativo:
   - **Administrador:** Acceso completo al sistema, inventarios, compras, caja y configuraciones.
   - **Cajero:** Punto de venta, abonos de pedidos y arqueo de caja de turno.
   - **Florista:** Tablero Kanban de taller, recetario y consulta de insumos.
   - **Repartidor:** Consulta de pedidos asignados, rutas y guías de entrega.

---

## 🛠️ Guía para el Equipo de Desarrollo: Publicación de Versiones

Tanto **César Alberto López Martínez** (`CoriosMwRaw`) como **Kevin de Jesús Ramírez López** (`KeVINj29`) tienen permisos de escritura para gestionar y publicar nuevas versiones en este repositorio.

### Paso 1: Generar el Paquete Ejecutable / Instalador
Desde la carpeta raíz del código fuente (`eden-rosa-software`):
```bash
# Asegurar que todas las pruebas pasen al 100%
pytest -v

# Compilar ejecutable con PyInstaller / Inno Setup
python scripts/build_executable.py
```

### Paso 2: Crear el Tag y Release en GitHub
Puedes crear el nuevo lanzamiento directamente desde la línea de comandos usando GitHub CLI:
```bash
# Ejemplo para versión v2.0.1
gh release create v2.0.1 \
  --repo CoriosMwRaw/eden-rosa-releases \
  --title "Edén Rosa Software v2.0.1" \
  --notes "Notas de la versión: mejoras en sincronización y corrección de interfaz." \
  dist/EdenRosa-Setup-v2.0.1.exe
```

O desde la interfaz web de GitHub:
1. Entra a [https://github.com/CoriosMwRaw/eden-rosa-releases/releases/new](https://github.com/CoriosMwRaw/eden-rosa-releases/releases/new).
2. Asigna el tag semántico (ej. `v2.0.1`).
3. Asigna el título oficial y redacta las notas de cambio (*Changelog*).
4. Arrastra el archivo ejecutable `EdenRosa-Setup-vX.X.X.exe` al área de archivos adjuntos.
5. Haz clic en **Publish release**.

### Paso 3: Actualizar el Manifiesto de Versión
Actualiza el archivo `release-manifest.json` en la rama principal (`main`) para que el actualizador en segundo plano del sistema detecte y notifique la nueva versión automáticamente a las terminales clientes.

---

## 👥 Colaboradores del Proyecto

- **César Alberto López Martínez** ([@CoriosMwRaw](https://github.com/CoriosMwRaw)) — Líder de Proyecto & Desarrollador Backend
- **Kevin de Jesús Ramírez López** ([@KeVINj29](https://github.com/KeVINj29)) — Co-Desarrollador, Líder Técnico Frontend & Base de Datos
- **Cliente Patrocinadora:** Fátima Monserrat Orozco Escamilla (Florería Edén Rosa)
- **Materia:** Gestión de Proyecto de Software — 7° Semestre

---

<div align="center">
  <sub>Edén Rosa Boutique Floral • Desarrollado con ❤️ para floristerías de alta gama.</sub>
</div>
