---
title: "Filtern von Berichtsansichten der Profilerstellungstools | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Profilerstellungstools, Konfigurieren"
ms.assetid: 820cf192-7fd6-4bee-9a51-aa69154aca85
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Filtern von Berichtsansichten der Profilerstellungstools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Profilerstellungs\-Datendateien filtern, um die in den Leistungsberichtansichten angezeigten und in Berichtsdateien exportierten Profilerstellungsdaten einzuschränken.  Sie können einen Bericht auf die Daten zwischen Zeitstempelwerten einschränken, Sie können die Daten aber auch auf bestimmte Prozesse und Threads einschränken.  Sie können Filter in einer Datei speichern und dann durch Importieren des gespeicherten Filters einen Filter für eine andere Profilerstellungs\-Datendatei erstellen.  
  
 Mithilfe der grafischen Zeitachse in der Zusammenfassungsansicht können Sie einen Bericht auch auf ein Zeitsegment beschränken.  Siehe [Gewusst wie: Filtern von Berichtsansichten aus der Zeitachsenübersicht](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
 Wenn Sie System\- und Drittanbietercode aus einem Bericht ausschließen möchten, finden Sie entsprechende Informationen unter [Gewusst wie: Filtern der Berichtsansichten, um nur eigenen Code anzuzeigen](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)  
  
## Prozeduren  
  
#### So erstellen Sie einen Profilerberichtsfilter  
  
1.  Wenn das Fenster Filter für die Leistungsbericht\-Ansicht nicht angezeigt wird, klicken Sie auf der Symbolleiste Leistungsberichtansicht auf **Filter anzeigen**.  
  
     Der Filter für die Leistungsbericht\-Ansicht ist eine Tabelle.  Jede Zeile der Tabelle stellt eine Klausel des Filters dar.  Sie können einem Filter beliebig viele Klauseln hinzufügen.  
  
2.  Für jede Klausel, die Sie einem Filter hinzufügen möchten, wählen Sie Werte in den folgenden Feldern einer Zeile aus oder geben diese ein.  
  
    |Feld|**Beschreibung**|  
    |----------|----------------------|  
    |**Und\/Oder**|Wählen Sie **Und** aus, wenn diese Klausel und die nächste Klausel beide den Wert true haben müssen, um zu einer Übereinstimmung zu führen.  Wählen Sie **Oder** aus, wenn diese Klausel oder die nächste Klausel den Wert true haben kann, um zu einer Übereinstimmung zu führen.|  
    |**Feld**|Wählen Sie das in der Filterklausel zu verwendende Berichtsfeld in der angezeigten Liste der Datenfelder aus.|  
    |**Operator**|Wählen Sie den Operator aus, der die Beziehung angibt, die Sie in der Klausel zwischen dem Feld und dem Wert herstellen möchten.<br /><br /> \=    Gleich<br /><br /> \<\>  Ungleich<br /><br /> \<    Kleiner als<br /><br /> \>    Größer als<br /><br /> \<\=  Kleiner oder gleich<br /><br /> \>\=  Größer oder gleich|  
    |**Wert**|Wählen Sie den Wert aus, nach dem gesucht werden soll, oder geben Sie den Wert ein.  In einigen Feldern werden die verfügbaren Werte für das Feld aufgeführt.|  
  
#### So erstellen Sie in der Ansicht für Markierungsberichte einen Profilerberichtsfilter  
  
1.  Wählen Sie auf der Symbolleiste Leistungsberichtansicht in der Liste **Aktuelle Ansicht** den Eintrag **Markierungen** aus.  
  
     Der Profilerbericht Markierungen wird angezeigt.  
  
2.  Wählen Sie das ETW\- oder Samplingereignis aus, die Sie als Ausgangspunkt des Berichts verwenden möchten.  
  
3.  Halten Sie STRG gedrückt, und klicken Sie auf das Ereignis, das Sie als Endpunkt des Berichts verwenden möchten.  
  
4.  Klicken Sie mit der rechten Maustaste, und wählen Sie eine der folgenden Optionen aus:  
  
    -   Mit **Filter für Markierungen hinzufügen** erstellen Sie Filterklauseln, in denen die Spalte "Markierung" als Filterfeld verwendet wird.  
  
    -   Mit **Filter für Timestamps hinzufügen** erstellen Sie Filterklauseln, in denen die Spalte Timestamp in Millisekunden als Filterfeld verwendet wird.  
  
     Mit den beiden Optionen filtern Sie die aktuelle Datendatei an den gleichen Ausgangs\- und Endpunkten.  Wenn Sie den Filter zur Verwendung in anderen Berichten exportieren, können sich beide Optionen besser eignen.  
  
#### So laden Sie einen vorhandenen Filter aus einer Datei  
  
1.  Klicken Sie auf der Symbolleiste Leistungsberichtansicht auf **Filter importieren**.  
  
     Das Dialogfeld **Filter laden** wird angezeigt.  
  
2.  Geben Sie den Speicherort und den Dateinamen der zu ladenden Filterdatei \(.vspf\) an.  
  
#### So führen Sie einen Filter aus  
  
-   Klicken Sie auf der Symbolleiste Leistungsberichtansicht auf **Filter ausführen**.  
  
#### So beenden Sie einen Filter, dessen Ausführung zu lange dauert  
  
-   Klicken Sie auf der Symbolleiste Leistungsberichtansicht auf **Filter beenden**.  
  
#### So entfernen Sie einen Filter aus einer Berichtsansicht  
  
1.  Löschen Sie die Klauselzeilen im Filter für die Leistungsbericht\-Ansicht.  
  
2.  Klicken Sie auf der Symbolleiste Leistungsberichtansicht auf **Filter ausführen**.  
  
#### So speichern Sie einen Filter in einer Datei  
  
1.  Klicken Sie auf der Symbolleiste Leistungsberichtansicht auf **Filter exportieren**.  
  
     Das Dialogfeld **Filter speichern** wird angezeigt.  
  
2.  Geben Sie den Speicherort und den Dateinamen der zu speichernden Filterdatei \(.vspf\) an.  
  
## Siehe auch  
 [Anpassen von Berichtsansichten der Profilerstellungstools](../profiling/customizing-performance-tools-report-views.md)