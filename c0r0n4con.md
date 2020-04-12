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
    
# Visibilidad
    
Ajusta la visibilidad asignando scores individuales a cada técnica. El siguiente comando genera un archivo de técnicas que solo incluye aquellas para las que hemos definido visibilidad anteriormente.
 
        python dettect.py ds -fd sample-data/data-sources-endpoints.yaml --yaml


