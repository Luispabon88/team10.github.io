## Desafío: 
-Generar código/Script para convertir los datasets a formato comercial (se escogió .csv).

-Usar solo librerías python comerciales y de libre accsero para análisis de data parcial del Bosón de Higgs.

-Generar un gráfico en matplotlib (o similar) de la masa invariante de 4 leptones.

## Codificación
### Generar código/Script para convertir los datasets a formato comercial.
Hemos obtenido la data desde el sitio web [opendata CERN](http://opendata.web.cern.ch/record/12361), donde usando la herramienta colaborativa de Google desde el Google Drive, se ha originado un archivo codificado en Python. El archivo obtenido es un .ROOT, el cual no es comercial ni fácil de utilizar directamente, lo cual limita su uso. Uno de los objetivos principales de nuestro trabajo es crear un código en Python que convierta este .ROOT en un archivo separado por comas en EXCEL, el cual permita la difusión del trabajo y deje la data al alcance de todos.

Lo primero que debemos hacer es instalar en el Google Drive la herramienta Colaboratory, disponible en la sección de más herramientas al dar click en el <b>+</b> de Google Drive en la parte superior izquierda.

<img src="001_instalarColGoogle.png"
     width="400"
     height="300">

Dentro de Market Place, buscamos la aplicación Colaboratory (en la imagen siguiente se muestra que ya está instalada).

<img src="002_market.png"
     width="400"
     height="200">

Se procede a crear un archivo nuevo de tipo colaborativo, donde se realizará la programación. Como primer paso debemos realizar la instalación de la libreria <b>uproot</b>. Esta nos permitirá leer el archivo .ROOT y poder procesarlo. NOTA: Para ejecutar el código se debe dar click en un botón "play" a la izquierda del código.

```markdown
!pip install uproot awkward #
```

A continuación, se deben declarar las librerias a utilizar. Para resolver nuestra problemática utilizaremos funciones conocidas y básicas dentro de Python:

```markdown
import uproot
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from scipy import constants
```

Como observamos, necesitaremos de la libreria uproot para abrir el .ROOT, de pandas para manejo y análisis de estructuras de datos, numpy para manejo de datos y cálculos asociados, además de matplotlib.pyplot para las gráficas necesarias. La librería scipy se utiliza para los valores de las constantes en la Física, de caso puntual, la constante de la velocidad de la luz en el vacío.

Procederemos a subir el archivo con la data a procesar. En el código mostrado a continuación, al ser ejecutado, se mostrarán dos botones <b>Elegir Archivo</b> y <b>Cancelar</b> mientras ejecuta la segunda línea y espera por su decisión. <b>Elegir Archivo</b> le permitirá buscar en su computador el archivo de datos. Para nuestra solución, utilizaremos el archivo <b>SMHiggsToZZTo4L.root</b>.
```markdown
from google.colab import files
uploaded = files.upload()
```
Debemos verificar que el archivo termine de cargarse correctamente. Para esto, deberemos observar el progreso y que la barra termine de cargar. La siguiente imagen muestra el mensaje final del proceso:

<img src="003_100.PNG">

Lo siguiente es leer el archivo cargado usando la librería <b>uproot</b> para poder manejar los datos.

```markdown
file = uproot.open("SMHiggsToZZTo4L.root")
```

Como un paso de verificación, se puede usar el código a continuación que permite visualizar las variables (head columns) del archivo de datos.
```markdown
file['Events'].show()
```
Declararemos la variable <b>events</b> para proceder a crear los archivos panda.
```markdown
events = file['Events']
```

Los archivos panda nos permitiran el análisis discriminado de data. Esto es para poder separar los eventos donde se detectan muones y electrones. Como podemos observar en la siguiente figura, se presenta un diagrama de Feynman, el cual inicia con el proceso de  producción de un boson de Higgs, la partículas entrantes son gluones, uno de cada protón de la colisión. Luego se desintegra en un par de bosones Z  y posteriormente vuelve a desintegrarse en 4 leptones

<img src="004_signal.PNG">





```markdown
prueba
```

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for


Syntax highlighted code block

# Header 1
## Header 2
### Header 3



### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/Luispabon88/luispabon88.github.io/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
