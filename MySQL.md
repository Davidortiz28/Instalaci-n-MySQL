# Introducción a MySQL e Instalación

> Guía completa para estudiantes de programación técnica: historia, características, ventajas y puesta en marcha de MySQL.

---

## ¿Qué es MySQL?

MySQL es una base de datos **relacional de código abierto** que nació en **1995** de la mano de Michael "Monty" Widenius, con el objetivo de ofrecer un sistema rápido, confiable y accesible para la comunidad de desarrolladores.

Cualquier aplicación que podamos imaginar requiere almacenar datos: listas de usuarios, permisos y propiedades. MySQL resuelve esta necesidad de forma eficiente y universal.

| Característica | Descripción |
|---|---|
| **Código Abierto** | Accesible para todos los desarrolladores sin costes de licencia |
| **Relacional** | Organiza datos en tablas interconectadas de forma eficiente |
| **Universal** | Usado desde pequeñas empresas hasta grandes corporaciones |

---

## Historia

| Período | Hito |
|---|---|
| 1995–1996 | Fundación de TcX y lanzamiento de MySQL 3.11 |
| 1998–2000 | Creación de MySQL AB; versión 3.23 con índices y UNION |
| 2005 | MySQL 5.0: transacciones, procedimientos almacenados y vistas |
| 2008–2010 | Adquisición por Sun Microsystems (~$1.000M) y luego por Oracle |

// Aquí va una foto de la línea del tiempo de MySQL //

---

## Características Técnicas

- **Bases de Datos Relacionales:** tablas interconectadas para una organización efectiva de la información.
- **Arquitectura Cliente-Servidor:** clientes independientes realizan consultas, modifican datos y crean tablas.
- **Compatibilidad SQL:** lenguaje estándar de la industria; facilita la migración desde otros sistemas.
- **Sistema de Transacciones:** garantiza la integridad — todas las operaciones se completan o ninguna se aplica.

Desde la versión 5.0, MySQL también soporta **vistas personalizadas**, **procedimientos almacenados** y **disparadores (triggers)** para automatizar tareas.

---

## Ventajas

- Código abierto: reduce costes de licencia y mantenimiento.
- Comunidad activa con recursos y soporte constante.
- Válido para empresas de todos los tamaños.
- Alternativa confiable y estandarizada frente a soluciones costosas.

---

## Clientes Populares

| Cliente | Descripción |
|---|---|
| **MySQL Workbench** | Herramienta oficial de Oracle, todo en uno |
| **HeidiSQL** | Código abierto, compatible con MySQL, PostgreSQL y SQLite |
| **Navicat** | Multiplataforma con diseño visual avanzado |
| **DBeaver** | Universal y de código abierto |
| **Sequel Pro** | Exclusivo para macOS, interfaz simple |

---

## MySQL Workbench

MySQL Workbench nació en **2007** como herramienta unificada para diseño, modelado, administración y consultas SQL. Desarrollada por MySQL AB, pasó a Oracle en 2010.

### Funcionalidades principales

| Función | Descripción |
|---|---|
| **Modelado Visual** | Diseña tablas, relaciones y vistas de forma gráfica |
| **Editor SQL** | Escribe, depura y ejecuta consultas SQL fácilmente |
| **Administración** | Gestiona usuarios, privilegios, copias de seguridad y registros |
| **Migración y Exportación** | Migra datos desde otras bases y exporta en CSV, SQL, JSON |
| **Automatización** | Scripts en Python o SQL para programar tareas repetitivas |
| **Sincronización** | Compara y sincroniza esquemas entre bases de datos |

---

## Instalación en Windows

### Paso 1 — Descargar el instalador

Visita [dev.mysql.com/downloads/workbench](https://dev.mysql.com/downloads/workbench), selecciona **Microsoft Windows** y descarga el instalador.

Tienes dos opciones:
- **MySQL Installer MSI** (web, ~2 MB): descarga componentes durante la instalación.
- **MySQL Installer MSI** (completo, ~566 MB): incluye todo sin conexión adicional.

> Se recomienda el instalador completo si tu conexión es lenta o inestable.

<a href="https://ibb.co/jPVVm9X5"><img src="https://i.ibb.co/rRbbYKrt/Captura-de-pantalla-2026-06-17-195245.png" alt="Captura-de-pantalla-2026-06-17-195245" border="0"></a>

### Paso 2 — Seleccionar productos

Al ejecutar el instalador, selecciona la opción **Custom** y agrega:
- MySQL Server 8.x (X64)
- MySQL Workbench 8.x (X64)

<a href="https://ibb.co/H0bH358"><img src="https://i.ibb.co/R1sDdRw/Captura-de-pantalla-2026-06-17-184320.png" alt="Captura-de-pantalla-2026-06-17-184320" border="0"></a>

### Paso 3 — Configurar contraseña del root

En el paso **Accounts and Roles**, define una contraseña segura para el usuario `root`.

> ⚠️ Guarda bien esta contraseña, la necesitarás para conectarte desde Workbench.

<a href="https://ibb.co/vxBBb9bx"><img src="https://i.ibb.co/pvPPgqgv/Captura-de-pantalla-2026-06-17-184349.png" alt="Captura-de-pantalla-2026-06-17-184349" border="0"></a>

### Paso 4 — Aplicar configuración

En el paso **Apply Configuration**, haz clic en **Execute** y espera a que todos los pasos se completen con ✅.

<a href="https://ibb.co/Rp3MJdRC"><img src="https://i.ibb.co/QFPqxty6/Captura-de-pantalla-2026-06-17-182858.png" alt="Captura-de-pantalla-2026-06-17-182858" border="0"></a>

### Paso 5 — Conectarse desde Workbench

Abre MySQL Workbench, haz doble clic en **Local instance MySQL80** e ingresa la contraseña del usuario root.

<a href="https://imgbb.com/"><img src="https://i.ibb.co/n8PXcxk0/Captura-de-pantalla-2026-06-17-183121.png" alt="Captura de pantalla 2026 06 17 183121" border="0"></a>

---

## Primera Query en Workbench

Sigue estos pasos para crear tu primera base de datos:

1. Abrir Workbench
2. Conectar al servidor (doble clic en Local instance)
3. Abrir una nueva pestaña SQL (`Ctrl+T`)
4. Escribir el siguiente script
5. Ejecutar con `Ctrl+Shift+Enter`

```sql
-- Creamos la base de datos
CREATE DATABASE MiBaseDeDatos;
USE MiBaseDeDatos;

-- Tabla Usuarios
CREATE TABLE Usuarios (
    usuario_id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50),
    apellido VARCHAR(50),
    correo VARCHAR(100)
);

-- Tabla Pedidos
CREATE TABLE Pedidos (
    pedido_id INT AUTO_INCREMENT PRIMARY KEY,
    usuario_id INT,
    fecha_pedido DATE,
    total DECIMAL(10,2),
    FOREIGN KEY (usuario_id) REFERENCES Usuarios(usuario_id)
);
```

Si todo salió bien, verás 4 marcas verdes ✅ en el panel **Output**:

<a href="https://ibb.co/Ng44GmWT"><img src="https://i.ibb.co/XfwwG3FY/Captura-de-pantalla-2026-06-17-183656.png" alt="Captura-de-pantalla-2026-06-17-183656" border="0"></a>

Para verificar, ve a la pestaña **Schemas** y refresca la lista. Deberías ver **mibasededatos** con sus tablas.

<a href="https://ibb.co/LzQ1vFW4"><img src="https://i.ibb.co/vxskDFG2/Captura-de-pantalla-2026-06-17-183951.png" alt="Captura-de-pantalla-2026-06-17-183951" border="0"></a>
