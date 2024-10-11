### **Presentación del Laboratorio: Creación de un Helm Chart para el despliegue de los servicios Ratings y MysqlDB en Kubernetes**

---

## Objetivos del laboratorio:
En este laboratorio aprenderás a:
- Crear un **Helm chart** para el despliegue de dos servicios: **Ratings** y **MysqlDB**.
- Utilizar las imágenes Docker de **Ratings** y **MysqlDB** provistas por **Istio**.
- Automatizar el despliegue y la gestión de aplicaciones en Kubernetes a través de **Helm**.

## Requisitos previos:
Antes de comenzar el laboratorio, asegúrate de cumplir con los siguientes requisitos:
1. Un clúster de **Kubernetes** en funcionamiento.
2. **Helm** instalado en tu entorno de trabajo.
3. Familiaridad con los conceptos básicos de Kubernetes y Helm.

## Instrucciones del laboratorio:

En este laboratorio se te proporciona un **Helm chart** parcialmente completo. El archivo `values.yaml` ya tiene configuradas las definiciones necesarias para el correcto despliegue de las aplicaciones **Ratings** y **MysqlDB**. Además, **los parámetros para el StatefulSet de MySQL DB, el servicio `mysqldb-svc`, y los datos contenidos en la ConfigMap y los Secrets ya están definidos en el archivo `values.yaml`**. Por lo tanto, todas las implementaciones que crearás deberán estar **parametrizadas**, de manera que los valores correspondientes sean leídos directamente desde el archivo `values.yaml`.

### Archivos faltantes que deberás crear:

1. **configmap.yaml**: utilizado para almacenar y manejar variables de configuración que serán compartidas entre los despliegues de las aplicaciones. Deberás crear este archivo de forma que las configuraciones se lean del archivo `values.yaml`.
  
2. **secret.yaml**: utilizado para almacenar credenciales sensibles, como contraseñas, claves de acceso y otras configuraciones confidenciales necesarias para las aplicaciones. Crea este archivo de forma que las credenciales se obtengan de los valores ya definidos en el archivo `values.yaml`.

3. **statefulset.yaml**: necesario para desplegar **MySQL DB** como un **StatefulSet** en Kubernetes. Este archivo deberá estar parametrizado para leer los valores de configuración y las propiedades del StatefulSet desde el archivo `values.yaml`.

4. **service-mysql.yaml**: define el servicio `mysqldb-svc`, que permitirá la comunicación con los pods donde se desplegará la aplicación **MySqlDB**. Este servicio debe configurarse para que los valores del puerto y otros detalles de la comunicación sean tomados directamente del archivo `values.yaml`.

### Tareas:

- **configmap.yaml**: Crea este archivo para manejar configuraciones de la aplicación. Asegúrate de que todas las variables de configuración necesarias estén parametrizadas y tomen los valores de `values.yaml`.

- **secret.yaml**: Crea este archivo para almacenar credenciales como el nombre de usuario y la contraseña para la base de datos MySQL. Los secretos deberán extraerse de los parámetros ya definidos en `values.yaml`.

- **statefulset.yaml**: Crea este archivo para desplegar la base de datos MySQL como un StatefulSet, garantizando persistencia en el almacenamiento y la estabilidad de los pods. Las propiedades del StatefulSet, como el número de réplicas y los volúmenes persistentes, deberán estar parametrizadas en función de los valores de `values.yaml`.

- **service-mysql.yaml**: Define el servicio para que los pods del deployment de MySQL puedan comunicarse de manera eficiente dentro del clúster Kubernetes. Asegúrate de que los puertos y otros detalles estén configurados para tomar los valores definidos en `values.yaml`.

## Estructura del laboratorio:
El laboratorio se divide en las siguientes fases:
1. **Completar el Chart Helm**:
   - Crear los archivos mencionados para completar el chart Helm y preparar el despliegue de **Ratings** y **MySQL DB**.
2. **Configuración de los servicios**:
   - Verificar las configuraciones en el archivo `values.yaml` para garantizar que ambas aplicaciones se desplieguen correctamente.
3. **Despliegue en el clúster Kubernetes**:
   - Ejecutar los comandos de instalación para desplegar ambos servicios usando Helm.
4. **Verificación del Despliegue**:
   - Verificar que ambos servicios se desplieguen correctamente utilizando `kubectl` y confirmar que los servicios están operativos.
5. **Pruebas de funcionalidad**:
   - Realizar pruebas para garantizar que tanto **Ratings** como **MysqlDB** están funcionando y se comunican adecuadamente.

## Comandos principales:
- Creación del chart Helm:
  \`\`\`bash
  helm create ratings-mysqldb
  \`\`\`
- Despliegue de los servicios:
  \`\`\`bash
  helm install my-release ./ratings-mysqldb
  \`\`\`
- Verificación del estado de los pods y servicios:
  \`\`\`bash
  kubectl get all
  \`\`\`

## Conclusión:
Al finalizar este laboratorio, serás capaz de crear, configurar y gestionar servicios distribuidos en Kubernetes utilizando **Helm**, y habrás completado el proceso para el despliegue de **Ratings** y **MysqlDB**, manejando tanto la configuración como los secretos de la aplicación, y desplegando la base de datos como un **StatefulSet**, todo de manera parametrizada según los valores definidos en `values.yaml`.
