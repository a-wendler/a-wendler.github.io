---
layout: single
title:  "Data Science im Museum"
excerpt: "Ein Dashboard für 1 Million Objekte aus der Sammlung des Deutschen Buch- und Schriftmuseums"

date:   2021-07-21
categories:
  - Data Science
 
tags:
  - Museum
  - DBSM
  - Python
  - Visualisierung

header:
  overlay_image: /assets/images/2021-07-21-dbsm-dashboard.png
  overlay_filter: 0.5
---

Museen können üblicherweise nur einen Bruchteil der Objekte in ihren Sammlungen ausstellen. Die meisten Objekte bleiben im Depot und warten darauf, für ein Forschungsvorhaben oder eine Ausstellung hervorgeholt zu werden. Wer trotzdem einen Überblick über die gesamte Sammlung eines Museums haben wollte, musste sich durch endlose Kataloge wälzen oder war auf zusammenfassende Bestandsbeschreibungen angewiesen.

Für das [Deutsche Buch- und Schriftmuseum](https://www.dnb.de/dbsm) der Deutschen Nationalbibliothek in Leipzig haben wir einen anderen Ansatz versucht: Die elektronischen Katalogdaten wurden massenhaft ausgewertet und zu übersichtlichen Darstellungen verarbeitet.

# Das Dashboard

Auf dem Dashboard kann man die gesamte Sammlung oder einzelne Teilsammlungen analysieren. Die Sammlungsgegenstände sind nach Entstehungszeit oder geografischer Herkunft dargestellt. Die zeitliche und räumliche Dimension kann auch gekoppelt werden. So lassen sich zum Beispiel alle im Bestand vorhandenen Herstellungsorte eines bestimmten Zeitraums auf einer Karte darstellen. Wer geografisch begrenzte Studien am Bestand durchführen will, kann so leicht sehen, ob sich der Bestand dafür eignet.

{% capture fig_img %}
![Zeitdiagramm]({{ site.url }}{{ site.baseurl }}/assets/images/2021-07-21-zeitdiagramm.png)
{% endcapture %}

<figure>
  {{ fig_img | markdownify | remove: "<p>" | remove: "</p>" }}
  <figcaption>Zeitliche Einordnung der Sammlungsobjekte</figcaption>
</figure>

Für die Inkunabelsammlung wurde eine Karte erstellt, auf der man sehen kann, aus welchen der über 300 bekannten Inkunabeldruckorten das Museum Exemplare besitzt.

# Datenaufbereitung

Es gibt einen einfachen Zugriff auf die Museumsdaten über einen Gesamtabzug im Bibliotheksformat PICA+, der mit dem Tool [pica.rs](https://github.com/deutsche-nationalbibliothek/pica-rs) gefiltert und nach CSV exportiert werden kann. Die Daten sind aber nicht ohne weiteres in Diagrammen oder auf Karten darstellbar.

Bei der __zeitlichen Einordnung__ gibt es zum Beispiel sehr unterschiedliche Angaben. Wenn Daten nur indirekt ermittelt wurden und sich nicht vom Objekt selbst ablesen lassen, werden üblicherweise eckige Klammern ergänzt: \[1809\]. Unklare oder zweifelhafte Angaben werden mit Fragezeichen gekennzeichnet: 1809?. Ist das Jahrzehnt der Entstehung, aber nicht das genaue Jahr bekannt, können Angaben wie 182X verwendet werden und alle diese Kennzeichen können natürlich auch miteinander kombiniert werden: \[182X?\]

Solche Angaben müssen entweder normalisiert werden oder man entscheidet sich, sie aus der Auswertung auszuschließen.

Ähnliches gilt für Formats- und Umfangsangaben. Traditionell werden die Formate von Büchern vor dem 19. Jahrhundert in einer Form angegeben, die sich aus der Anzahl der Faltungen des Druckbogens ergibt: das Oktavformat zum Beispiel als 8° oder gr. 8°. Bei sehr alten Drucken werden oft die Lagen einzeln aufgeführt und es ist keine Seltenheit, dass Umfangsbeschreibungen wie diese dabei herauskommen: 1 Tafel, 246, 276 Blätter, 3 gefaltete Karten.

Diese Daten müssen automatisch ausgewertet werden, wozu man die bibliothekarischen Regelwerke kennen sollte. Auch hier muss die Entscheidung getroffen werden, wie man mit schlecht oder gar nicht auszuwertenden Angaben und Fehlern umgeht.

# Code und Lizenz

Das Dashboard ist derzeit nicht mehr online. Der Source-Code des Dashboards ist auf [GitHub](https://github.com/buchmuseum/dbsm-dashboard) verfügbar. Die Daten und Skripte stehen unter freien Lizenzen zur Verfügung.
