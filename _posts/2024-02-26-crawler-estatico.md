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



## Reconocimiento


## Desarrollo


## Conclusión


## Código Documentado

There was a hint earlier that some variation of `PleaseSubscribe!` is used.

I'll use hashcat for this and since I don't know the hash ID for bcrypt by heart I can find it in the help.

```
C:\bin\hashcat>hashcat --help | findstr bcrypt
   3200 | bcrypt $2*$, Blowfish (Unix)                     | Operating System
```

My go-to rules is normally one of those two ruleset:

- [https://github.com/NSAKEY/nsa-rules/blob/master/_NSAKEY.v2.dive.rule](https://github.com/NSAKEY/nsa-rules/blob/master/_NSAKEY.v2.dive.rule)
- [https://github.com/NotSoSecure/password_cracking_rules/blob/master/OneRuleToRuleThemAll.rule](https://github.com/NotSoSecure/password_cracking_rules/blob/master/OneRuleToRuleThemAll.rule)

These will perform all sort of transformations on the wordlist and we can quickly crack the password: `PleaseSubscribe!21`

```
C:\bin\hashcat>hashcat -a 0 -m 3200 -w 3 -O -r rules\_NSAKEY.v2.dive.rule hash.txt wordlist.txt
[...]
$2a$10$VM6EeymRxJ29r8Wjkr8Dtev0O.1STWb4.4ScG.anuu7v0EFJwgjjO:PleaseSubscribe!21

Session..........: hashcat
Status...........: Cracked
Hash.Name........: bcrypt $2*$, Blowfish (Unix)
[...]
```

The root password from MatterMost is the same as the local root password so we can just su to root and get the system flag.

![](/assets/images/htb-writeup-delivery/root.png) 
