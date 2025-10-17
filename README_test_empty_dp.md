# ESB_ACE12_TestService.

## INFORMACIÓN DEL SERVICIO

Test service description

### Último despliege

|CQ |JIRA | Fecha|
|---|---|---|
| NA | NA |6/10/2023 (WS) | 

## Procedimiento de despliegue

Test deployment

## ACCESO AL SERVICIO

### DataPower Externo :

### DataPower Interno :
NA

### Endpoint BUS

|AMBIENTE|    NODO/GE    |ENDPOINT|
|---|----------|---|
|DESARROLLO|BOGESERVICIOSWS05_SRV01|https://adbog162e.bancodeoccidente.net:4907/test|
|CALIDAD|N1-BOGESERVICIOSWS05_SRV01|https://atbog163d.bancodeoccidente.net:4907/test|
|PRODUCCION|BOGESERVICIOSWS05_SRV01|https://boc060ap.prd.app.bancodeoccidente.net:4907/test|

## CANALES - APLICACIONES

||||
|---|---|---|
|**Consumidor**|CANALES|PB|
 
||||
|---|---|---|
|**Backends**|NA||

## DEPENDENCIAS

|Servicios|
|---|
|TestService|

|XSL|
|---|
|NA|

## DOCUMENTACION

**Documento de diseño detallado:** <br>
https://bancoccidente.sharepoint.com/:f:/r/sites/BibliotecaAplicaciones/test

**Mapeo:** <br>
https://bancoccidente.sharepoint.com/:f:/r/sites/BibliotecaAplicaciones/test

**Evidencias (Unitarias/Auditoria/Monitoreo):**      <br>
https://bancoccidente.sharepoint.com/:f:/r/sites/BibliotecaAplicaciones/test

**WSDL:** <br>
NA

## SQL
Filtrar por cola del servicio
```
select * from admesb.ESB_LOG_AUDITORIA where 1 = 1
```
