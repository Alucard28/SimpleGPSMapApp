#Informe de vulnerabilidades

## Resumen

- Total de vulnerabilidades encontradas: 5
- Críticas: 0
- Altas: 3
- Medio: 2
- Bajo: 0

## Hallazgos Detallados

### 1. Application signed with debug certificate

- *Descripción : Aplicación firmada con un certificado de depuración. La aplicación de producción no debe enviarse con un certificado de depuración.
 
- * Gravedad : Alta.

- * Impacto : Puede comprometer su seguridad, limitar su distribución y afectar a su funcionalidad global.

- * Pasos para reproducirlo : Utilizando certificados de producción, implementando auditorías de seguridad y pruebas de penetración.

- * Remediación : Reemplazar el Certificado de Depuración, Eliminar Funciones de Depuración, Realizar Pruebas de Seguridad e Implementar Gestión de Parches.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 2. App can be installed on a vulnerable upatched Android version. Android 7.0, [minSdk=24]

- *Descripción : Esta aplicación se puede instalar en una versión anterior de Android que tiene múltiples vulnerabilidades no corregidas. 
Estos dispositivos no recibirán actualizaciones de seguridad razonables de Google. Soporta una versión de Android => 10, API 29 para recibir actualizaciones de seguridad razonables.
 
- * Gravedad : Alta.

- * Impacto : Exposición a Vulnerabilidades Conocidas, Acceso No Autorizado a Datos, Riesgo de Malware y Consecuencias Legales y Financieras.

- * Pasos para reproducir la vulnerabilidad : Utilizando certificados de producción, implementando auditorías de seguridad, pruebas de penetración, 
Desactivar Funciones de Depuración en Producción, Actualizar Regularmente Dependencias y Bibliotecas y Implementar Políticas de Seguridad.

- * Remediación : Actualizar el "minSdkVersion" y aumentando la versión mínima del SDK

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 3. Debug Enabled For App [android:debuggable=true]

- *Descripción : La depuración se habilitó en la aplicación que hace que sea más fácil para los ingenieros inversos para enganchar
un depurador a ella. Esto permite el volcado de una pila de seguimiento y el acceso a la depuración de ayuda de depuración.

- * Gravedad : Alta.

- * Impacto : Acceso No Autorizado a Funciones Sensibles, Explotación de Funciones de Prueba, Modificación del Comportamiento de la Aplicación, 
Recopilación de Información Sensible y Aumenta del Riesgo de Ataques.

- * Pasos para reproducir la vulnerabilidad : Descompilar el APK, Modificar el "AndroidManifest.xml", Recompilar y Firmar el APK, Instalar el APK Modificado, 
Configurar el Dispositivo para Depuración, Conectar el Depurador, Iniciar la Depuración, Manipular Variables y Comportamiento y Ejecutar y Observar Cambios.

- * Remediación : Configurar "android:debuggable=false", Revisar Configuraciones de Compilación, Eliminar Funciones de Depuración, Auditoría de Seguridad, 
Capacitación del Equipo de Desarrollo, Verificación Post-Lanzamiento y Uso de Herramientas de Análisis Estático.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 ### 4. Application Data can be Backed up [android:allowBackup=true]

- *Descripción : Esta bandera permite a cualquier persona hacer una copia de seguridad de los datos de su aplicación a través de adb. 
Permite a los usuarios que han habilitado la depuración USB copiar los datos de la aplicación fuera del dispositivo.

- * Gravedad : Media.

- * Impacto : Exposición de Datos Sensibles,Riesgo de Acceso Malicioso, Inconsistencias en el Estado de la Aplicación, 
Fugas de Información a Través de Copias de Seguridad, Dificultades para Manejar Datos Críticos.

- * Pasos para reproducir la vulnerabilidad : Descompilar el APK, Modificar el "AndroidManifest.xml", Recompilar y Firmar el APK, 
Instalar el APK Modificado, Realizar una Copia de Seguridad de la Aplicación, Extraer Datos del Archivo de Copia de Seguridad, 
Examinar los Datos Respaldados y Analizar la Información Sensible.

- * Remediación : Deshabilitar las Copias de Seguridad, Implementar Estrategias Alternativas, Auditar Datos Sensibles y Capacitar al Equipo sobre Seguridad.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 ### 5. Broadcast Receiver (androidx.profileinstaller.ProfileInstallReceiver) is Protected by a permission, but the protection level of the permission should be checked. 
Permission: android.permission.DUMP [android:exported=true]

- *Descripción : Se ha descubierto que un receptor de difusión se comparte con otras aplicaciones del dispositivo, por lo que es accesible para cualquier otra aplicación del dispositivo. 
Está protegido por un permiso que no está definido en la aplicación analizada. Por lo tanto, se debe comprobar el nivel de protección del permiso donde está definido. 
Si está definido como normal o peligroso, una aplicación maliciosa puede solicitar y obtener el permiso e interactuar con el componente. Si está definido como firma, 
sólo las aplicaciones firmadas con el mismo certificado pueden obtener el permiso.

- * Gravedad : Media.

- * Impacto : Acceso No Autorizado a Información Sensible, Explotación de Funciones del Sistema, Riesgo de Escalación de Privilegios, Confusión en la Gestión de Permisos y la Posibilidad de Ataques Coordinados.

- * Pasos para reproducir la vulnerabilidad : Verificar el Broadcast Receiver, Enviar una Intención Maliciosa, Observar el Comportamiento de la Aplicación y Capturar Resultados y Análisis.

- * Remediación : Revisar la Configuración del Receptor, Evaluar la Necesidad del Permiso DUMP, Auditoría Regular de Permisos y capacitar sobre Seguridad.
