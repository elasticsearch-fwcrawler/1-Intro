# 1-Intro

1. [Módulo 1: Introducción a Elasticsearch](#schema1)
2. [Instalar Elasticsearch](#schema2)
3. [Ejercicio 1: Configuración de Elasticsearch](#schema3)


<hr>

<a name="schema1"></a>

## 1- Módulo 1: Introducción a Elasticsearch
### Qué es Elasticsearch
- Elasticsearch es un motor de búsqueda y análisis de datos en tiempo real, capaz de indexar y realizar búsquedas en grandes volúmenes de datos distribuidos.
### Conceptos clave:
- Cluster: Un conjunto de nodos (servidores) que trabajan juntos.
- Node: Cada instancia de Elasticsearch que forma parte de un cluster.
- Index: Similar a una base de datos en RDBMS, contiene documentos.
- Document: La unidad básica de información en Elasticsearch, almacenado en JSON.
- Shard: Fragmento de un índice, permite escalar el índice a través de múltiples nodos.
- Replica: Copia de un shard, proporciona alta disponibilidad y rendimiento.


<hr>

<a name="schema2"></a>

## 2. Instalar Elasticsearch

- Descargar Elasticsearch
    - Descarga la versión de Elasticsearch compatible con macOS desde la página oficial de descargas:
        - Ve a la página de descargas de Elasticsearch.
        - Descarga el archivo .tar.gz o .zip.
- Extraer y configurar Elasticsearch
    - Abre Terminal y navega al directorio donde descargaste el archivo.
 
        ```bash
        cd ~/Downloads
        ```
    - Extrae el contenido del archivo descargado:

        ```bash
        tar -xzf elasticsearch-<version>.tar.gz
        ```
        O si descargaste el archivo .zip:

        ```bash
        unzip elasticsearch-<version>.zip
        ```
    - Esto creará un directorio llamado elasticsearch-<version>.

    - Mueve el directorio de Elasticsearch a una ubicación de tu elección (por ejemplo, /usr/local/):

        ```bash
        sudo mv elasticsearch-<version> /usr/local/elasticsearch
        ```
### Iniciar Elasticsearch
    
- Navega al directorio bin dentro del directorio de Elasticsearch:
    ```bash
    cd /usr/local/elasticsearch/bin
    ```
- Inicia Elasticsearch con el siguiente comando:

    ```bash
    ./elasticsearch
    ````

- Este comando iniciará Elasticsearch en segundo plano y lo pondrá disponible en http://localhost:9200/.
- Si deseas que Elasticsearch se ejecute en segundo plano (sin ocupar la terminal), puedes utilizar nohup:

    ```bash
    nohup ./elasticsearch &
    ```
### Verificar la instalación
- Una vez que Elasticsearch esté en funcionamiento, puedes verificar que todo esté correcto accediendo desde tu navegador a:

    ```bash
    http://localhost:9200/
    ````

- Deberías ver una respuesta en formato JSON con información sobre el clúster de Elasticsearch.

- Alternativamente, puedes usar curl desde la terminal para verificar:

    ```bash
    curl -X GET "localhost:9200/"
    ```
### Configurar Elasticsearch (opcional)
- Si deseas personalizar la configuración de Elasticsearch, puedes editar el archivo de configuración elasticsearch.yml ubicado en /usr/local/elasticsearch/config/. Aquí puedes ajustar parámetros como el nombre del clúster, configuraciones de red, seguridad, entre otros.

### Parar Elasticsearch
- Para detener Elasticsearch, puedes simplemente presionar Ctrl + C en la terminal donde se está ejecutando, o matar el proceso si se está ejecutando en segundo plano:

    ```bash
    ps aux | grep elasticsearch
    kill <PID>
    ```
- Donde <PID> es el ID del proceso de Elasticsearch.


<hr>

<a name="schema3"></a>

### 3. Ejercicio 1: Configuración de Elasticsearch

### Configuración básica:
- Inicia Elasticsearch y verifica que esté corriendo accediendo a http://localhost:9200/ desde tu navegador.
    - Navega al directorio bin dentro del directorio de Elasticsearch:
    ```bash
    cd /usr/local/elasticsearch
    ```
     -  Crear contraseña
    ```
    export ELASTIC_PASSWORD="your_password"
    ```
    - Inicia Elasticsearch con el siguiente comando:

    ```bash
    ./bin/elasticsearch
    ```
 
- Revisa el archivo de configuración `elasticsearch.yml` para entender los parámetros básicos, como el nombre del cluster y las configuraciones de red.
- Cambios añadidos a `elasticsearch.yml`
   ```yml
    # Network
        network.host: 0.0.0.0
        http.port: 9200

    # Security
        xpack.security.enabled: false
    ```
![localhost](./img/localhost.jpg)
