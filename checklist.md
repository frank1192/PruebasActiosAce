# Checklist de Cierre de Documentación - ESB/ACE12

Este checklist profesional guía el proceso completo de documentación y validación para proyectos ESB/ACE12, asegurando que todos los estándares y requisitos sean cumplidos antes del despliegue.

## 📋 Información del Proyecto

- **Proyecto**: UtilizacionCreditoRotativoPlus
- **Fecha de inicio**: _____________________
- **Fecha de cierre**: _____________________
- **Responsable**: _____________________
- **Revisor técnico**: _____________________

---

## ✅ 1. Validación de Estructura del Repositorio

### 1.1 Estructura de Carpetas
- [ ] Carpeta `Broker` existe y contiene los archivos del proyecto
- [ ] Carpeta `WSDL` existe con los archivos de definición de servicios
- [ ] No existen carpetas `BD` (información sensible) en el repositorio
- [ ] Estructura de carpetas sigue el estándar definido por el equipo

### 1.2 Archivos de Configuración
- [ ] Archivo `.project` existe y está correctamente configurado
- [ ] Archivo `.gitignore` está configurado para excluir archivos sensibles
- [ ] Archivos de propiedades (.properties) están versionados correctamente
- [ ] Archivos BAR están documentados en el procedimiento de despliegue

---

## ✅ 2. Documentación del README.md

### 2.1 Estructura General
- [ ] Título principal sigue el formato: `# ESB_ACE12_NombreServicio.`
- [ ] El título no es solo `# ESB_` o contiene solo guiones/guiones bajos
- [ ] Todas las secciones obligatorias están presentes en el orden correcto

### 2.2 Sección: INFORMACIÓN DEL SERVICIO
- [ ] Encabezado `## INFORMACIÓN DEL SERVICIO` presente
- [ ] Contiene descripción detallada del servicio ANTES de subsecciones
- [ ] Describe claramente la funcionalidad del servicio
- [ ] Menciona los sistemas con los que interactúa

#### 2.2.1 Subsección: Último Despliegue
- [ ] Encabezado `### Último despliege` presente
- [ ] Tabla con columnas: `|CQ |JIRA | Fecha|`
- [ ] Al menos una fila de datos completada
- [ ] Todas las celdas tienen valores (usar 'NA' si no aplica)
- [ ] Fecha en formato legible (ej: `6/10/2023 (WS)`)

### 2.3 Sección: Procedimiento de Despliegue
- [ ] Encabezado `## Procedimiento de despliegue` presente
- [ ] Contiene instrucciones claras de despliegue
- [ ] Menciona el archivo .properties a aplicar
- [ ] Menciona el archivo .bar a desplegar
- [ ] Lista los grupos de ejecución correctos
- [ ] Los grupos coinciden con el archivo central de configuración

### 2.4 Sección: ACCESO AL SERVICIO

#### 2.4.1 DataPower Externo
- [ ] Subsección `### DataPower Externo :` presente (si aplica)
- [ ] Si no aplica: contiene 'NA', 'N/A', 'No Aplica', o está vacía
- [ ] Si aplica: tabla con columnas correctas
- [ ] Tabla contiene filas para: DESARROLLO, CALIDAD, PRODUCCION
- [ ] URLs comienzan con `https://boc201` (NO `boc200`)
- [ ] Endpoints DESARROLLO: `https://boc201.des.app.bancodeoccidente.net`
- [ ] Endpoints CALIDAD: `https://boc201.testdmz.app.bancodeoccidente.net`
- [ ] Endpoints PRODUCCION: `https://boc201.prddmz.app.bancodeoccidente.net`
- [ ] DataPower nombres: `BODP*DEV`, `BODP*QAS`, `BODP*PRD`

#### 2.4.2 DataPower Interno
- [ ] Subsección `### DataPower Interno :` presente (si aplica)
- [ ] Si no aplica: contiene 'NA', 'N/A', 'No Aplica', o está vacía
- [ ] Si aplica: tabla con columnas correctas
- [ ] Tabla contiene filas para: DESARROLLO, CALIDAD, PRODUCCION
- [ ] URLs comienzan con `https://boc201` (NO `boc200`)
- [ ] Endpoints DESARROLLO: `https://boc201.des.app.bancodeoccidente.net`
- [ ] Endpoints CALIDAD: `https://boc201.testint.app.bancodeoccidente.net`
- [ ] Endpoints PRODUCCION: `https://boc201.prdint.app.bancodeoccidente.net`
- [ ] DataPower nombres: `BODP*DEV`, `BODP*QAS`, `BODP*PRD`

#### 2.4.3 Endpoint BUS
- [ ] Subsección `### Endpoint BUS` presente
- [ ] Tabla contiene endpoints para los 3 ambientes
- [ ] NO contiene valores 'NA' (endpoints son obligatorios)
- [ ] Endpoints DESARROLLO: `https://adbog162e.bancodeoccidente.net:XXXX`
- [ ] Endpoints CALIDAD: válidos para nodos de calidad
- [ ] Endpoints PRODUCCION: válidos para nodos de producción

### 2.5 Sección: CANALES - APLICACIONES
- [ ] Encabezado `## CANALES - APLICACIONES` presente
- [ ] Contiene fila `**Consumidor**` con valores
- [ ] Contiene fila `**Backends**` con valores
- [ ] Valores pueden ser 'NA' si no aplica, pero no vacíos
- [ ] Lista todos los canales consumidores del servicio
- [ ] Lista todos los backends con los que interactúa

### 2.6 Sección: DEPENDENCIAS

#### 2.6.1 Tabla de Servicios
- [ ] Encabezado de tabla `|Servicios|` presente
- [ ] Lista todos los proyectos/librerías que son dependencias
- [ ] Los servicios listados coinciden con el archivo `.project`
- [ ] No hay servicios en `.project` que falten en README
- [ ] No hay servicios en README que no existan en `.project`

#### 2.6.2 Tabla de XSL
- [ ] Encabezado de tabla `|XSL|` presente
- [ ] Si hay XSLs: todos están listados
- [ ] Si no hay XSLs: contiene 'NA'
- [ ] Lista completa de archivos .xsl utilizados

### 2.7 Sección: DOCUMENTACION
- [ ] Encabezado `## DOCUMENTACION` presente

#### 2.7.1 Documento de Diseño Detallado
- [ ] Campo `**Documento de diseño detallado:**` presente
- [ ] Enlace SharePoint válido comienza con:
  `https://bancoccidente.sharepoint.com/:f:/r/sites/BibliotecaAplicaciones/`
- [ ] Enlace es accesible y apunta a la carpeta correcta

#### 2.7.2 Mapeo
- [ ] Campo `**Mapeo:**` presente
- [ ] Enlace SharePoint válido comienza con:
  `https://bancoccidente.sharepoint.com/:f:/r/sites/BibliotecaAplicaciones/`
- [ ] Enlace es accesible y apunta a la carpeta correcta

#### 2.7.3 Evidencias
- [ ] Campo `**Evidencias (Unitarias/Auditoria/Monitoreo):**` presente
- [ ] Enlace SharePoint válido comienza con:
  `https://bancoccidente.sharepoint.com/:f:/r/sites/BibliotecaAplicaciones/`
- [ ] Enlace es accesible y apunta a la carpeta correcta
- [ ] Carpeta contiene evidencias de pruebas unitarias
- [ ] Carpeta contiene evidencias de auditoría
- [ ] Carpeta contiene evidencias de monitoreo

#### 2.7.4 WSDL
- [ ] Campo `**WSDL:**` presente
- [ ] Si aplica: ruta sigue formato `git\{NOMBRE_REPO}\Broker\WSDL\wsdl\{archivo}.wsdl`
- [ ] Nombre del repositorio en la ruta coincide con el título
- [ ] Si no aplica: contiene 'NA' o 'N/A'
- [ ] Archivo WSDL existe en la ruta especificada

### 2.8 Sección: SQL
- [ ] Encabezado `## SQL` presente
- [ ] Contiene queries de auditoría y monitoreo
- [ ] NO contiene códigos de operación vacíos (`= ''`)
- [ ] Códigos de operación contienen SOLO números (sin letras)
- [ ] Queries están comentadas para facilitar uso
- [ ] Incluye filtros por cola del servicio
- [ ] Incluye filtros por P3 (si aplica)
- [ ] Incluye filtros por código de operación

---

## ✅ 3. Validaciones Automatizadas

### 3.1 Workflow de GitHub Actions
- [ ] Workflow `checklist.yml` se ejecuta correctamente
- [ ] Validación de nombre de rama PASA
- [ ] Validación de existencia README.md PASA
- [ ] Validación de plantilla README PASA
- [ ] Validación de carpetas BD PASA
- [ ] Validación de grupos de ejecución PASA
- [ ] Validación de rutas y revisores PASA
- [ ] NO hay errores que causen exit code 1

### 3.2 Validaciones Específicas
- [ ] DataPower vacío no causa error (solo notice)
- [ ] URLs con boc201 pasan validación
- [ ] Ambientes DESARROLLO, CALIDAD, PRODUCCION presentes
- [ ] Formato de tablas es correcto
- [ ] Códigos SQL son válidos

---

## ✅ 4. Gestión de Ramas y Pull Requests

### 4.1 Estructura de Ramas
- [ ] Rama sigue nomenclatura: `feature/`, `bugfix/`, `hotfix/`, o `release/`
- [ ] Nombre de rama es descriptivo
- [ ] Rama parte del branch correcto (develop, quality, main)

### 4.2 Pull Request
- [ ] PR tiene título descriptivo
- [ ] PR tiene descripción clara de los cambios
- [ ] PR está asignado a revisor(es) apropiado(s)
- [ ] PR incluye etiquetas (labels) relevantes
- [ ] Todos los checks de GitHub Actions PASAN
- [ ] No hay conflictos de merge

### 4.3 Revisiones
- [ ] Para develop → quality: revisor autorizado asignado
- [ ] Para quality → main: revisor autorizado asignado
- [ ] Revisores autorizados: DRamirezM, cdgomez, acardenasm, CAARIZA
- [ ] Comentarios de revisión han sido atendidos
- [ ] Aprobación final recibida

---

## ✅ 5. Pruebas y Calidad

### 5.1 Pruebas Unitarias
- [ ] Pruebas unitarias ejecutadas y documentadas
- [ ] Cobertura de código es aceptable
- [ ] Resultados subidos a SharePoint (Evidencias)

### 5.2 Pruebas de Integración
- [ ] Pruebas de integración en DESARROLLO completadas
- [ ] Pruebas de integración en CALIDAD completadas
- [ ] Resultados documentados en evidencias

### 5.3 Auditoría
- [ ] Logs de auditoría configurados correctamente
- [ ] Queries SQL de auditoría probadas
- [ ] Monitoreo configurado en ambientes

---

## ✅ 6. Despliegue

### 6.1 Preparación
- [ ] Archivo .properties actualizado para cada ambiente
- [ ] Archivo .bar generado correctamente
- [ ] Grupos de ejecución identificados y validados
- [ ] Plan de rollback definido

### 6.2 Despliegue en Ambientes
- [ ] Despliegue en DESARROLLO exitoso
- [ ] Validación funcional en DESARROLLO PASA
- [ ] Despliegue en CALIDAD exitoso
- [ ] Validación funcional en CALIDAD PASA
- [ ] Despliegue en PRODUCCION exitoso (si aplica)
- [ ] Validación funcional en PRODUCCION PASA (si aplica)

### 6.3 Post-Despliegue
- [ ] README actualizado con fecha de último despliegue
- [ ] Monitoreo activo y funcionando
- [ ] Alertas configuradas
- [ ] Documentación de despliegue en SharePoint

---

## ✅ 7. Seguridad

### 7.1 Información Sensible
- [ ] No hay credenciales en el código
- [ ] No hay tokens o secrets hardcodeados
- [ ] No hay carpetas BD con información sensible
- [ ] Archivos de configuración usan variables de entorno

### 7.2 Validaciones de Seguridad
- [ ] CodeQL u otra herramienta de seguridad ejecutada
- [ ] No hay vulnerabilidades críticas
- [ ] Dependencias actualizadas a versiones seguras
- [ ] Accesos y permisos correctamente configurados

---

## ✅ 8. Cierre y Aprobación Final

### 8.1 Documentación Completa
- [ ] README.md 100% completo y validado
- [ ] CHECKLIST.md actualizado con últimos cambios
- [ ] Este checklist.md completado
- [ ] Enlaces a SharePoint funcionando
- [ ] WSDL versionado correctamente

### 8.2 Aprobaciones
- [ ] Aprobación técnica recibida
- [ ] Aprobación de arquitectura (si aplica)
- [ ] Aprobación de seguridad (si aplica)
- [ ] Aprobación final de líder técnico

### 8.3 Comunicación
- [ ] Equipo notificado del despliegue
- [ ] Documentación compartida con stakeholders
- [ ] Capacitación realizada (si aplica)
- [ ] Canal de soporte definido

---

## 📝 Notas y Comentarios

**Cambios importantes realizados:**
- Corrección del bug de exit code 1 en validación de DataPower
- Actualización de CHECKLIST.md con historial de cambios
- Creación de este checklist profesional

**Observaciones durante la validación:**
```
_____________________________________________________________________
_____________________________________________________________________
_____________________________________________________________________
```

**Lecciones aprendidas:**
```
_____________________________________________________________________
_____________________________________________________________________
_____________________________________________________________________
```

---

## ✍️ Firmas

| Rol | Nombre | Fecha | Firma |
|-----|--------|-------|-------|
| Desarrollador | _____________ | ____/____/____ | _____________ |
| Revisor Técnico | _____________ | ____/____/____ | _____________ |
| Líder Técnico | _____________ | ____/____/____ | _____________ |
| Arquitecto (si aplica) | _____________ | ____/____/____ | _____________ |

---

## 📚 Referencias

- [CHECKLIST.md - Documentación Detallada](./CHECKLIST.md)
- [README.md - Plantilla](./README.md)
- [Workflow checklist.yml](./.github/workflows/checklist.yml)
- [Repositorio de Configuración Central](https://github.com/bocc-principal/ESB_ACE12_General_Configs)

---

**Versión**: 1.0  
**Última actualización**: 2025-10-23  
**Mantenido por**: Equipo ESB/ACE12
