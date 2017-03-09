---
title: "Erweiterte Einstellungen (Dialogfeld) (Parallelit&#228;tsschnellansicht) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.settings"
ms.assetid: bb3d90aa-5f08-4953-9be0-be6cea11633d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erweiterte Einstellungen (Dialogfeld) (Parallelit&#228;tsschnellansicht)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im Dialogfeld **Erweiterte Einstellungen** in der Parallelitätsschnellansicht verwenden, können Sie steuern, z Ablaufverfolgungen erfasst werden.  Das Dialogfeld verfügt über Registerkarten für Symbole, Nur mein Code, Pufferung, Filtern, CLR\-Ereignisse, Markierung, Anbieter und Dateien.  
  
## "Symbols"  
 Die Parallelitätsschnellansicht verwendet dieselben Symboleinstellungen wie der Visual Studio\-Debugger.  Die Parallelitätsschnellansicht Einstellungen verwendet, um mit Aufruflisten aufzulösen, die Leistungsdaten zugeordnet werden.  Wenn sie Prozess Ablaufverfolgungen, die Parallelitätsschnellansicht auf die Symbolserver zugreift, die auf der Seite "Einstellungen" angegeben werden.  Wenn auf diese Daten zu einem Netzwerk zugegriffen werden, kann das Ablaufverfolgungsverarbeiten.  Um die Zeitdauer zu reduzieren die erforderlich ist Symbole zu beheben, können Sie Symbole lokal zwischengespeichert.  Wenn Symbole heruntergeladen wurden, lädt Visual Studio sie vom lokalen Cache.  
  
## Nur eigenen Code  
 Standardmäßig momentan mein Code der EXE\- und DLL\-Dateien, die mit der aktuellen Projektmappe in Visual Studio zugeordnet werden.  Die Parallelitätsschnellansicht wird diesen Satz Dateien aus, wenn das gerechte My Codefunktion verwenden, um zu Aufruflisten filtern.  Klicken Sie im gerechten My Coderegisterkarte, können Verzeichnisse hinzufügen, die EXE\- und DLL\-Dateien zu Stellen enthalten, die die Parallelitätsschnellansicht für Nur mein Code.  
  
 Die Pfade des der EXE\- und DLL\-Dateien werden Ablaufverfolgungsdatei in der gespeichert, wenn die Ablaufverfolgung wird erfasst.  Das Ändern dieser Einstellung wirkt sich keine zuvor aufgelisteten Ablaufverfolgungen.  
  
## Buffering  
 Die Parallelitätsschnellansicht verwendet Ereignisablaufverfolgung für Windows \(ETW\) wenn eine Ablaufverfolgung erfasst.  ETW verwendet verschiedene Puffer, das Ereignisse speichert.  Puffereinstellungen Die standardmäßigen ETW sind möglicherweise nicht in allen Fällen optimal, und in einigen Fällen, könnte Probleme wie verlorene Ereignisse verursachen.  Sie können die Pufferungsregisterkarte verwenden, um ETW\-Puffereinstellungen zu konfigurieren.  Weitere Informationen finden Sie und [Ereignisablaufverfolgung](http://go.microsoft.com/fwlink/?LinkId=234579) [EVENT\_TRACE\_PROPERTIES\-Struktur](http://go.microsoft.com/fwlink/?LinkId=234580).  
  
## Filter  
 Auf der Filterregisterkarte können Sie den Satz von Ereignissen aktivieren, die die Parallelitätsschnellansicht erfasst.  Eine Teilmenge Ereignisse auswählen, schränkt die Typen von Daten, die in Berichten angezeigt werden, wird die Größe der Ablaufverfolgung und reduziert die Uhrzeit ein, die den Prozess Ablaufverfolgungen benötigt wird.  
  
### CLR\-Ereignisse  
 Die Ereignisse, die durch Common Language Runtime \(CLR\) generiert werden, aktivieren die Parallelitätsschnellansicht, um verwalteten Aufruflisten aufzulösen.  Wenn Sie Auflistung CLR\-Ereignisse deaktivieren, wird die Ablaufverfolgungsgröße reduziert, aber mehrere Aufruflisten lösen nicht auf.  Dadurch würde etwa CPU\-Threadaktivität falsch kategorisiert werden.  
  
### Für systemeigene Prozesse auflisten  
 CLR\-Ereignisse Standardmäßig werden nur erfasst, wenn ein verwalteter Prozess ein Profil erstellt wird, weil sie normalerweise für systemeigene Prozesse nicht erforderlich sind.  In einigen Fällen \(beispielsweise, wenn ein systemeigener Prozess die CLR hostet\), müssen Sie möglicherweise einen systemeigener Prozess für CLR\-Ereignisse sammeln.  Wenn dies der Fall ist, aktivieren Sie das Kontrollkästchen **Für systemeigene Prozesse auflisten**.  
  
### Rundown\-Ereignisse deaktivieren  
 Die CLR generiert Ereignisse von zwei Anbieter: Laufzeit und Rundown.  Wenn Sie CLR\-Ablaufereignisse sammeln möchten, aber Rundownereignisse, sammeln vermeiden möchten, aktivieren Sie das Kontrollkästchen **Rundown\-Ereignisse deaktivieren**.  Dadurch wird die Größe der Ablaufverfolgungsdatei, durch die Auflistung generiert wird, jedoch einige Stapel wurde möglicherweise nicht auf.  Weitere Informationen finden Sie unter [CLR ETW Providers](../Topic/CLR%20ETW%20Providers.md)  
  
### Samplingereignisse  
 Sie können Samplingereignisse verwenden, um zu Aufruflisten sammeln, die mit Threadausführung zugeordnet werden.  Diese Ereignisse werden etwa einmal pro Millisekunde für Threads erfasst, die im aktuellen Prozess ausführen.  Wenn Sie die Auflistung von Samplingereignissen deaktivieren, wird die Größe der erfassten Ablaufverfolgung reduziert, aber keine mit Aufruflisten anzeigen, die Threadausführung zugeordnet werden.  
  
### GPU\-Ereignisse  
 GPU\-Ereignisse sind die Ereignisse, die von DirectX generiert werden.  Wenn Sie die Auflistung von GPU\-Ereignissen deaktivieren, wird die Größe der erfassten Ablaufverfolgung reduziert, aber keine GPU\-Aktivität in der Auslastungsansicht oder DirectX\-Modulaktivität in der Threadansicht anzeigen.  
  
### Datei\-E\/A\-Ereignisse  
 Datei\-E\/A\-Ereignisse stellen auf dem Datenträger im Namen des Stromprozesses dar.  Wenn Sie Datei\-E\/A\-Ereignisse deaktivieren, wird die Größe der Ablaufverfolgung reduziert, aber die Threadansicht meldet keine Informationen über Datenträger\-Vorgänge Datenträgerchannels oder.  
  
## Markers  
 Auf den Markierungen Registerkarte, können Sie den Satz von ETW\-Anbietern konfigurieren, die als Markierung in der Parallelitätsschnellansicht angezeigt werden.  Sie können die Markerauflistung auf Grundlage Wichtigkeitsstufe und ETW\-Kategorie auch filtern.  Wenn Sie [Parallelitätsschnellansichts\-SDK](../profiling/concurrency-visualizer-sdk.md) verwenden und eigene Markeranbieter verwenden, können Sie diesen hier registrieren, damit er in der Threadansicht wird.  
  
### Hinzufügen eines neuen Anbieter  
 Wenn der Code unter [Parallelitätsschnellansichts\-SDK](../profiling/concurrency-visualizer-sdk.md) oder ETW\-Ereignisse generiert, die der <xref:System.Diagnostics.Tracing.EventSource> \- Konvention folgen, können Sie diese Ereignisse in der Parallelitätsschnellansicht anzeigen, indem Sie sie in diesem Dialogfeld registrieren.  
  
 Auf Namensfeld geben Sie einen Namen ein, der die Typen von Ereignissen beschreibt, die vom Anbieter generiert werden.  Klicken Sie im GUID\-Gebiet geben Sie die GUID ein, die mit diesem Anbieter zugeordnet ist. \(Eine GUID wird mit jedem ETW\-Anbieter zugeordnet.\)  
  
 Optional können Sie angeben, ob Ereignisse dieses Anbieters, basierend auf der Kategorie oder Wichtigkeitsstufe herausfiltert.  Sie können das Feld Category verwenden, um auf Grundlage der Parallelitätsschnellansicht SDK\-Kategorien zu filtern.  Hierzu, geben Sie eine durch Trennzeichen getrennte Zeichenfolge von Kategorien oder Bereichen von Kategorien ein.  Dies gibt die Kategorien der Ereignisse im aktuellen Anbieter, um darzustellen.  Wenn Sie einem <xref:System.Diagnostics.Tracing.EventSource> Anbieter hinzufügen, können Sie das Feld Category verwenden, um durch ETW\-Schlüsselwort zu filtern.  Da das Schlüsselwort eine Bitmaske ist, können Sie eine durch Trennzeichen getrennte Zeichenfolge von ganzen Zahlen verwenden, um anzugeben, die Bits in der Maske gesetzt werden.  Durch "1,2 " legt die erste und zweite Bits festgelegt, und dieses übersetzt bis 6 im Dezimal\-.  
  
 Sie können die Wichtigkeitsstufenliste verwenden, um Ereignisse, die eine Bedeutung oder ETW\-Ebene, die kleiner haben, als der angegebene Wert ist herauszufiltern.  
  
### Konfigurieren eines vorhandenen Anbieters  
 Um Einstellungen bearbeiten die einem vorhandenen Anbieter zugeordnet werden, wählen Sie diesen in der Liste aus, und wählen Sie dann die Schaltfläche **Anbieter bearbeiten** aus.  Sie können den Namen, die GUID und die Filterungseinstellungen ändern.  
  
### Filter\-Marker\-Daten aus Nebenläufigkeitsschnellansichts\-Berichten Auschecken  
 Wenn Sie keine Daten sollen, damit ein bestimmter Anbieter in zukünftigen Ablaufverfolgungen wird, deaktivieren Sie das Kontrollkästchen neben dem Anbieter, die Sie entfernen möchten.  
  
## Dateien  
 Auf der Registerkarte **Dateien** Sie können das Verzeichnis angeben, unter dem Ablaufverfolgungsdateien jedes Mal eine Ablaufverfolgung erfasst gespeichert werden.  Die Parallelitätsschnellansicht generiert vier Dateien für jede Ablaufverfolgung, die sie erfasst:  
  
-   Eine Kernelmodusereignisablaufverfolgungsprotokoll\-\(ETL\)\- Datei \(\*.kernel.etl\)  
  
-   Eine Benutzermodusereignisablaufverfolgungsprotokolldatei \(\*.user.etl\)  
  
-   Eine Nebenläufigkeitsschnellansichts\-Datendatei \(\*.CVData\)  
  
-   Eine Nebenläufigkeitsschnellansichts\-Ablaufverfolgungsdatei \(\*.CVTrace\)  
  
 Die ETL\-Dateien zwei speichern die unformatierten Ablaufverfolgungsdaten, und die beiden Nebenläufigkeitsschnellansichtsdateien speichern den verarbeiteten Daten.  Die ETL\-Dateien unformatierten werden in der Regel nicht verwendet, nachdem eine Ablaufverfolgung verarbeitet wird.  Das Das Kontrollkästchen aktivieren **Ereignisablaufverfolgungs\-Protokolldateien \(Event Trace Log, ETL\) nach der Analyse löschen** reduziert die Menge der Ablaufverfolgungsdaten, die auf dem Datenträger gespeichert wird.  
  
## Siehe auch  
 [Nur mein Code](../profiling/just-my-code-threads-view.md)   
 [Parallelitätsschnellansichtsmarker](../profiling/concurrency-visualizer-markers.md)