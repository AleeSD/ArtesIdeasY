## Documentación Técnica del Sistema ArtesIdeasY

Nota para administradores: Existe una guía compacta para Obsidian en `docs/Admin-Guia-Obsidian.md`.

### 1) Descripción detallada de las 6 aplicaciones

#### A) Dashboard
- **objetivo**: vista ejecutiva con métricas de ingresos, pedidos, entregas, inventario, producción, clientes y contratos.
- **funcionalidad**:
  - Filtros temporales (hoy, semana, mes) para ajustar todas las métricas y comparativos.
  - Tarjetas de métricas con navegación contextual a secciones (por ejemplo, abrir `reportes`, `pedidos`, `produccion`, `inventario` con un clic).
  - Panel de alertas rápidas con indicadores de riesgo (atrasos, stock bajo, pagos por vencer) y enlaces de acción.
  - Bloques informativos:
    - Estado de producción: pendientes, en proceso, completadas y atrasadas.
    - Clientes: total, nuevos del periodo, activos/inactivos.
    - Contratos: valor total, activos, pagos pendientes, por vencer.
    - Productos más vendidos: ranking con unidades y valor.
    - Pedidos recientes: listado compacto con estado y acceso a detalle.
    - Entregas programadas hoy: conteo y estado de alistamiento.
  - Visualizaciones: indicadores numéricos, variaciones porcentuales y etiquetas de contexto (p. ej., “Hoy”, “Esta semana”).
  - Acciones rápidas: botones “Ver todos” por bloque para aterrizar en el módulo correspondiente.
- **datos**: actualmente datos simulados en el cliente con posibilidad de enlazar a servicios reales (API de reportes, pedidos, producción, inventario y contratos) para cifras en tiempo real.

#### B) Agenda
- **objetivo**: calendarizar y controlar sesiones, entregas y recordatorios del negocio.
- **funcionalidad**:
  - Vistas de calendario: día, semana, mes y trimestral para planificación táctica y estratégica.
  - Gestión de eventos: crear, editar, eliminar con validación básica (cliente/título, fecha y hora).
  - Clasificación por tipo (Sesión Fotográfica, Entrega, Recordatorio) y filtros rápidos por categoría.
  - Panel lateral de detalles del evento con información de cliente, fecha/hora, ubicación, descripción y estado.
  - Panel de “todos los eventos del día” para explorar rápidamente jornadas con alta densidad.
  - Paginación de próximos eventos y modales accesibles para edición/confirmación.
  - Integración prevista con otros módulos (p. ej., generar eventos desde un Contrato o Pedido).
  - Notificaciones y resaltado visual para eventos de hoy o próximos.
- **datos**: persistencia local de eventos (almacenamiento en el navegador) y capacidad de evolucionar a un backend para sincronización multiusuario y recordatorios automáticos.

#### C) Pedidos
- **objetivo**: registrar, consultar y administrar pedidos en sus diferentes modalidades.
- **funcionalidad**:
  - Creación guiada por tipo de cliente (Particular, Colegio, Empresa) y tipo de documento: Proforma, Nota de Venta, Contrato.
  - Gestión de detalle: productos/servicios, cantidades, precios, subtotales; cálculo automático de total, a cuenta y saldo.
  - Actualización de estados (Pendiente, En Proceso, Completado, Cancelado) con trazabilidad básica.
  - Búsqueda y filtros por número, cliente, tipo de documento y estado; tabla con resúmenes financieros.
  - Modales de “Observar” (detalle) y “Editar” para ajustes rápidos sin salir del listado.
  - Acciones por documento:
    - Proforma: cotización sin afectar inventario.
    - Nota de Venta: registro de venta con pago completo (saldo 0) y potencial afectación de inventario.
    - Contrato: registro con pago parcial (a cuenta), saldo pendiente y fechas programables (vinculables a Agenda).
  - Reportabilidad: totales visibles, indicadores de saldo y soporte para exportes/reportes en evolución.
  - Integración prevista con inventario (descuento de stock) y agenda (programación operativa).
- **datos**: estado y registros simulados en el cliente; diseñados para conectarse a servicios de pedidos, contratos, inventario y reportes.

#### D) Clientes
- **objetivo**: centralizar datos de clientes y facilitar su gestión comercial.
- **funcionalidad**:
  - Registro y edición de clientes de tipo Particular, Colegio y Empresa con datos de contacto y documentos (DNI/RUC).
  - Búsqueda, filtros por tipo y paginación para manejo eficiente de grandes listados.
  - Vista de detalle con KPIs: total de pedidos, monto total gastado y último pedido.
  - Acciones rápidas: crear, ver, editar y eliminar con confirmación.
  - Segmentación por tipo de cliente y soporte a campañas/acciones específicas.
  - Integración prevista con Pedidos (selección de cliente) y Reportes (análisis de valor de cliente y recurrencia).
- **datos**: información gestionada actualmente en memoria del cliente; preparada para persistencia en backend y enriquecimiento con historial de interacciones.

#### F) Activos
- **objetivo**: administrar el ciclo de vida de activos físicos y digitales del negocio.
- **funcionalidad**:
  - Registro de activos con atributos clave: categoría, proveedor, fecha de compra, costo total, vida útil, depreciación y estado.
  - Pestañas dedicadas: Activos, Financiamientos, Mantenimientos y Repuestos para una gestión integral.
  - Financiamientos: entidad, monto, cuotas, estado y cálculo de próximos pagos; ajuste automático del tipo de pago del activo.
  - Mantenimientos: preventivos/correctivos con fecha, costo, proveedor, descripción, próximo mantenimiento y estado.
  - Repuestos/Insumos: alta, edición y control básico con stock, costo y proveedor; asociación conceptual con mantenimientos.
  - Búsqueda y filtros transversales; chips visuales de estado/categoría/tipo para rápida interpretación.
  - Modales de detalle y formularios para alta/edición; confirmaciones en eliminaciones con reglas de negocio (p. ej., eliminar financiamiento → pago “Contado”; eliminar mantenimiento → estado “Activo”).
  - Integración prevista con Compras/Inventario para abastecimiento de repuestos y con Reportes para análisis de costos.
- **datos**: datos gestionados en el cliente con posibilidad de conexión a servicios de activos, financiamientos y mantenimiento para trazabilidad completa.

### 2) Detalle por aplicación

#### A) Dashboard
- **requisitos funcionales**
  - Mostrar métricas clave filtrables por tiempo.
  - Navegar a módulos relacionados desde tarjetas/listas.
  - Panel de alertas y listados recientes.
- **requisitos no funcionales**
  - Carga breve (<1–2s).
  - Responsive y accesible.
  - Estado consistente al cambiar filtro temporal.
- **diagramas de flujo**
  - Carga de datos:
    ```
    Usuario selecciona filtro → setTimeFilter → useEffect(load) → obtiene datos (mock/API) → render tarjetas/listas
    ```
  - Navegación contextual:
    ```
    Click tarjeta → onSectionChange('destino') → AppContent renderiza sección destino
    ```
- **casos de uso**
  - Ver KPIs del día/semana/mes.
  - Abrir `pedidos` desde métrica.
  - Revisar pedidos recientes.
- **interfaces/componentes**
  - `pages/dashboard/Dashboard.jsx`, `components/dashboard/StatsCard`, `components/common/QuickAlertsPanel`.
- **dependencias**
  - `App.jsx` para `onSectionChange`.
  - Futuro: `services/dataService`/`apiHelpers`.
- **reglas de negocio**
  - Cálculo de métricas por periodo.
  - Accesos rápidos abren sección pertinente.

#### B) Agenda
- **requisitos funcionales**
  - Vistas día/semana/mes/trimestre.
  - Filtro por tipo de evento.
  - CRUD de eventos; detalle y próximos con paginación.
  - Persistencia local.
- **requisitos no funcionales**
  - Interacción fluida.
  - Persistencia inmediata en `localStorage`.
  - Accesibilidad en modales (foco/teclado) deseable.
- **diagramas de flujo**
  - Crear evento:
    ```
    Click "Nuevo Evento" → Modal form → Validación → setEvents([...]) → persist localStorage
    ```
  - Ver detalle:
    ```
    Click evento → setSelectedEvent → abrir panel/modal → Editar/Eliminar
    ```
  - Eliminar:
    ```
    Click Eliminar → confirm → filter out → persist → cerrar panel
    ```
- **casos de uso**
  - Programar sesión fotográfica.
  - Ver entregas del día y su detalle.
  - Editar evento por cambio de hora.
- **interfaces/componentes**
  - `pages/management/Agenda.jsx`, `components/agenda/FilterSelect`, `EventCard`, `Pagination`, `components/common/Button`.
- **dependencias**
  - Integración con `Pedidos`/`Contratos` para programar sesiones/entregas.
- **reglas de negocio**
  - Tipos: Sesión, Entrega, Recordatorio.
  - Estados: confirmada/pendiente/cancelada.
  - Persistencia clave `agenda_events_new`.

#### C) Pedidos
- **requisitos funcionales**
  - Listado con filtros/búsqueda y totales.
  - Creación por tipo de cliente (Particular/Colegio/Empresa).
  - Tipos de documento: Proforma, Nota de Venta, Contrato.
  - Modal de observar y edición con recálculo de saldo.
  - Manejo de productos y subtotales.
- **requisitos no funcionales**
  - Validaciones mínimas.
  - Notificaciones con toasts.
  - Estado consistente entre vistas.
- **diagramas de flujo**
  - Crear proforma:
    ```
    Seleccionar "Proforma" → datos y productos → Guardar Proforma → agregar a lista (Pendiente)
    ```
  - Procesar venta:
    ```
    "Nota de Venta" → total==aCuenta → crear pedido (Completado, saldo 0)
    ```
  - Crear contrato:
    ```
    "Contrato" → aCuenta parcial → saldo = total - aCuenta → (opcional) fechas → crear pedido (Pendiente)
    ```
- **casos de uso**
  - Registrar venta directa.
  - Generar proforma.
  - Crear contrato para colegio/empresa con fechas.
- **interfaces/componentes**
  - `pages/management/Pedidos.jsx`, `useApp`, `react-toastify`.
- **dependencias**
  - Potenciales: `contratosService`, `inventario` (ajuste stock), `agenda` (programación).
  - `services/api.js` y `endpoints.orders` para backend futuro.
- **reglas de negocio**
  - Nota de venta: `aCuenta == total` y saldo 0.
  - Contrato: saldo = total - aCuenta; puede generar eventos en Agenda.
  - Estados: Pendiente, En Proceso, Completado, Cancelado.

#### D) Clientes
- **requisitos funcionales**
  - Listado con filtros/búsqueda y paginación.
  - Crear/editar cliente; eliminar con confirmación.
  - Modal de detalle con KPIs.
- **requisitos no funcionales**
  - Persistencia (actualmente en memoria); futura API.
  - Notificaciones persistentes tras acciones.
- **diagramas de flujo**
  - Alta cliente:
    ```
    Click "Nuevo Cliente" → Modal ClientForm → validar → setClients([...]) → notifyNewClient
    ```
  - Editar:
    ```
    Modal detalles → Editar → ClientForm → actualizar lista → notifyClientAction('edit')
    ```
  - Eliminar:
    ```
    Click eliminar → confirm → filter out → notifyClientAction('delete')
    ```
- **casos de uso**
  - Registrar colegio/empresa con RUC.
  - Filtrar por tipo para campañas.
- **interfaces/componentes**
  - `pages/management/Clientes.jsx`, `components/forms/ClientForm`, `components/common/Modal`, `Button`, `Card`.
- **dependencias**
  - `useApp` para notificaciones.
  - `endpoints.clients` para integración backend.
- **reglas de negocio**
  - Tipos: Particular, Colegio, Empresa.
  - KPIs: total pedidos, total gastado.

#### F) Activos
- **requisitos funcionales**
  - CRUD de activos y repuestos; alta/edición de financiamientos y mantenimientos.
  - Vistas por pestañas; filtros; modales de detalle.
- **requisitos no funcionales**
  - Estados derivados consistentes en acciones de eliminar.
  - UX clara para relaciones activo↔financiamiento/mantenimiento.
- **diagramas de flujo**
  - Crear financiamiento:
    ```
    Seleccionar activo → Nuevo Financiamiento → guardar → activo.tipoPago=Financiado/Leasing
    ```
  - Crear mantenimiento:
    ```
    Seleccionar activo → Nuevo Mantenimiento → guardar → activo.estado=según mantenimiento
    ```
  - Eliminar mantenimiento:
    ```
    Eliminar → activo.estado='Activo'
    ```
- **casos de uso**
  - Registrar equipo financiado con plan de cuotas.
  - Programar y controlar mantenimientos con insumos asociados.
- **interfaces/componentes**
  - `pages/management/Activos.jsx`, `components/forms/ActivoForm`, `FinanciamientoForm`, `MantenimientoForm`.
- **dependencias**
  - Potencial con Inventario/Compras para repuestos.
  - `useState` mocks, futura API.
- **reglas de negocio**
  - Tipo de pago: Contado/Financiado/Leasing.
  - Estados: Activo/Mantenimiento/Inactivo.
  - Colores por categoría/tipo/estado.

### 3) Especificaciones técnicas

#### Arquitectura del sistema
- SPA con React + Vite.
- Navegación condicional en `App.jsx` con `react-router-dom` y `activeSection`.
- Estado global:
  - `src/context/AuthContext.jsx` para autenticación/autorización y perfil.
  - `src/context/AppContext.jsx` para notificaciones/utilidades de UI.
- Capa de servicios:
  - `src/services/api.js`: cliente fetch con `API_BASE_URL`, timeout, `ApiError`, endpoints centralizados.
  - Servicios específicos (auth, pedidos, clientes, etc.) listos para backend; varias pantallas usan mock local.
- Componentización por dominio (`components/common`, `components/agenda`, `components/forms`, `components/dashboard`).

#### Tecnologías utilizadas
- React 18, Vite, TailwindCSS, PostCSS.
- `react-router-dom`, `lucide-react`, `react-toastify`.
- Context API, LocalStorage para persistencia simulada.
- `fetch` envuelto en `services/api.js`.

#### Estándares de implementación
- Estructura por dominios en `src/pages` y `src/components`.
- Componentes con props claras; formularios desacoplados.
- Reglas de negocio en componentes por ahora; migrables a servicios.
- Nomenclatura en español, variables descriptivas.
- UI con utilidades Tailwind; responsive-first.

#### Protocolos de seguridad aplicados
- Autenticación simulada en `src/services/authService.js`:
  - Usuarios fijos y usuarios creados en `localStorage`.
  - Roles/permisos: `hasPermission`, `hasRole`, `isAdmin`.
  - Flujo de primer ingreso con verificación simulada (código).
- Cliente API `src/services/api.js`:
  - Token Bearer desde `localStorage` (estandarizar nombre: `token` vs `authToken`).
  - Timeouts y manejo robusto de errores (`ApiError`).
- Rutas protegidas:
  - `src/utils/ProtectedRoute.jsx` (en App actual, gating con `useAuth`).

### Diagramas de flujo principales (ASCII)

- Autenticación y carga de App:
  ```
  App → useAuth.loading? → spinner
     → !isAuthenticated? → rutas Login/Recuperación
     → autenticado → layout Sidebar+Header → render sección por activeSection
  ```

- Pedidos (crear):
  ```
  Seleccionar tipo cliente → llenar formulario
  → seleccionar tipo doc (P/V/C) → agregar productos
  → Guardar según tipo:
     - Proforma: add lista (Pendiente)
     - Nota de Venta: aCuenta=total, saldo=0 (Completado)
     - Contrato: saldo=total-aCuenta; opcional fechas → (Pendiente)
  ```

- Agenda (CRUD):
  ```
  Nuevo → validar → guardar en estado + localStorage → render
  Editar → actualizar estado + persistencia
  Eliminar → confirmar → remover + persistencia
  ```

### Dependencias entre aplicaciones

- Dashboard: lee métricas de Pedidos, Producción, Inventario, Clientes, Contratos.
- Pedidos: crea Contratos y fechas (Agenda); Ventas deberían impactar Inventario (roadmap).
- Agenda: recibe eventos desde Pedidos/Contratos (roadmap).
- Activos: relación con Compras/Inventario para repuestos (no cableado aún).

### Reglas de negocio transversales

- Roles y permisos:
  - `admin`: acceso a configuración; permisos amplios.
  - `empleado`: permisos restringidos.
- Estados de pedido: Pendiente, En Proceso, Completado, Cancelado.
- Tipos de documento (P/V/C) dictan comportamiento financiero/operativo.
- Activos:
  - Financiado/Leasing modifica `tipoPago`.
  - Mantenimientos modifican `estado` y planifican próximos servicios.

### Recomendaciones de evolución

- Unificar token en `api.js` y `authService`.
- Externalizar reglas a servicios/hooks de dominio.
- Integrar backend real con `services/*` y `endpoints.*` ya definidos.
- Sincronizar Pedidos→Agenda e Inventario; producción con estados/tiempos.
- Añadir validaciones robustas (p. ej., Zod/React Hook Form).


