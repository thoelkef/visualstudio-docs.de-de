---
title: "Visualisieren von EventSource-Ereignissen als Marker | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Visualisieren von EventSource-Ereignissen als Marker
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Parallelitätsschnellansicht kann EventSource\-Ereignisse als Markierung anzeigen, und Sie können steuern, wie die Markierung angezeigt werden.  Um die EventSource\-Marker anzuzeigen, registrieren Sie die ETW\-Anbieter GUID indem Sie das Dialogfeld [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) verwenden.  Die Parallelitätsschnellansicht hat die Standardkonventionen, um von EventSource\-Ereignissen als [Flag\-Marker](../profiling/flag-markers.md), [Bereichsmarker](../profiling/span-markers.md) und [Meldungsmarker](../profiling/message-markers.md).  Sie können anpassen, wie EventSource\-Ereignisse angezeigt werden, indem benutzerdefinierte Felder an Ereignisse hinzufügen.  Weitere Informationen zur Markierung, finden Sie unter [Parallelitätsschnellansichtsmarker](../profiling/concurrency-visualizer-markers.md).  Weitere Informationen über EventSource\-Ereignisse, finden Sie unter <xref:System.Diagnostics.Tracing>.  
  
## Angenommen Visualisierung von EventSource\-Ereignissen den Standardwert an  
 Standardmäßig verwendet die Parallelitätsschnellansicht die folgenden Konventionen, um EventSource\-Ereignisse darzustellen.  
  
### Markertyp  
  
1.  Ereignisse, die [Opcode](http://msdn.microsoft.com/de-de/d97953df-669b-4c55-b1a8-925022b339b7) Gewinn haben: Anfang oder Gewinn: Beenden Sie behandelt werden als Anfang oder das Ende einer Spanne, bzw. auf.  Geschachtelte oder überlappende Spannen können nicht angezeigt werden.  Ereignispaare, die an einen Thread an und Ende an anderen starten, können nicht angezeigt werden.  
  
2.  Ein Ereignis, dessen Opcode weder win:Start noch win:Stop ist, wird als Markerflag behandelt, es sei denn, dass der [Ebene](http://msdn.microsoft.com/de-de/dfa4e0a9-4d89-4f50-aef9-1dae0dc11726) \(Feld aus EVENT\_RECORD.EVENT\_HEADER.EVENT\_DESCRIPTOR\) Gewinn ist: Ausführlich oder höher.  
  
3.  In allen anderen Fällen wird das Ereignis als Meldung behandelt.  
  
### Wichtigkeit  
 In der folgenden Tabelle definiert wie die auf Designebene Zuordnungen des Ereignisses für die Markerbedeutung.  
  
|ETW\-Ebene|Nebenläufigkeitsschnellansichts\-Bedeutung|  
|----------------|------------------------------------------------|  
|win:LogAlways|Normal|  
|win:Critical|Kritisch|  
|win:Error|Kritisch|  
|win:Warning|Hoch|  
|win:Informational|Normal|  
|win:Verbose|Niedrig|  
|Größer als win:verbose|Niedrig|  
  
### Reihen\-Name  
 Der Aufgabenname des Ereignisses wird für den Reihennamen verwendet.  Reihe benennt ist leer, wenn keine Aufgabe für das Ereignis definiert wurde.  
  
### Kategorie \(Category\)  
 Wenn die Ebene win:Critical oder win:Errorist, ist die Kategorie wachsam \(\- 1\).  Andernfalls wird die Kategorie der Standardwert \(0\).  
  
### Text  
 Wenn eine Nachricht des PrintfTypformatierten Text für das Ereignis definiert wurde, wird diese Beschreibung des Markers angezeigt.  Andernfalls stellt die Beschreibung der Name des Ereignisses und des Werts jedes Nutzlastfelds.  
  
## Anpassen von Visualisierung von EventSource\-Ereignissen  
 Sie können, wie EventSource\-Ereignisse indem angezeigt werden, die entsprechenden Felder dem Ereignis hinzugefügt, wie in den folgenden Abschnitten beschrieben anpassen.  
  
### Markertyp  
 Verwenden Sie das `cvType` Feld, ein Byte, dass die Art des Markers zu steuern, der verwendet wird, um das Ereignis darstellt.  Nachstehend sind die verfügbaren Werte für cvType:  
  
|cvType Wert|Resultierender Marker\-Typ|  
|-----------------|--------------------------------|  
|0|Meldung|  
|1|Spannen\-Anfang|  
|2|Spannen\-Ende|  
|3|Flag|  
|Alle anderen Werte|Meldung|  
  
### Wichtigkeit  
 Sie können das `cvImportance` Feld, ein Byte verwenden, um die Bedeutung zu steuern, die für ein EventSource\-Ereignis festlegt.  Es wird jedoch empfohlen, die angezeigte Bedeutung eines Ereignisses steuern, indem Sie seine Ebene verwenden.  
  
|cvImportance Wert|Nebenläufigkeitsschnellansichts\-Bedeutung|  
|-----------------------|------------------------------------------------|  
|0|Normal|  
|1|Kritisch|  
|2|Hoch|  
|3|Hoch|  
|4|Normal|  
|5|Niedrig|  
|Alle anderen Werte|Niedrig|  
  
### Reihen\-Name  
 Verwenden Sie das `cvSeries`\-Ereignisfeld, eine Zeichenfolge, die den Reihennamen zu steuern, den die Parallelitätsschnellansicht zu einem EventSource\-Ereignis gibt.  
  
### Kategorie \(Category\)  
 Verwenden Sie das `cvCategory` Feld, ein Byte, um die Kategorie zu steuern, die die Parallelitätsschnellansicht zu einem EventSource\-Ereignis gibt.  
  
### Text  
 Verwenden Sie das `cvTextW` Feld, eine Zeichenfolge, um die Beschreibung zu steuern, die die Parallelitätsschnellansicht zu einem EventSource\-Ereignis gibt.  
  
### SpanID  
 Verwenden Sie das cvSpanId Feld, int, zu den Abgleichungspaaren Ereignissen.  Der Wert für jedes Paar Start\/Endereignisse, die eine Spanne darstellen, muss eindeutig sein.  In der Regel für parallelen Code, erfordert jedoch die Verwendung von Synchronisierungsprimitiven wie <xref:System.Threading.Interlocked.Exchange%2A>, um sicherzustellen, dass der Schlüssel \(der Wert, der für CvSpanID verwendet wird\), richtig ist.  
  
> [!NOTE]
>  Die Verwendung von SpanID Spannen, zu schachteln, ermöglicht es teilweise der Überlappung in demselben Thread oder können sie zum Start auf einem Thread und auf anderen Ende wird nicht unterstützt.  
  
## Siehe auch  
 [Parallelitätsschnellansichtsmarker](../profiling/concurrency-visualizer-markers.md)