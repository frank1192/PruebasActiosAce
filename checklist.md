# ✅ Checklist de Validaciones - GitHub Actions Workflow

> **Guía rápida de referencia para desarrolladores**  
> Este documento proporciona un checklist profesional de todas las validaciones que se ejecutan automáticamente en Pull Requests para garantizar el cumplimiento de estándares ESB/ACE.

---

## 📋 Tabla de Contenidos

- [Introducción](#-introducción)
- [Checklist de Validaciones](#-checklist-de-validaciones)
- [Guía de Resolución Rápida](#-guía-de-resolución-rápida)
- [Buenas Prácticas](#-buenas-prácticas)
- [Recursos Adicionales](#-recursos-adicionales)

---

## 🎯 Introducción

Este checklist documenta todas las validaciones automáticas implementadas en el workflow `checklist.yml`. Utilízalo como guía para preparar tu Pull Request y asegurar que pase todas las verificaciones en el primer intento.

**Estado de las validaciones**: Las validaciones se ejecutan automáticamente en cada PR hacia las ramas:
- ✅ `main`
- ✅ `develop`
- ✅ `quality`
- ✅ `feature/**`

---

## ✅ Checklist de Validaciones

### 1️⃣ Validación de Nombre de Rama

- [ ] La rama comienza con uno de los prefijos válidos: `feature/`, `bugfix/`, `hotfix/`, `release/`
- [ ] El nombre después del prefijo contiene solo caracteres alfanuméricos, puntos, guiones bajos o guiones
- [ ] El nombre no está vacío después del prefijo

**Ejemplo válido**: `feature/nueva-funcionalidad` ✅  
**Ejemplo inválido**: `nueva-funcionalidad` ❌ (falta prefijo)

---

### 2️⃣ Validación de Existencia del README.md

- [ ] Existe el archivo `README.md` en la raíz del repositorio
- [ ] El archivo está correctamente nombrado (case-sensitive)

---

### 3️⃣ Validación de Estructura del README.md

#### 3.1 Título Principal

- [ ] Comienza con `# ESB_`
- [ ] Contiene texto descriptivo después de `ESB_` (no solo guiones o guiones bajos)
- [ ] Termina con un punto (.)

**Formato esperado**: `# ESB_ACE12_NombreServicio.`

---

#### 3.2 Sección INFORMACIÓN DEL SERVICIO

- [ ] Existe el encabezado `## INFORMACIÓN DEL SERVICIO`
- [ ] Contiene descripción del servicio **antes** de la subsección `### Último despliege`
- [ ] La descripción no está vacía

---

#### 3.3 Subsección Último Despliege

- [ ] Existe la subsección `### Último despliege`
- [ ] Contiene tabla con encabezado: `|CQ |JIRA | Fecha|`
- [ ] La tabla tiene al menos una fila de datos después del separador
- [ ] Todas las celdas tienen valores (puede ser 'NA' si no aplica)
- [ ] No hay celdas vacías

**Formato esperado**:
```markdown
### Último despliege

|CQ |JIRA | Fecha|
|---|---|---|
| NA | NA |6/10/2023 (WS) |
```

---

#### 3.4 Sección Procedimiento de Despliegue

- [ ] Existe el encabezado `## Procedimiento de despliegue`
- [ ] Contiene instrucciones de despliegue (no está vacía)
- [ ] Incluye la frase "desplegar en los grupos de ejecución:" seguida de los grupos

---

#### 3.5 Sección ACCESO AL SERVICIO

##### DataPower (Interno/Externo)

- [ ] Existe al menos una subsección: `### DataPower Interno :` o `### DataPower Externo :`
- [ ] Si existe una subsección, puede estar:
  - Vacía (se permite ✅)
  - Con "NA", "N/A" o "No Aplica" ✅
  - Con una tabla de endpoints ✅

**⚠️ IMPORTANTE**: Las subsecciones DataPower **pueden estar vacías** sin causar error. Solo se muestra un mensaje informativo.

- [ ] Si contiene tabla, tiene al menos una fila de datos (no solo encabezado y separador)
- [ ] **CRÍTICO**: Las URLs de DataPower comienzan con `https://boc201` (NO `boc200`)
- [ ] Los endpoints cumplen con el formato específico por ambiente:

| Ambiente | DataPower Interno | DataPower Externo |
|----------|-------------------|-------------------|
| DESARROLLO | `https://boc201.des.app.bancodeoccidente.net` | N/A |
| CALIDAD | `https://boc201.testint.app.bancodeoccidente.net` | `https://boc201.testdmz.app.bancodeoccidente.net` |
| PRODUCCION | `https://boc201.prdint.app.bancodeoccidente.net` | `https://boc201.prddmz.app.bancodeoccidente.net` |

- [ ] Si hay tabla, existen filas para los 3 ambientes: DESARROLLO, CALIDAD, PRODUCCION
- [ ] El nombre del DataPower comienza con `BODP` y termina con `DEV`, `QAS` o `PRD` según el ambiente

---

##### Endpoint BUS

- [ ] Existe la subsección `### Endpoint BUS`
- [ ] Contiene tabla con endpoints para los 3 ambientes
- [ ] **No contiene valores NA** (a diferencia de DataPower)
- [ ] Los endpoints cumplen con los formatos esperados:

| Ambiente | Formato URL |
|----------|-------------|
| DESARROLLO | `https://adbog162e.bancodeoccidente.net:XXXX/...` |
| CALIDAD | `https://a[dt]bog16[34][de].bancodeoccidente.net:XXXX/...` |
| PRODUCCION | `https://adbog16[56][ab].bancodeoccidente.net:XXXX/...` o `https://boc060ap.prd.app.bancodeoccidente.net:XXXX/...` |

---

#### 3.6 Sección CANALES - APLICACIONES

- [ ] Existe el encabezado `## CANALES - APLICACIONES`
- [ ] Contiene una fila `**Consumidor**` con valores (puede ser 'NA')
- [ ] Contiene una fila `**Backends**` con valores (puede ser 'NA')
- [ ] Las filas no están vacías

---

#### 3.7 Sección DEPENDENCIAS

##### Tabla Servicios

- [ ] Contiene la tabla `|Servicios|`
- [ ] Los servicios listados coinciden con los proyectos en el archivo `.project`
- [ ] No hay servicios en `.project` que falten en README
- [ ] No hay servicios en README que no existan en `.project`

##### Tabla XSL

- [ ] Contiene la tabla `|XSL|`
- [ ] Si no hay XSLs, se indica explícitamente con 'NA'
- [ ] La tabla no está vacía

---

#### 3.8 Sección DOCUMENTACION

- [ ] Existe el encabezado `## DOCUMENTACION`
- [ ] Contiene campo `**Documento de diseño detallado:**` con enlace a SharePoint
  - Enlace comienza con: `https://bancoccidente.sharepoint.com/:f:/r/sites/BibliotecaAplicaciones/`
- [ ] Contiene campo `**Mapeo:**` con enlace a SharePoint
  - Enlace comienza con: `https://bancoccidente.sharepoint.com/:f:/r/sites/BibliotecaAplicaciones/`
- [ ] Contiene campo `**Evidencias (Unitarias/Auditoria/Monitoreo):**` con enlace a SharePoint
  - Enlace comienza con: `https://bancoccidente.sharepoint.com/:f:/r/sites/BibliotecaAplicaciones/`
- [ ] Contiene campo `**WSDL:**`
  - Con ruta: `git\{NOMBRE_REPO}\Broker\WSDL\wsdl\{archivo}.wsdl`
  - O con valor 'N/A' si no aplica

---

#### 3.9 Sección SQL

- [ ] Existe el encabezado `## SQL`
- [ ] Contiene queries SQL para auditoría y monitoreo
- [ ] La sección no está vacía
- [ ] **Los códigos de operación son solo números** (sin letras)
- [ ] **No hay códigos de operación vacíos** (`num_id_tipo_operacion = ''`)

**Validaciones específicas**:
- [ ] En formato `where ... = '123'`: el valor contiene solo dígitos
- [ ] En formato `where ... in('123','456')`: todos los valores contienen solo dígitos
- [ ] No hay códigos de operación vacíos

---

### 4️⃣ Validación de Carpetas BD

- [ ] No existe ninguna carpeta llamada "BD" (case-insensitive) en el repositorio
- [ ] Se han excluido carpetas con información sensible de base de datos

---

### 5️⃣ Validación de Grupos de Ejecución

- [ ] El nombre del servicio está en el título del README
- [ ] La sección "Procedimiento de despliegue" contiene la frase "desplegar en los grupos de ejecución:"
- [ ] Los grupos listados coinciden exactamente con los del archivo de configuración central
- [ ] No hay grupos en README que no estén en la configuración
- [ ] No hay grupos en configuración que no estén en README

**Nota**: Requiere el secret `ESB_ACE12_ORG_REPO_TOKEN` para acceder al repositorio de configuración.

---

### 6️⃣ Validación de Rutas y Revisores

#### Ruta develop → quality

- [ ] Tiene al menos un revisor autorizado de la lista: `DRamirezM`, `cdgomez`, `acardenasm`, `CAARIZA`

#### Ruta quality → main

- [ ] Tiene al menos un revisor autorizado de la lista: `DRamirezM`, `cdgomez`, `acardenasm`, `CAARIZA`

#### Ruta feature/** → develop

- [ ] Tiene revisor autorizado, O
- [ ] Existe comentario `@bot aprobar excepción` para emergencias

---

## 🔧 Guía de Resolución Rápida

### Error: "Título no puede ser solo ESB_"
**Solución**: Agregar un nombre descriptivo después de ESB_
```markdown
# ESB_ACE12_MiServicio.
```

### Notice: "DataPower está vacía"
**Comportamiento**: Las subsecciones de DataPower vacías son **permitidas** y solo generan un mensaje informativo.  
**Opciones válidas**:
- Dejar la subsección vacía ✅
- Agregar "NA", "N/A" o "No Aplica" ✅
- Agregar una tabla con endpoints ✅

### Warning: "No se encontró acceso a DataPower"
**Solución**: Agregar las subsecciones DataPower Interno/Externo con tablas o "NA"

### Error: "Endpoint debe comenzar con https://boc201"
**Solución**: Verificar que todas las URLs de DataPower comiencen con `boc201` y no `boc200`

### Error: "Grupos de ejecución no coinciden"
**Solución**: Verificar que los grupos listados en el README coincidan exactamente con los del archivo de configuración central

### Error: "Código de operación está vacío"
**Solución**: Reemplazar `num_id_tipo_operacion = ''` con un código válido solo numérico

### Error: "Código de operación contiene letras"
**Solución**: Usar solo números en los códigos de operación: `'123'` en lugar de `'99a9042'`

---

## 💡 Buenas Prácticas

1. **Mantén el README actualizado**: El README es la fuente de verdad para la configuración del servicio.

2. **Usa valores NA apropiadamente**: Si algo no aplica, indica explícitamente 'NA' en lugar de dejar vacío.

3. **Verifica URLs antes de commit**: Asegúrate de que las URLs de DataPower usen `boc201` y no `boc200`.

4. **Sincroniza dependencias**: Mantén la tabla de Servicios en README sincronizada con el archivo `.project`.

5. **Códigos de operación limpios**: Usa solo números en los códigos de operación SQL.

6. **Nombra ramas correctamente**: Usa los prefijos estándar (`feature/`, `bugfix/`, etc.) para evitar errores.

7. **DataPower vacío es válido**: No te preocupes si las subsecciones de DataPower están vacías durante el desarrollo - esto es válido y solo genera un aviso informativo.

---

## 📚 Recursos Adicionales

- **Documentación completa del workflow**: Ver `CHECKLIST.md` (mayúsculas) para detalles técnicos completos
- **Archivo del workflow**: `.github/workflows/checklist.yml`
- **Plantilla de README**: Disponible en el repositorio central de configuración
- **Repositorio de configuración**: `bocc-principal/ESB_ACE12_General_Configs`

---

## 🔄 Historial de Versiones

### Versión 1.0 (2025-10-23)
- ✅ Documentación inicial del checklist profesional
- ✅ Integración con todas las validaciones del workflow
- ✅ Guía de resolución rápida para errores comunes
- ✅ Confirmación de que subsecciones DataPower vacías son válidas

---

## 📞 Soporte

Si tienes dudas sobre alguna validación o necesitas ayuda:

1. Revisa este checklist y la documentación completa en `CHECKLIST.md`
2. Verifica los mensajes de error en el PR - cada uno incluye información específica sobre cómo resolverlo
3. Consulta con los revisores autorizados: `DRamirezM`, `cdgomez`, `acardenasm`, `CAARIZA`

---

**Última actualización**: 2025-10-23  
**Mantenido por**: Equipo de Integración ESB/ACE
