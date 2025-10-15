## Guía de Administración (Obsidian)

> Vista compacta y navegable para administradores. Enlaces entre módulos y focos de gestión.

### Índice
- [[#Dashboard]]
- [[#Agenda]]
- [[#Pedidos]]
- [[#Clientes]]
- [[#Activos]]
- [[#KPIs-y-Reportes]]
- [[#Seguridad-y-Accesos]]

---

### Dashboard
**Propósito**: visión ejecutiva del negocio.

- Filtros: Hoy / Semana / Mes.
- Métricas: Ingresos, Pedidos activos, Entregas a tiempo, Valor de inventario.
- Bloques clave: Estado de producción, Clientes (nuevos/activos), Contratos (valor/pagos por vencer), Productos más vendidos, Pedidos recientes, Entregas de hoy.
- Acciones rápidas: abrir [[#Pedidos]]/[[#Activos]]/[[#Agenda]]/[[#KPIs-y-Reportes]].

> Sugerencia: revisar diariamente Pedidos recientes y Entregas de hoy para priorización operativa.

Enlaces: [[#KPIs-y-Reportes]] · [[#Pedidos]] · [[#Agenda]] · [[#Activos]]

---

### Agenda
**Propósito**: organizar sesiones, entregas y recordatorios.

- Vistas: Día, Semana, Mes, Trimestral.
- Operaciones: crear/editar/eliminar eventos; ver detalles (cliente, lugar, fecha/hora, estado).
- Filtros: por tipo de evento (Sesión, Entrega, Recordatorio).
- Uso típico admin: confirmar eventos críticos, resolver solapes, coordinar recursos.

Enlaces: [[#Pedidos]] (fechas de contratos/ventas) · [[#Dashboard]]

---

### Pedidos
**Propósito**: creación y control de pedidos.

- Tipos: Proforma (cotización), Nota de Venta (venta inmediata), Contrato (pago parcial y programación).
- Funciones clave:
  - Estados: Pendiente → En Proceso → Completado/Cancelado.
  - Gestión de productos/servicios, totales, a cuenta y saldo.
  - Búsqueda y filtros (número, cliente, tipo, estado).
- Uso típico admin: seguimiento de estados, ver saldos, coordinar entregas con [[#Agenda]] y stock con [[#Activos]].

Enlaces: [[#Clientes]] · [[#Agenda]] · [[#Activos]] · [[#KPIs-y-Reportes]]

---

### Clientes
**Propósito**: base central de clientes.

- Tipos: Particular, Colegio, Empresa.
- Funciones: alta/edición, búsqueda, segmentación por tipo.
- KPIs por cliente: total de pedidos, monto gastado, último pedido.
- Uso típico admin: actualización de datos clave, segmentación para campañas y priorización comercial.

Enlaces: [[#Pedidos]] · [[#KPIs-y-Reportes]]

---

### Activos
**Propósito**: ciclo de vida de activos físicos/digitales.

- Pestañas: Activos · Financiamientos · Mantenimientos · Repuestos.
- Activos: categoría, proveedor, costo, vida útil, depreciación, estado.
- Financiamientos: entidad, monto, cuotas, estado. Eliminar financiamiento → tipo de pago “Contado”.
- Mantenimientos: preventivo/correctivo, costo, proveedor, próximo mantenimiento. Eliminar → estado “Activo”.
- Repuestos: stock y costos básicos; relación conceptual con mantenimientos.
- Uso típico admin: asegurar disponibilidad operativa, controlar costos y programar mantenimientos.

Enlaces: [[#KPIs-y-Reportes]] · [[#Agenda]] (cuando aplique) · [[#Pedidos]] (impacto indirecto por capacidad operativa)

---

### KPIs y Reportes
**Propósito**: evaluación del rendimiento y toma de decisiones.

- KPI sugeridos: Ingresos por periodo, Conversión de pedidos, Tiempo de entrega, Stock bajo, Coste de mantenimiento, Valor de contratos por vencer.
- Prácticas: revisar variaciones vs. periodo anterior; priorizar alertas (pagos por vencer, atrasos, stock crítico).

Enlaces: [[#Dashboard]] · [[#Pedidos]] · [[#Activos]] · [[#Clientes]]

---

### Seguridad y Accesos
**Rol Admin**: acceso a configuración y permisos ampliados.

- Sesión: autenticación con rol; control de permisos por función.
- Buenas prácticas: rotación de contraseñas, alta de usuarios con mínimos privilegios necesarios, revisión periódica de accesos.

Enlaces: [[#Dashboard]]


