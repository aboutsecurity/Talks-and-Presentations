<h1> Modelado Práctico de Amenazas y Defensas BlueTeam con MITRE ATT&CK </h1>

# Herramientas

    - MITRE ATT&CK Navigator https://mitre-attack.github.io/attack-navigator/enterprise/#
    - MITRE Jypiter Notebook https://mybinder.org/v2/gh/mitre-attack/attack-scripts/master
    - DeTTECT https://github.com/rabobank-cdc/DeTTECT/

# Instalar



# Ejecutar 

    docker start -i dettect

# Usar Editor Local

    python dettect.py editor
    
Abre el editor interactivo en el navegador:

    http://localhost:8080/dettect-editor
    
Recuerda guardar los archivos YAML editados. Por defecto se guardarán en tus archivos de descarga.
    
# Data Sources
    
Genera tu primera capa en ATT&CK Navigator en base a las fuentes de datos disponibles en tu entorno:
       
       python dettect.py ds -fd sample-data/data-sources-endpoints.yaml -l
       
Importa el fichero JSON generado en /output en ATT&CK Navigator 
    
# Ajustar Visibilidad y Detección 
    
Ajusta la visibilidad y la detección asignando scores individuales a cada técnica. El siguiente comando genera un archivo de técnicas que solo incluye aquellas para las que hemos definido data sources anteriormente.
 
    python dettect.py ds -fd sample-data/data-sources-endpoints.yaml --yaml

Abre el archivo en el navegador usando el editor local:

    python dettect.py editor

Ajusta los scores individuales y guarda el archivo.

Genera un archivo JSON nuevo para ATT&CK Navigator con tu cobertura de visibilidad ajustada:

    python dettect.py v -ft sample-data/techniques-administration-endpoints.yaml -fd sample-data/data-sources-endpoints.yaml -l

Importa el fichero JSON generado en /output en ATT&CK Navigator.

Genera un archivo JSON nuevo para ATT&CK Navigator con tu cobertura de detección ajustada:

    python dettect.py d -ft sample-data/techniques-administration-endpoints.yaml -l

Importa el fichero JSON generado en /output en ATT&CK Navigator.

# Threat Actors

Genera un fichero JSON con el heatmap de todos los actores en ATT&CK. Cuanto más oscuro el color, más técnicas tienen en común:

    python dettect.py g

Genera un fichero JSON con el heatmap de solo los grupos en los que estamos interesados (FIN6, FIN7, FIN8):

    python dettect.py g -g 'fin7,fin8,fin6'
    
# Gap Análisis de Visibilidad y Detección (Purple Teaming)

Genera un JSON con el heatmap customizado de actores y con la plantilla ajustada con los valores de visibilidad y detección.

    python dettect.py g -g output/20190319-RedCanary-2.yaml -o output/techniques-administration-example-windows-revised3.yaml -t visibility
    
    python dettect.py g -g output/20190319-RedCanary-2.yaml -o output/techniques-administration-example-windows-revised3.yaml -t detection
    
Importa los ficheros JSON generados en /output en ATT&CK Navigator.

