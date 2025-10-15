## Guía de Inserción en Obsidian

Esta guía explica cómo importar y visualizar la documentación del proyecto en Obsidian con enlaces internos y navegación optimizada.

### 1) Requisitos
- Instalar Obsidian (`https://obsidian.md`).
- Tener la carpeta del repositorio disponible localmente.

### 2) Crear/usar un Vault
1. Abrir Obsidian.
2. Seleccionar "Open folder as vault".
3. Elegir la carpeta raíz del proyecto (donde está `README.md`).

> Alternativa: crear un Vault nuevo y luego añadir como subcarpeta la ruta `docs/` del proyecto.

### 3) Estructura recomendada
- Utilizar la carpeta `docs/` como espacio principal de notas.
- Archivos clave:
  - `docs/DOCUMENTACION_TECNICA.md`: documentación técnica completa.
  - `docs/Admin-Guia-Obsidian.md`: guía compacta para administradores (vista Obsidian).
  - `docs/Obsidian-Setup.md`: esta guía.

### 4) Enlaces y navegación
- La guía de administración incluye enlaces internos al estilo Obsidian:
  - Desde `docs/Admin-Guia-Obsidian.md`, navegar por módulos (Dashboard, Agenda, Pedidos, Clientes, Activos).
- Recomendado: activar el panel "Backlinks" y el gráfico para visualizar relaciones.

### 5) Buenas prácticas en Obsidian
- Renombrar notas manteniendo enlaces internos (Obsidian actualiza referencias).
- Usar encabezados `###` para secciones y mantener títulos consistentes.
- Crear notas adicionales para políticas internas, procedimientos y FAQs, enlazándolas desde la guía admin.

### 6) Snippets útiles
- Añadir un índice al inicio de cada nota larga con enlaces a encabezados:
  ```
  - [[#Sección 1]]
  - [[#Sección 2]]
  - [[#Sección 3]]
  ```
- Referenciar la documentación técnica desde la guía admin:
  ```
  Ver también: [[DOCUMENTACION_TECNICA]]
  ```

### 7) Exportación/compartición
- Para compartir con otros, versionar los `.md` en Git y pedirles abrir la misma carpeta como Vault.
- Opcional: usar "Publish" de Obsidian (servicio de pago) o exportar a PDF desde Obsidian/impresora del navegador.

### 8) Solución de problemas
- Si los enlaces internos no funcionan, verificar que el Vault apunta a la carpeta correcta y que los títulos/encabezados coinciden.
- Si no se ven las notas, confirmar que `docs/` está dentro del Vault.


