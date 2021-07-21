---
layout: single
title:  "Börsenblatt Eplorer"
date:   2020-10-15
excerpt: "Eine App zur Erkundung des Börsenblattes für den Deutschen Buchhandel 1834–1945"
comments: true
header:
  overlay_image: /assets/images/2021-07-21-bbl.jpg
  teaser: /assets/images/2021-07-21-bbl.jpg
  overlay_filter: 0.5
  actions:
    - label: "zur App"
      url: "https://share.streamlit.io/a-wendler/bbl-streamlit/bbl-streamlit-app.py"
---

Das Börsenblatt für den Deutschen Buchhandel ist eine buchhändlerische Zeitschrift, die seit 1834 bis heute erscheint. In ihr bewerben Verlage neue Erscheinungen und Buchhändler ihre Angebote. Das historische Börsenblatt ist eine einmalige Quelle für die Geschichte des deutschsprachigen Buchhandels im 19. Jahrhundert.

Mehr als 27.000 Ausgaben mit fast 830.000 Seiten wurden durch die Sächsische Landes- und Universitätsbibliothek Dresden in Kooperation mit der Deutschen Nationalbibliothek digitalisiert und sind [frei verfügbar](https://www.boersenblatt-digital.de).

Um einen Einstieg in diese riesige Textmenge zu erleichtern, wurde eine [Webapp](https://share.streamlit.io/a-wendler/bbl-streamlit/bbl-streamlit-app.py) programmiert, die den Erscheinungsverlauf nach dem Umfang der Hefte auswertet. So können überdurchschnittlich umfangreiche Hefte ausfindig gemacht werden, die oft Jahresverzeichnisse oder besonders dicke Anzeigenteile zur Buchmesse enthalten.

{% capture fig_img %}
![Diagramm]({{ site.url }}{{ site.baseurl }}/assets/images/2021-07-21-bbl-explorer-diagramm.png)
{% endcapture %}

<figure>
  {{ fig_img | markdownify | remove: "<p>" | remove: "</p>" }}
  <figcaption>Erscheinungsverlauf mit Umfang der einzelnen Hefte</figcaption>
</figure>

# Datenherkunft

Über die [OAI-Schnittstelle](https://digital.slub-dresden.de/oai?verb=ListSets) der Sächsischen Landes- und Universitätsbibliothek Dresden wurden die Metadaten der Digitalisate im METS/MODS-Format heruntergeladen. Pro Ausgabe bekommt man eine Datei. Diese Dateien wurden dann mit einem Python-Skript ausgewertet. Aus der Anzahl der darin verlinkten Bilddateien ergibt sich die Anzahl der Seiten pro Heft.

Mit Streamlit und Altair wurde dann eine interaktive Grafik des Erscheinungsverlaufs gezeichnet, die jeweils die umfangreichsten Hefte inkl. Link zum Digitalisat angibt.