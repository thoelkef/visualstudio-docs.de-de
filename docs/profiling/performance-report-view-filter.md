---
title: "Filter f&#252;r die Berichtsansicht der Profilerstellungstools | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Profilerstellungstools, Filter für die Profiler-Berichtsansicht"
  - "Filter für die Profiler-Berichtsansicht, Profilerstellungstools"
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Filter f&#252;r die Berichtsansicht der Profilerstellungstools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Fenster Filter für die Profiler\-Berichtsansicht befindet sich am oberen Rand des Fensters Leistungsbericht.  Wenn es nicht angezeigt wird, klicken Sie auf die Schaltfläche **Filter anzeigen**.  
  
 Sie können jede Filterklausel ändern, um die Ergebnisse zu optimieren.  Die folgenden Spalten sind im Filter\-Generator verfügbar.  
  
|Filterelement|**Beschreibung**|  
|-------------------|----------------------|  
|Und\/Oder|Wählen Sie **Und** aus, wenn diese Klausel und die nächste Klausel beide den Wert true haben müssen, um zu einer Übereinstimmung zu führen.  Wählen Sie **Oder** aus, wenn diese Klausel oder die nächste Klausel den Wert true haben kann, um zu einer Übereinstimmung zu führen.|  
|Feld|Wählen Sie das Feld, das in der Filterklausel verwendet werden soll, aus der Liste der Datenfelder aus, die in der aktuellen Berichtsdatei verfügbar sind.|  
|Operator|Wählen Sie den Operator aus, der die Beziehung angibt, die Sie zwischen dem Feld und dem Wert herstellen möchten.<br /><br /> \=    Gleich<br /><br /> \<\>  Ungleich<br /><br /> \<    Kleiner als<br /><br /> \>    Größer als<br /><br /> \<\=  Kleiner oder gleich<br /><br /> \>\=  Größer oder gleich|  
|Wert|Wählen Sie den Wert aus, nach dem gesucht werden soll, oder geben Sie den Wert ein.  In einigen Feldern werden die verfügbaren Werte für das Feld aufgeführt.|  
  
 Sie können Filterklauseln hinzufügen, bis Sie das Gefühl haben, dass der Filter die besten Ergebnisse ausgibt.  Klicken Sie auf **Filter ausführen**, um den Filter auf die Datendatei anzuwenden.  
  
 In der Berichtansicht **Markierungen** können Sie Filterklauseln generieren, um die Daten in den Berichtansichten auf die zwischen zwei Markierungen erfassten Daten zu beschränken.  Wählen Sie die Markierungen aus, an denen Berichtsdaten beginnen und enden sollen, klicken Sie mit der rechten Maustaste, und wählen Sie entweder **Filter für Markierungen hinzufügen** oder **Filter für Timestamps hinzufügen** aus.  Beide Filter beschränken die aktuelle Datendatei auf denselben Zeitraum. **Filter für Markierungen hinzufügen** kann auf andere VSP\-Dateien angewendet werden.  
  
 Um den Filter zu speichern, klicken Sie in der Symbolleiste des Leistungsberichts auf **Filter exportieren**, und geben Sie dann einen Speicherort und Dateinamen für die VSPF\-Datei an.  Um einen zuvor gespeicherten Filter zu laden, klicken Sie auf **Filter importieren**, und suchen Sie die gespeicherte Filterdatei.  Filterdateien können auch verwendet werden, um Datendateien auf Computern zu filtern, auf denen die eigenständigen Profilerstellungstools installiert sind.  Weitere Informationen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).  
  
## Siehe auch  
 [Analysieren der durch Profilerstellungstools erstellten Daten](../profiling/analyzing-performance-tools-data.md)   
 [VSPerfReport](../profiling/vsperfreport.md)