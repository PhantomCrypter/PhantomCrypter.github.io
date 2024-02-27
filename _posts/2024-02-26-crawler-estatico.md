---
layout: single
title: Crawler En Página Estática
excerpt: "En este proyecto, exploré el web scraping utilizando Python y Beautiful Soup para extraer información de una página web estática de manera automatizada. Utilizando Python y Beautiful Soup, desarrollé un crawler eficiente que me permitió recopilar datos relevantes de la página objetivo. A lo largo de esta breve introducción, compartiré mi experiencia y los resultados obtenidos."
date: 2024-02-26
classes: wide
header:
  teaser: /assets/images/Crawler-stat/wc.png
  teaser_home_page: true
  icon: 
categories:
  - Crawler
  - infosec
tags:  
  - Python
  - Ciberinteligencia
  - Automatización

---

![](/assets/images/Crawler-stat/wc.png)

En este proyecto, me aventuré en el fascinante mundo del web scraping utilizando Python y Beautiful Soup. El objetivo principal fue extraer información de una página web estática de manera automatizada, lo que me permitió recopilar datos relevantes para su posterior análisis o uso.

Al emplear Python como lenguaje de programación principal y Beautiful Soup como biblioteca de análisis HTML, pude desarrollar un crawler eficiente y poderoso. El proceso implicaba navegar por el código HTML de la página objetivo, identificar y extraer los elementos deseados, como texto, enlaces o imágenes, y luego procesar esa información según mis necesidades específicas.

Este proyecto no solo me proporcionó una sólida comprensión de la manipulación de datos web con Python, sino que también me permitió explorar conceptos como la estructura del documento HTML, la selección de elementos mediante selectores y la gestión de datos extraídos.

A lo largo de esta breve introducción, compartiré mi experiencia, los desafíos enfrentados y las soluciones implementadas durante el desarrollo de este emocionante proyecto de crawler en Python.

## ¿Qué es un Crawler?

Un `crawler`, también conocido como "rastreador web" o "araña web", es un programa de software que navega por la web de manera automatizada, siguiendo enlaces de una página a otra. Su objetivo principal es `indexar` y `recopilar` información de diversas páginas web para su posterior análisis o indexación en motores de búsqueda. Los crawlers son fundamentales para la indexación y la recuperación de información en la web, ya que facilitan la recopilación de datos de manera eficiente y sistemática.

## Desventajas de los crawlers

Los crawlers enfrentan algunas desventajas al tratar con páginas que no son estáticas:

    Dificultad para rastrear cambios dinámicos: Los crawlers pueden tener dificultades para detectar cambios en el contenido de las páginas dinámicas, ya que estas se generan mediante scripts o consultas a bases de datos en tiempo real. Esto significa que los cambios en el contenido pueden no ser capturados de manera oportuna o precisa.

    Posibilidad de rastrear información irrelevante o duplicada: Debido a la naturaleza dinámica del contenido, los crawlers pueden encontrarse con dificultades para distinguir entre contenido relevante y contenido redundante o irrelevante que se genera dinámicamente. Esto puede resultar en la indexación de información duplicada o poco útil.

    Necesidad de actualización constante: Los crawlers deben adaptarse continuamente a los cambios en la estructura y el comportamiento de las páginas dinámicas para garantizar un rastreo efectivo. Esto puede requerir una inversión adicional en desarrollo y mantenimiento de software para mantener el crawler actualizado.

Por esta razón, para este proyecto he decidido utilizar una página web estática para así asegurar que este proyecto sea 100% funcional y que pueda servir de base para otros futuros proyectos.

## Reconocimiento

Paso 1:

Antes de empezar con nuestro Crawler, primero tenemos que escoger la página objetivo. Yo usé la página de [Real Python](https://realpython.com), usando el siguiente link: [https://realpython.github.io/fake-jobs/](https://realpython.github.io/fake-jobs/)

En este ejemplo usé esta página ya que a como se muestra en los entrenamientos de [Real Python](https://realpython.com), esta es la mejor forma de aprender ya que la página es 100% estática por lo que no va a haber ningún cambio futuro que afecte el desempeño del Crawler.

Paso 2:

Una vez dentro se debe de identificar la información en la cual estamos interesados:


![](/assets/images/Crawler-stat/p2.png)


Paso 3:

Cuando ya tenemos nuestros objetivos identificados, se procede a buscarlos en el HTML haciendo uso de la secuencia de teclas CTRL + SHIFT + I

Paso 4:

Explorando las Herramientas para el Desarrollador podemos notar que la información que necesitamos se encuentra en las etiquetas de encabezado <h2>, <h3> y <p>.


![](/assets/images/Crawler-stat/p3.png)


## Desarrollo


## Conclusión


## Código Documentado


```
# Importación de módulos necesarios
import requests
from bs4 import BeautifulSoup

# Definición de la URL de la página web a analizar
URL = "https://realpython.github.io/fake-jobs/"

# Realizar una solicitud HTTP a la página web y almacenar el contenido de la página en una variable
page = requests.get(URL)

# Crear un objeto BeautifulSoup para analizar el contenido HTML de la página
soup = BeautifulSoup(page.content, "html.parser")

# Encontrar el elemento en la página con el ID "ResultsContainer"
results = soup.find(id="ResultsContainer")

# Solicitar al usuario que ingrese el tema de trabajo de interés
tema = input("En cuál trabajo se encuentra interesado?:  ")

# Construir el título para mostrar en la salida
titulo = "Trabajos en " + tema

# Convertir el tema ingresado a minúsculas para una comparación insensible a mayúsculas y minúsculas
minus = tema.lower()

# Imprimir el título con líneas separadoras
print("\n" + titulo + "\n" + "-" * len(titulo) + "\n")

# Encontrar todos los elementos <h2> que contienen el tema ingresado y sus elementos padres
Request_jobs = results.find_all("h2", string=lambda text: minus in text.lower())
Request_job_elements = [h2_element.parent.parent.parent for h2_element in Request_jobs]

# Imprimir el número de trabajos relacionados encontrados
print("[*] Búsquedas relacionadas " + str(len(Request_jobs)) + "\n")

# Iterar sobre los elementos de trabajo encontrados y mostrar la información relevante
for job_element in Request_job_elements:
    title_element = job_element.find("h2", class_="title")
    company_element = job_element.find("h3", class_="company")
    location_element = job_element.find("p", class_="location")
    print(title_element.text.strip())
    print(company_element.text.strip())
    print(location_element.text.strip())
    
    # Obtener el enlace para aplicar al trabajo
    link_url = job_element.find_all("a")[1]["href"]
    print(f"Apply here: {link_url}\n")
    print()

```
Este código realiza lo siguiente:

    1. Realiza una solicitud HTTP a una página web.

    2. Utiliza BeautifulSoup para analizar el contenido HTML de la página.

    3. Encuentra elementos específicos en la página web.

    4. Interactúa con el usuario para obtener información sobre el trabajo de interés.

    5. Filtra los trabajos que coinciden con el tema de interés.

    6. Muestra información relevante sobre los trabajos encontrados, incluidos títulos, empresas, ubicaciones y enlaces para aplicar.


