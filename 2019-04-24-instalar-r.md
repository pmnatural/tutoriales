## ¿Cómo instalar R en Mac, Ubuntu y Windows?

*2019-04-22*

*Mauricio Vargas S. 帕夏*

*Este tutorial es una traducción de una adaptación del original que escribí en mi blog en inglés. Los videos también fueron traducidos*

## Motivación

Esta es una guía para usuarios principiantes pensada para ahorrarte un dolor de cabeza y tiempo valioso en caso de que necesites instalar R por tu cuenta.

Dado que hago clases, no me gusta gastar una hora de los talleres en instalar R. Para minimizar ese problema he pulido estas instrucciones con el tiempo y haciendo experimentos con distintos notebooks para intentar maximizar la experiencia de la clase.

Lo que encontrarás aquí es una colección de línea de código que funcionan al momento de instalar R. Desde luego, intenté varias soluciones que no funcionaron y lo que presento acá es el resultado final.

## R y RStudio

Esta configuración pretende instalar R y RStudio. Puedes imaginar la instalación de R como comprar un automóvil y RStudio como comprar un automóvil con todos los accesorios para una mejor experiencia de usuario.

[R](https://www.r-project.org/) se refiere a un entorno de software que viene con una GUI (Interfaz Gráfica de Usuario, viene de *Graphical User Interface*). La GUI de R es más parecida a la antigua consola de DOS que a SPSS o Stata.

[RStudio](https://www.rstudio.com/) es un IDE (Entorno de Desarrollo Integrado, del inglés *Integrated Development Environment*) que facilita el uso de R y es más similar a SPSS o Stata. Incluye un editor de código, depurador y herramientas de visualización. Por favor úsenlo para mejorar su experiencia de usuario con R.

## El Tidyverse

El [Tidyverse](https://www.tidyverse.org/) provee un conjunto de paquetes que aumentan las capacidades de R y que comparten una misma filosofía de diseño.

Un ejemplo destacable es `dplyr`, un paquete que realmente simplifica la manipulación de datos. A modo de ejemplo, provee, entre otras funciones y capacidades, las funciones `group_by` y `summarise` para realizar operaciones similares a `SUMAR.SI` o `SUMAR.SI.CONJUNTO` de Microsoft Excel.

Si deseas graficar usando R, El Tidyverse provee el paquete `ggplot2` para la creación de gráficos. Existen muy buenos tutoriales para aprender `ggplot2`. Jodie Burchell y yo escribimos [The Hitchhiker's Guide to Ggplot2](https://leanpub.com/hitchhikers_ggplot2) que se puede descargar de forma gratuita.

Otra herramienta interesante del Tidyverse es `haven`, un paquete para importar/exportar datos usando los formatos de SPSS, Stata y SAS.

## Instrucciones para usuarios de Mac

### Instalar R y RStudio

Instalar R en Mac puede ser problemático. LO que he escuchado de mis estudiantes es que las dependencias de software pueden ser un gran problema al momento de instalar R, lo que también aplica a Python, Ruby y otras herramientas.

¿Tiene que ser problemático? La opción más simple para instalar R en Mac es usar [Homebrew](https://brew.sh/) que es un administrador de paquetes que hace todo en tu lugar si le pasas un comando como `brew install r`. Para instalar R de esta forma necesitas hacer lo siguiente:

* Instalar las Herramientas de Línea de Comandos de XCode
* Instalar Homebrew
* Finalmente instalar R

Puedes descargar R para Mac desde [el sitio web de CRAN](http://cran.us.r-project.org/bin/macosx/). Algunos artículos [como este publicado en Medium](https://medium.com/@GalarnykMichael/install-r-and-rstudio-on-mac-e911606ce4f4) entregan una buena guía respecto de esa alternativa, pero mis estudiantes reclaman que ese método de instalación no les funciona a todos. Algunos han tenido problemas con el instalador pero lo han resuelto usando Homebrew.

Recomiendo instalar R con [OpenBLAS](http://www.openblas.net/). En palabras simples, OpenBLAS acelera algunas operaciones y quiero que seas un usuario feliz. Puedes ignorar esta recomendación si vas a trabajar con conjuntos de datos relativamente pequeños.

Entre los pasos tres o cuatro, debes escoger uno solo, el que creas que es más conveniente para ti. No ejecutes el paso tres y luego el cuatro o vas a perder tiempo dado que el paso cuatro reemplazará todo lo que hiciste en el paso tres.

### Paso 1: Instalar las Herramientas de Línea de Comandos de XCode

Compilar software en Mac requiere instalar [XCode CLT](https://developer.apple.com/download/more/). Dado que algunos pasos de esta instalación de R requieren compilación, no hay forma de evadir este paso.

Abre la terminal (cmd + espacio y busca 'Terminal'), luego pega el siguiente comando:
```
xcode-select --install
```
Presiona enter y espera un minuto. Si tu computador ya tiene este software instalado, verás un mensaje que dice que XCode CLT ya está instalado, en caso contrario comenzará a descargar e instalar el software.

Consulta el siguiente <a href="https://www.youtube.com/embed/ZNrmawbATtM" target="_blank" >video</a> en caso de dudas.

### Paso 2: Instalar Homebrew

Para instalar Homebrew pega el siguiente comando en la terminal:
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
Luego presiona enter y observa los múltiples emojis que aparecen en la pantalla.

Seguramente vas a querer configurar las rutas de Homebrew. Para hacerlo basta con replicar lo siguiente una vez. La razón para hacer esto es que es la forma de decirle al sistema en que carpeta del disco duro se encuentra el software de Homebrew.

Pega el siguiente código en la terminal:
```
## Homebrew PATH
echo "export LC_ALL=es_ES.UTF-8" >> ~/.bash_profile
echo "export LANG=es_ES.UTF-8" >> ~/.bash_profile
echo "export PATH=/usr/local/bin:$PATH" >> ~/.bash_profile && source ~/.bash_profile
```
Como ya habrás adivinado, debes presionar enter luego de pegar esto.

Consulta el siguiente <a href="https://www.youtube.com/embed/ZNrmawbATtM?start=20" target="_blank" >video</a> en caso de dudas.

### Paso 3: Instalar R sin OpenBLAS

Ya tenemos XCode CLT y Hombrew instalado. Ahora pega el siguiente código en la terminal:
```
brew install r
echo 'Sys.setlocale(category="LC_ALL", locale = "en_US.UTF-8")' >> ~/.bash_profile
```
Presiona enter y algo bueno sucederá.

Consulta el siguiente <a href="https://www.youtube.com/embed/ZNrmawbATtM?start=50" target="_blank" >video</a> en caso de dudas.

### Paso 4: Instalar R con OpenBLAS

Este paso es muy similar al anterior. Pega el siguiente código en la terminal:
```
brew install openblas
brew install r --with-openblas
echo 'Sys.setlocale(category="LC_ALL", locale = "en_US.UTF-8")' >> ~/.bash_profile
```
Presiona enter y algo bueno sucederá.

Consulta el siguiente <a href="https://www.youtube.com/embed/ZNrmawbATtM?start=50" target="_blank" >video</a> en caso de dudas.

### Paso 5: Instala RStudio

Finalmente, pega el siguiente código en la terminal:
```
brew cask install rstudio
```
Presiona enter y estarás listo.

Consulta el siguiente <a href="https://www.youtube.com/embed/ZNrmawbATtM?start=285" target="_blank" >video</a> en caso de dudas.

## Instrucciones para usuarios de Ubuntu

### Instalar R y RStudio

Recomiendo instalar R con [OpenBLAS](http://www.openblas.net/). En palabras simples, OpenBLAS acelera algunas operaciones y quiero que seas un usuario feliz. Puedes ignorar esta recomendación si vas a trabajar con conjuntos de datos relativamente pequeños.

Instalar R en Ubuntu es simple, ¡sorprendentemente simple! Podemos instalar R, RStudio y el Tidyverse de manera muy sencilla en comparación a Mac o incluso Windows.

Entre los pasos uno o dos, debes escoger uno solo, el que creas que es más conveniente para ti. No ejecutes el paso uno y luego el dos o vas a perder tiempo dado que el paso dos reemplazará todo lo que hiciste en el paso uno

### Paso 1: Instalar R sin OpenBLAS

Abre la terminal y pega el siguiente código:
```
# R sin OpenBLAS
sudo apt-get install r-base
```
Luego presiona enter.

Consulta el siguiente <a href="https://www.youtube.com/embed/ZNrmawbATtM?start=90" target="_blank" >video</a> en caso de dudas.

### Paso 2: Instalar R con OpenBLAS

Abre la terminal y pega el siguiente código:
```
# R con OpenBLAS
sudo apt-get install libopenblas-base r-base
```
Luego presiona enter.

Consulta el siguiente <a href="https://www.youtube.com/embed/ZNrmawbATtM?start=90" target="_blank" >video</a> en caso de dudas.

### Paso 3: Instalar RStudio

No cierres la terminal y pega el siguiente código:
```
sudo apt-get install gdebi
cd ~/Downloads
wget https://download1.rstudio.org/rstudio-xenial-1.1.379-amd64.deb
sudo gdebi rstudio-xenial-1.1.379-amd64.deb
```
Luego presiona enter.

Otra alternativa es visitar el sitio web de [RStudio](https://www.rstudio.com) para descargar el software a instalarlo desde el escritorio con un instalador gráfico.

Consulta el siguiente <a href="https://www.youtube.com/embed/ZNrmawbATtM?start=320" target="_blank" >video</a> en caso de dudas.

## Instrucciones para usuarios de Windows

### Instalar R y RStudio

Mi experiencia con Windows y R cambió de trágica a magnífica. Lo que cambió esa experiencia fue [Microsoft R Open](https://mran.microsoft.com/open), una versión de R que incluye [Intel MKL](https://software.intel.com/en-us/mkl), una librería numérica que aumenta la velocidad de algunas operaciones y que viene activada por defecto.

En cualquier caso siempre puedes instalar la versión estándar de R. Por favor no ignores que entre los pasos uno o dos, debes escoger uno solo, el que creas que es más conveniente para ti.

### Paso 1: Instalar Microsoft R Open

Para instalar R en Windows se puede obtener del sitio web de [MRO](https://mran.microsoft.com/download) y luego ejecutar el instalador. La configuración es directa, basta con presional "siguiente" todas las veces que el programa lo pida y asegurarse de marcar la opción MKL.

Consulta el siguiente <a href="https://www.youtube.com/embed/ZNrmawbATtM?start=130" target="_blank" >video</a> en caso de dudas.

### Paso 2: Instalar R estándar

Como alternativa al paso uno, R estándar se puede bajar desde CRAN (La Red Exhaustiva de Archivo de R, del inglés *The Comprehensive R Archive Network*). Visita el sitio web de [CRAN](https://cran.r-project.org/) para obtener la última versión.

Consulta el siguiente <a href="https://www.youtube.com/embed/ZNrmawbATtM?start=225" target="_blank" >video</a> en caso de dudas.

### Paso 3: Instala RStudio

Para instalar RStudio visita el sitio web de [RStudio](https://www.rstudio.com/products/rstudio/download/#download) y descarga la última versión.

Consulta el siguiente <a href="https://www.youtube.com/embed/ZNrmawbATtM?start=370" target="_blank" >video</a> en caso de dudas.

## Instala el Tidyverse

Abre RStudio. Los siguientes pasos son los mismos para cualquier sistema operativo.

En el panel inferior izquierdo de RStudio puedes escribir cualquier comando válido y R ejecutará dicho comando.

Pega el siguiente código en el panel inferior izquierdo:
```{r install-tidyverse, eval = F}
install.packages("tidyverse", repos = 'https://cran.us.r-project.org')
```
Presiona enter y tendrás una configuración de R a punto.

Consulta el siguiente <a href="https://www.youtube.com/embed/ZNrmawbATtM?start=425" target="_blank" >video</a> en caso de dudas.

## Instalar más paquetes de R

Aparte del Tidyverse existen otros paquetes muy útiles.

Algunos de los que uso a diario son:

* `XML`: Read and create XML documents with R.
* `jsonlite`: Read and create JSON data tables with R.
* `httr`: A set of useful tools for working with http connections.
* `rvest`: Very useful for web scraping.

Quizá creas que este es el mejor modo de instalar varios paquetes:
```{r install-more-packages-1, eval = F}
install.packages("XML", repos = 'https://cran.us.r-project.org')
install.packages("jsonlite", repos = 'https://cran.us.r-project.org')
etc...
```

Pero existe un modo más eficiente de hacerlo:
```{r install-more-packages-2, eval = F}
install.packages(c("XML", "jsonlite", "httr", "rvest"))
```

Consulta el siguiente <a href="https://www.youtube.com/embed/ZNrmawbATtM?start=450" target="_blank" >video</a> en caso de dudas.

## Verifica que todo funcione

En RStudio dirígete a Archivo, luego Archivo Nuevo y luego click en Script de R. En el archivo en blanco que aparece, pega el siguiente código:

```{r plot, warning = F}
library(ggplot2)

ggplot(airquality, aes(x = Day, y = Ozone)) +
  geom_point()
```

Lo que el código hace es cargar `ggplot` e instruirle que use `airquality`, un conjunto de datos que viene con R, para graficar Día versus Ozono.

Necesitamos cargar paquetes porque si la instalación fresca de R viniera con los más de 10.000 paquetes que existen, la descarga e instalación del software sería muy lenta y abrir RStudio sería más lento aún.

Para correr el código selecciona las líneas y presiona Control + Enter (o CMD + Enter en Mac). Si todo funcionó, aparecerá un gráfico en el panel inferior derecho.

Consulta el siguiente <a href="https://www.youtube.com/embed/ZNrmawbATtM?start=475" target="_blank" >video</a> en caso de dudas.

## Estética de RStudio

Recomiendo cambiar los colores del programa para reducir la fatiga visual. Para cambiar los colores de RStudio debes ir a Herramientas, luego a Opciones Globales y finalmente a Apariencia.

Me gusta el tema Cobalto con la tipografía [Ubuntu Mono](https://fonts.google.com/specimen/Ubuntu+Mono) dado que escribo código todo el día.

Consulta el siguiente <a href="https://www.youtube.com/embed/ZNrmawbATtM?start=500" target="_blank" >video</a> en caso de dudas.

## Obtén el mayor provecho de este tutorial

Anteriormente subí tutoriales y ejercicios a DataCamp. Luego de los eventos revelados la primera semana de Abril, he decidido quitar mis video de la plataforma y dejar de recomendar sus servicios.

Aquí hay una lista de buenas recomendaciones que hizo [Jesse Mostipak](https://twitter.com/kierisi):

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">so you&#39;ve heard about DataCamp and want to leave the platform, but aren&#39;t sure where to go for your <a href="https://twitter.com/hashtag/rstats?src=hash&amp;ref_src=twsrc%5Etfw">#rstats</a> learning. well friends, you can start here:<br><br>🌊 <a href="https://t.co/SOIXekQIYL">https://t.co/SOIXekQIYL</a><br>💻 <a href="https://t.co/jHS4SXhYQZ">https://t.co/jHS4SXhYQZ</a><br>📊 <a href="https://t.co/xhVR2IQYl7">https://t.co/xhVR2IQYl7</a><br>🦜 <a href="https://t.co/G442ZY0Ny8">https://t.co/G442ZY0Ny8</a></p>&mdash; Jesse Mostipak (@kierisi) <a href="https://twitter.com/kierisi/status/1114162997604311040?ref_src=twsrc%5Etfw">April 5, 2019</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
