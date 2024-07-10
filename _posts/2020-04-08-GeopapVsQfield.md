---
title: QField vs Geopaparazzi
description: QField vs Geopaparazzi, qual'è la migliore app opensource per il rilievo in campo?
author: pierlu
date: 2020-04-08 13:00:00 +0000
categories: [Generale, Rilevamento sul terreno]
tags: [rilevamento, Qfield, Geopaparazzi, versus]     # TAG names should always be lowercase
pin: false
math: true
mermaid: true
image:
  path: https://i.postimg.cc/yYwvPHV0/QField-contro-Geopaparazzi-1.gif
  
---
  



## Breve descrizione delle due applicazioni


### Geopaparazzi


![Geopaparazzi Dashboard](https://i0.wp.com/www.onegis.it/wp/wp-content/uploads/2020/04/00_dashboard1556445307534926501.png?resize=640%2C1138&ssl=1){: width="768" height="1365" .w-50 .left}

[Geopaparazzi](https://www.geopaparazzi.org/#/) è una applicazione, scritta in Java, che non nasce direttamente collegata ad uno specifico Desktop GIS anche se adesso è molto ben integrata con [GvSig](http://www.gvsig.com/it/prodotti/gvsig-desktop)
 per il quale esiste una specifica estensione finalizzata alla preparazione dei dati e dei form per l’inserimento dei dati.

Geopaparazzi funziona similmente ad un GIS ovvero è possibile caricare sul nostro device (tablet o cellulare) una serie di dati geografici sia in formato raster che vettoriale. Per i raster il formato principale è MBtiles mentre per i vettoriali è lo spatialite.

Oltre ai dati cartografici che si possono utilizzare come sfondo i vettoriali sono ovviamente interrogabili, stilizzabili direttamente dall’applicazione, etichettabili, e gestibili in modo semplice attraverso apposite checkbox (spunte).

Già da qualche versione inoltre geopaparazzi ha aggiunto la possibilità di editare i layer puntuali e poligonali. L’editing dei poligoni è relativamente semplice quando si deve creare un nuovo poligono potendo anche aggiungere un vertice del poligono corrispondente alla posizione GPS. Più articolata invece risulta la modifica. Nel caso infatti si voglia fare un reshape (modifica della forma) si deve seguire una strada con una logica diversa rispetto a quanto accade in un classico GIS dove si attivano i vertici e l’utente può interagire con essi. In Geopaparazzi è necessario creare un nuovo poligono sovrapposto a quello che si vuole modificare e poi operare una sottrazione oppure una unione a seconda della necessità.

La parte sicuramente interessante di Gepaparazzi è la possibilità di raccogliere dati in campo. Ha la possibilità di creare dei form altamente personalizzati (maschere di inserimento) che sono configurabili attraverso un file di testo in formato json. Ogni elemento rilevato corrisponde ad un punto che viene salvato nel progetto corrente.

Geopaparazzi, all’avvio, chiede di creare un progetto che ha estensione .gpap che altro non è che un db sqlite che contiene tutti i dati rilevati oltre che le foto che sono state scattate. Le foto sono scattate con l’applicazione predefinita del telefono alla massima risoluzione possibile e salvate come blob nel file .gpap. Al termine del rilievo quindi tutto il rilievo è salvato in un unico file .gpap che poi deve essere gestito nel proprio Desktop GIS preferito.

In GvSig esiste una [specifica estensione](http://www.hortonmachine.org/hydrologis4gvsig_quickstart/hydrologis4gvsig_quickstart.html)
 che prende in input il file gpap e lo trasforma in layer geografici vettoriali in formato shapefile.

La mia esperienza con [QGIS](https://www.geopaparazzi.org/v600/index.html#_viewing_data_in_qgis_3)
 è stata altrettanto positiva, grazie al [plugin Io Geopaparazzi](https://github.com/eachiaradia/IOGeopaparazzi), attraverso il quale è possibile importare anche direttamente il file .gpap e trasformarlo in layer.

Per i mappers OSM può essere utile saper che ho utilizzato molto Geopaparazzi per mappare elementi da inserire in [openstreetmap](http://openstreetmap.org)
 con form personalizzati. Di recente ho scoperto questo [servizio online di conversione del file](https://gpapconv.frafra.eu/)
 .gpap per produrre direttamente l”xml da inserire in JOSM.
 
### QField


![Qfield dashboard](https://i0.wp.com/www.onegis.it/wp/wp-content/uploads/2020/04/user-guide_identify-feature.png?resize=288%2C512&ssl=1){: width="768" height="1365" .w-50 .right}

[QField](https://qfield.org/) è una applicazione che nasce con una filosofia diversa rispetto a Geopaparazzi ovvero si tratta di una app pensata per portare QGIS con tutte le sue specifiche in campo su dispositivo portatile (cellulare o tablet).

La totalità del lavoro per preparare i dati da visualizzare sul dispositivo e per preparare i dati da compilare in campo si fanno in QGIS. E’ stato poi sviluppato un apposito plugin che prepara una cartella specifica di tutto il materiale da copiare nel dispositivo.

La nuova versione di QField (oggi arrivata alla 1.4) ha una interfaccia di navigazione molto migliorata. E’ possibile copiare la cartella in qualsiasi memoria (interna che esterna). Una volta aperta la cartella da QField avete una visione semplificata del vostro progetto sul dispositivo.

Le cose che potete fare da dentro QField sono ridotte rispetto a Geopaparazzi, ad esempio non potete scegliere di etichettare una layer o cambiare colore ad una linea se non lo avete già predisposto in QGIS. Questo però non è da intendersi come una limitazione ma piuttosto una scelta dove si limita al campo solo la fase di raccolta/inserimento.

In QField è possibile non solo inserire dati puntuali come accade in Geopaparazzi ma anche dati poligonali e lineare. La digitalizzazione di elementi poligonali e lineari è, a mio parere, migliore che in geopaparazzi sopratutto nella fase di modifica.

Nell’ultima versione (la 1.4) è stata finalmente migliorata l’ultima cosa che secondo me metteva un gradino sotto QField. Adesso è possibile utilizzare la applicazione di fotocamera integrata in modo da avere foto di massima qualità. In passato si usava una applicazione di terze parti che faceva foto molto al di sotto delle potenzialità del proprio cellulare.

QFiled quindi è pensato proprio per chi utilizza QGIS come desktop GIS principale e presuppone una buona capacità di utilizzo del software, dei dati, della preparazione del progetto e dell’uso dei widget per l’editing dei dati. Infatti anche in QField è possibile personalizzare i form di inserimento passando però per i widget che sono già presenti in QGIS. I risultati che si raggiungono sono molto buoni e paragonabili in qualità a quelli di Geopaparazzi.

Una volta eseguito il rilievo basta importare sul Desktop PC la cartella dal proprio dispositivo ed il plugin [QFieldSync](https://qfield.org/docs/qfieldsync/)
 esegue la sincronizzazione per voi in odo efficiente è semplice.

---

## Il Confronto


| Geopaparazzi | Caratteristica | QField |
| --- | --- | --- |
| si  | MBtiles | si  |
| si  | spatialite | si  |
| si  | geopackage | si  |
| no  | shapefile | si  |
| si  | WMS | si  |
| si  | TMS | si  |
| no  | Postgis |     |
| si  | editing di punti | si  |
| si  | editing di poligoni | si (migliore) |
| no  | editing di linee | si  |
| si  | Foto con app interna | si  |
| si  | personalizzazioni dello stile da app. | no (per scelta) |
| si (con plugin) | Integrazione con QGIS | si (migliore) |
| si (GvSig) | Integrazione con altri GIS | no  |
| si  | registrazione azimuth foto | no  |
| si  | registrazione punto di scatto e quota | si  |
| si (PDF) | Esportazione nell’app del rilievo | no  |
| si ([guida](https://www.openstreetmap.org/user/Cascafico/diary/391537)) | Esportazione in OSM | no (si usa QGIS) |

## Conclusioni

 
Non è facile scegliere quale è la migliore app tra queste due. Nascono con filosofie differenti ed in sostanza QField è strettamente legata a QGIS, come un figlio minore per dispositivo mobile. Quindi la conclusione è ad ognuno il suo. Se si ha praticità con QGIS e già lo si usa per il proprio lavoro allora QField può essere la scelta giusta. Se usate altri Desktop GIS allora forse è meglio Geopaparazzi in quanto è più facile preparare i dati da portare in campo e poi molte delle personalizzazione si fanno direttamente dentro l’applicazione.

#### Allora QField vs Geopaparazzi chi vince?  
Io personalmente non ho una predilezione per l’uno o per l’altro. Mi baso su l’uno o l’altro a seconda dei casi. Se per esempio ho già un progetto QGIS pronto e devo raccogliere dati in campagna allora scelgo QField. Se ad esempio necessito dell’informazione della direzione di scatto di una foto allora vado su Geopaparazzi perchè QField non è in grado di leggerla direttamente dall’exif della foto. Ovviamente è possibile arrivarci ad essa anche da QField e QGIS con un workaround. Se siete arrivati fino a qui allora vuol dire che questo articolo vi è piaciuto e vi prego di lasciarmi un like e magari di prendere visione della nostra pagina in cui abbiamo pensato ad un [corso](https://www.onegis.it/corsi/)
 di [rilievo digitale in campo](https://www.onegis.it/corsi/corso-rilievo-digitale-campo-geopaparazzi/). 
