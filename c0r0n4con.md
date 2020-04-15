<h1> Prioritizing your Threat Hunting & Blue Teaming strategy with MITRE ATT&CK analytics </h1>

# Tools

- MITRE ATT&CK Navigator https://mitre-attack.github.io/attack-navigator/enterprise/#
        
- MITRE Jypiter Notebook https://mybinder.org/v2/gh/mitre-attack/attack-scripts/master

- DeTTECT https://github.com/rabobank-cdc/DeTTECT/

# Installing DeTT&CT:

Download the docker image:

    docker pull rabobankcdc/dettect:latest

# Start DeTT&CT:

Linux & MacOS: 

    docker run -p 8080:8080 -v $(pwd)/output:/opt/DeTTECT/output -v $(pwd)/input:/opt/DeTTECT/input --name dettect -it rabobankcdc/dettect:latest /bin/bash

Windows (cmd.exe): 

    docker run -p 8080:8080 -v %cd%/output:/opt/DeTTECT/output -v %cd%/input:/opt/DeTTECT/input --name dettect -it rabobankcdc/dettect:latest /bin/bash

PowerShell: 

    docker run -p 8080:8080 -v ${PWD}/output:/opt/DeTTECT/output -v ${PWD}/input:/opt/DeTTECT/input --name dettect -it rabobankcdc/dettect:latest /bin/bash
 
Start the container:

    docker start -i dettect 

# Use local Editor

    python dettect.py editor
    
Open up the interactive editor in the browser:

    http://localhost:8080/dettect-editor
    
Don't forget to save the YAML files once edited. They'll be saved in the Downloads folder by default.
    
# Data Sources
    
Generate your first JSON layer to import in ATT&CK Navigator based on the data sources available in your environment:
       
       python dettect.py ds -fd sample-data/data-sources-endpoints.yaml -l
       
Import the JSON file in ATT&CK Navigator 
    
# Adjust Visibility & Detection
    
Adjust visibility and detection assigning individual scores to each technique. The following command will generate a file of techniques that will only include those for which we have defined data sources previously. 
 
    python dettect.py ds -fd sample-data/data-sources-endpoints.yaml --yaml

Open up the file with the browser, using the local editor:

    python dettect.py editor

Adjust the individual scores and save the file. 

Generate a new JSON file for ATT&CK Navigator with your adjusted visibility coverage:

    python dettect.py v -ft sample-data/techniques-administration-endpoints.yaml -fd sample-data/data-sources-endpoints.yaml -l

Import the resulting JSON file in ATT&CK Navigator.

Generate a new JSON file for ATT&CK Navigator with your adjusted detection coverage:

    python dettect.py d -ft sample-data/techniques-administration-endpoints.yaml -l

Import the resulting JSON file in ATT&CK Navigator.

# Threat Actors

Generates a JSON flie with a heatmap of all threat actors in ATT&CK. The darker the color, the more techniques they have in common:

    python dettect.py g

Generates a JSON file with the heatmap corresponding to the groups we're interested in (FIN6, FIN7, FIN8):

    python dettect.py g -g 'fin7,fin8,fin6'
    
# Visibility & Detection Gap Analysis (Purple Teaming)

Generates a customized heatmap in a JSON file using the selected threat actors and the adjusted YAML templates for visibility and detection: 

    python dettect.py g -g output/20190319-RedCanary-2.yaml -o output/techniques-administration-example-windows-revised3.yaml -t visibility
    
    python dettect.py g -g output/20190319-RedCanary-2.yaml -o output/techniques-administration-example-windows-revised3.yaml -t detection
    
Import the resulting JSON file in ATT&CK Navigator.
