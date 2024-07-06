---
title: La cartografia geologica dell’Umbria per Qgis
description: La cartografia geologica vettoriale dell’Umbria, stilizzata per Qgis e impacchettata in un geopackage
autor: freddi
date: 2019-06-19 12:00:00 +0000
categories: [Qgis, Stilizzazione]
tags: [Qgis, geologia, cartografia, stili, Umbria]     # TAG names should always be lowercase
pin: false
math: true
mermaid: true
image:
  path: /media/images/copertina.jpeg
  
  alt: Esempio di cartografia geologica prodotta con gli stili per Qgis.
---

Da qualche tempo la Regione Umbria ha pubblicato i dati della cartografia geologica, prodotta nell’ambito del Progetto [CARG](https://www.isprambiente.gov.it/it/progetti/cartella-progetti-in-corso/suolo-e-territorio-1/progetto-carg-cartografia-geologica-e-geotematica), in formato vettoriale. Si tratta di dati molto utili e va dato atto al Servizio Geologico e Sismico della Regione Umbria del buon lavoro svolto, visto anche il ritardo di molte altre regioni italiane in quest’ambito.
I dati sono scaricabili dal sito della Regione Umbria e possono essere utilizzati liberamente con l’obbligo di citazione della fonte (licenza [CC BY 3.0 IT](https://creativecommons.org/licenses/by/3.0/it/)).  
Si qui tutto bene, ma il problema piuttosto arduo è **come fare per stilizzarli**.

Si tratta di un compito impegnativo, soprattutto considerando il vettore delle unità cartografabili (formazioni), che comprende ben 216 unità ciascuna con un proprio riempimento e retino.

---

## 🖌️ Gli stili per QGIS

La buona notizia è che possiamo utilizzare i dati geologici tramite il software libero (e gratuito) **QGIS** e gli stili elaborati dal me e scaricabili di seguito.

![esempio di cartogarfia nel programma](/media/images/schermataQGIS.png) _I dati della cartografia geologica vettoriale stilizzati in QGIS._

Dal sito della regione si scarica un file compresso che contiene 13 file vettoriali, in formato “shapefile”. Per adesso ho preparato gli stili dei quattro livelli vettoriali più importanti:

* POLUC – poligoni delle unità cartografabili, che contiene le formazioni;
* LINUC – linee delle unità cartografabili, che contiene i contatti stratigrafici e tettonici;
* PIEG – le pieghe;
* OSS – punti di osservazione, che contiene gli elementi puntuali tra cui le giaciture.

> Gli **stili per QGIS**, dei vettori sopra descritti, sono scaricabili dal link seguente.  
> 🔘  [stili.ultimi.zip](https://github.com/Freddi-kru/Cartografia_geol_UMB/blob/master/stili_ultimi.zip?raw=true)
{: .prompt-info }
---

## 🗃️ Upgrade al GeoPackage

Una volta decompresso il file della regione, si ottiene una cartella con 13 layer vettoriali in formato _shapefile_. Si tratta di uno dei primi formati dati utilizzati nei GIS e, ormai, **è sicuramente datato**.
Ciascun livello vettoriale è costituito da più file: da 3 sino a 8, come in questo caso. Ciò significa che la cartella della “cartografia geologica vettoriale” contiene quasi 100 files.  
Conviene senz'altro passare ad uno standard attuale, come il [GeopPackage](http://www.geopackage.org/).

Una buona descrizione dei vantaggi del formato GeoPackage è stata fatta da [Totò Fiandaca](https://pigrecoinfinito.com/) in questo [articolo](https://pigrecoinfinito.com/2018/04/08/qgis-e-il-formato-geopackage/).
Il GeoPackage è in realtà un contenitore, per cui in un singolo file (.gpkg) è possibile inserire più livelli vettoriali (o raster) e anche i **file di configurazione degli stili**.

Ho preparato un geopackage (carta_geologica_Umbria.gpkg) che contiene tutti i layer vettoriali della cartografia geologica compresi gli “stili” dei quattro vettori sopra descritti.
Una volta caricato uno dei vettori in QGIS (es. POLUC – le formazioni GEOLOGICHE) il software vede che **nel geopackage è presente lo stile e lo applica automaticamente**. 

![gif con stilizzazione automatica del layer POLUC](/media/images/stilizzazione_automatica.gif)
_Caricamento del layer POLUC, dal geopackage, in QGIS. Lo stile è applicato automaticamente dal software._

> La cartografia geologica vettoriale dell’Umbria, in formato GeoPackage (già stilizzata per QGIS), è scaricabile al link seguente.  
> 🔘  [carta_geologica_Umbria.zip](https://www.onegis.it/wp/wp-content/uploads/2019/06/carta_geologica_Umbria.zip)
{: .prompt-info }

Si ribadisce, per doveri di attribuzione, che l’ **autore del database** è il **Servizio Geologico e Sismico della Regione Umbria**.

---
## 🗺️ Descrizione dei dati contenuti nella cartografia vettoriale

Il database geologico contiene 13 layer vettoriali, i cui nomi non sono immediatamente comprensibili: POLUC, LINUC, PIEG, OSS, ma anche POLGM, LINGM, AR, e così via. La pagina internet della Regione Umbria è piuttosto generica e rimanda a:

_Linee guida per l’informatizzazione e per l’allestimento per la stampa dalla banca dati - Quaderno 6” del Servizio Geologico Nazionale (oggi I.S.P.R.A) e sue modificazioni ed integrazioni, nonché nei volumi 1, 2, 3 della III serie degli stessi Quaderni._

In effetti tutte le informazioni sono reperibili tra i documenti linkati alla pagina [Banca Dati Geologica](https://www.isprambiente.gov.it/it/progetti/cartella-progetti-in-corso/suolo-e-territorio-1/progetto-carg-cartografia-geologica-e-geotematica/banca-dati-geologica) del sito dell’ISPRA. Dopo vario scartabellare è possibile descrivere tutti i layer.

### 🔲 Elementi poligonali

* POLUC: unità geologiche, cartografabili – formazioni;
* POLGM: elementi geomorfologici ed antropici, cartografabili – conoidi alluvionali, deformazioni gravitative superficiali;
* AR: limiti delle Carte Tecniche Regionali.

### 〰️ Elementi lineari

* LINUC: unità geologiche lineari, cartografabili – contatti stratigrafici e contatti tettonici;
* LINGM: elementi lineari geomorfologici ed antropici, cartografabili – cordoni morenici terminali o laterali, crinali affilati, isopieziometriche, orli di scarpata, orli di scarpata di frana, orli di terrazzo, tracce di alveo fluviale abbandonato;
* ISOL: isocronopache – sismica, solo sul Lago Trasimeno;
* SIMUC: livelli guida;
* TRAC: tracciati geologici e geofisici – tracce di log stratigrafico, tracce di sequenza campionata, tracce di sezione geologica.

### ▪️ Elementi puntuali

* OSS: punti di osservazione. In questo caso è possibile capire il contenuto solo in base al codice numerico, il significato del codice non è esplicitato nella tabella attributi – 1110 = località fossilifera, 1220 = slumping intraformazionale non cartografabile, 3100 = superficie di origine primaria, 3120 = stratificazione verticale, 3130 = stratificazione rovesciata, 3140 = stratificazione contorta con valori medi di immersione ed inclinazione, 3150 = stratificazione a polarità sconosciuta, 3210 = superficie di clivaggio o scistosità inclinata, 3300 = elementi lineari primari e lineazioni, 3311 = elemento lineare primario con direzione e verso (struttura sedimentaria, direzione di flusso in rocce ignee), 3330 = specchio di faglia inclinato, 3410 = asse di piega simmetrica, 3440 = associazione di pieghe minori;
* PUNGM: elementi puntuali geomorfologici ed antropici, cartografabili – centri vulcanici, mancante, picchi isolati o cucuzzoli, piccole frane o gruppo di piccole frane non cartografabili, principali cavità ipogee;
* RIS: risorse e prospezioni – cave attive, cave inattive, miniere attive, miniere inattive, pozzi per acqua, pozzi per ricerca mineraria, sondaggi esplorativi o prove penetrometriche, sorgenti, sorgenti termominerali;
* CAM: campioni geologici.

---

**Il lavoro non è completato, man mano che aggiungeremo nuovi stili la pagina sarà aggiornata - Restate collegati!** 
