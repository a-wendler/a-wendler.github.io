---
layout: single
title:  "Ein Dashboard für die Gemeinsame Normdatei (GND)"
excerpt: "Wie kann man fast 9 Millionen Datensätze aus der GND anschaulich machen? Wir haben ein Dashboard dafür programmiert."

date:   2021-06-07
categories:
  - Data Science
 
tags:
  - GND
  - Python
  - Visualisierung

header:
  overlay_image: /assets/images/2021-06-24-gnd-dashboard.jpg
  overlay_filter: 0.5
  actions:
    - label: "zum Dashboard"
      url: "https://share.streamlit.io/buchmuseum/gnd_dashboard/main/dashboard/gnd-app.py"
---

Aus Anlass der [GNDCon 2.0](https://wiki.dnb.de/pages/viewrecentblogposts.action?key=GND) im Juni 2021, habe einige Kollegen der Deutschen Nationalbibliothek ein Dashboard gebaut, um die fast 9 Millionen Datensätze der gemeinsamen Normdatei etwas greifbarer und übersichtlicher zu machen.

[Hier geht es direkt zum Dashboard](https://share.streamlit.io/buchmuseum/gnd_dashboard/main/dashboard/gnd-app.py)
{: .notice--info}
{: .text-center}

## Datenmassen

Einen Gesamtabzug der Titeldaten der DNB und der GND haben wir nach verschiedenen Kriterien gefiltert. Das klingt einfacher, als es ist, weil die Menge der Daten sich nicht mit herkömmlichen Mitteln verarbeiten lässt. Mein Kollege [Niko Wagner](https://github.com/niko2342) hat dazu ein spezielles Tool programmiert. Sein [Pica-Parser](https://github.com/deutsche-nationalbibliothek/pica-rs) braucht nur wenige Minuten, um die enormen Datenmengen zu durchsuchen und die gewünschten Daten als übersichtliche und leichter zu verarbeitende CSV-Dateien zu extrahieren.

## Visualisierung

Unser Dashboard bietet allgemeine Informationen zur gesamten GND: welche Satzarten wie häufig vorkommen, welche Entitäten am häufigsten verwendet werden, in welchem zeitlichen Verlauf die Daten seit den 1970er-Jahren in die GND und ihre Vorläufer kamen.

{% capture fig_img %}
![Wordcloud]({{ site.url }}{{ site.baseurl }}/assets/images/2021-06-24-wordcloud.jpg)
{% endcapture %}

<figure>
  {{ fig_img | markdownify | remove: "<p>" | remove: "</p>" }}
  <figcaption>Wordcloud mit GND-Sachbegriffen</figcaption>
</figure>

Außerdem kann man nach den einzelnen Satzarten filtern und sich zusätzliche Widgets anzeigen lassen, z. B.

- eine Karte der häufigsten Wirkungsorte
- eine Word-Cloud der zuletzt verwendeten Sachbegriffe

{% capture fig_img %}
![Karte]({{ site.url }}{{ site.baseurl }}/assets/images/2021-06-24-karte-wirkungsorte.jpg)
{% endcapture %}

<figure>
  {{ fig_img | markdownify | remove: "<p>" | remove: "</p>" }}
  <figcaption>Karte mit Wirkungsorten von GND-Personen</figcaption>
</figure>

## Offene Daten

Die zugrundeliegenden Daten sind unter CC0-Lizenz [frei verfügbar](https://www.dnb.de/DE/Professionell/Standardisierung/GND/gnd_node.html#doc58016bodyText4). Die Skripte für die Datenverarbeitung das Dashboard selbst sind ebenfalls [frei bei GitHub](https://github.com/buchmuseum/GND_Dashboard) einzusehen.

## Hintergrund: Was ist die Gemeinsame Normdatei

Die Gemeinsame Normdatei (GND) enthalt normierte Personen, Körperschaften, Geografika, Sachschlageworte und weitere Normdaten. Sie stammt ursprünglich aus der Bibliothekswelt und wird in der Deutschen Nationalbibliothek (DNB) gehostet. Kultureinrichtungen, die die Normbegriffe der GND verwenden, können so Namen, Institutionen und geografische Orte eindeutig identifizieren.

Ein Beispiel: bei »Berlin« denken die meisten an die deutsche Hauptstadt. Tatsächlich gibt es aber in Nordamerika etliche Plätze mit demselben Namen. Wer die deutsche Hauptstadt und nicht einen der anderen Orte meint, kann sich auf den [Normdatensatz von Berlin](http://d-nb.info/gnd/4005728-8) beziehen und in einem Katalog oder einer Publikation den GND-Identifier 4005728-8. Der Name ist nun eineindeutig identifizert.
{: .notice}

Seit einigen Jahren nutzen nicht nur Bibliotheken diese Normdaten sondern immer mehr auch Museen, Archive, Forschungseinrichtungen. Es wird dadurch immer leichter möglich, die Datenbestände und Sammlungen der einzelnen Einrichtungen miteinander zu verbinden.