---
title: Visualisieren von EventSource-Ereignissen als Marker | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ffbd5568d35b59e262577102a9368089fdcac6be
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431094"
---
# <a name="visualizing-eventsource-events-as-markers"></a>Visualisieren von EventSource-Ereignissen als Marker
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit der Nebenläufigkeitsschnellansicht können EventSource-Ereignisse als Marker angezeigt werden. Zudem kann festgelegt werden, wie die Marker angezeigt werden. Registrieren Sie die ETW-Anbieter-GUID über das Dialogfeld [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md), um die EventSource-Marker anzuzeigen. In der Nebenläufigkeitsschnellansicht werden für die Darstellung von EventSource-Ereignissen als [Flag-Marker](../profiling/flag-markers.md), [Bereichsmarker](../profiling/span-markers.md) und [Meldungsmarker](../profiling/message-markers.md) Standardkonventionen verwendet. Durch Hinzufügen von benutzerdefinierten Feldern zu den Ereignissen, können Sie festlegen, wie EventSource-Ereignisse angezeigt werden. Weitere Informationen zu Markern finden Sie unter [Concurrency Visualizer Markers (Nebenläufigkeitsschnellansichtsmarker)](../profiling/concurrency-visualizer-markers.md). Weitere Informationen zu EventSource-Ereignissen finden Sie unter <xref:System.Diagnostics.Tracing>.  
  
## <a name="default-visualization-of-eventsource-events"></a>Standardvisualisierung von EventSource-Ereignissen  
 Standardmäßig werden von der Nebenläufigkeitsschnellansicht für die Darstellung von EventSource-Ereignissen die folgenden Konventionen verwendet.  
  
### <a name="marker-type"></a>Markertyp  
  
1. Ereignisse mit dem [Opcode](http://msdn.microsoft.com/d97953df-669b-4c55-b1a8-925022b339b7) win:Start oder win:Stop werden als Anfang bzw. Ende eines Bereichs behandelt.  Geschachtelte oder überlappende Bereiche können nicht angezeigt werden. Ereignispaare, die mit einem Thread beginnen und mit einem anderen enden, können nicht angezeigt werden.  
  
2. Ein Ereignis, mit einem anderen Opcode als win:Start oder win:Stop wird als Flag-Marker behandelt, sofern für die [Ebene](http://msdn.microsoft.com/dfa4e0a9-4d89-4f50-aef9-1dae0dc11726) (Feld EVENT_RECORD.EVENT_HEADER.EVENT_DESCRIPTOR) nicht win:Verbose oder höher festgelegt ist.  
  
3. In allen anderen Fällen wird das Ereignis als Meldung behandelt.  
  
### <a name="importance"></a>Wichtigkeit  
 In der folgenden Tabelle wird das Verhältnis zwischen Ereignisebene und Markerwichtigkeit definiert.  
  
|ETW-Ebene|Nebenläufigkeitsschnellansicht – Wichtigkeit|  
|---------------|---------------------------------------|  
|win:LogAlways|Normal|  
|win:Critical|Kritisch|  
|win:Error|Kritisch|  
|win:Warning|Hoch|  
|win:Informational|Normal|  
|win:Verbose|Niedrig|  
|Greater than win:verbose|Niedrig|  
  
### <a name="series-name"></a>Reihenname  
 Der Taskname des Ereignisses wird für den Namen der Reihe verwendet. Der Name der Reihe ist leer, wenn für das Ereignis keine Task definiert wurde.  
  
### <a name="category"></a>Kategorie  
 Wenn die Ebene win:Critical oder win:Error lautet, lautet die Kategorie Alert (-1). Andernfalls wird für die Kategorie der Standardwert (0) verwendet.  
  
### <a name="text"></a>Text  
 Wenn für das Ereignis eine formatierte printf-type-Textmeldung definiert wurde, wird diese als Beschreibung für den Marker angezeigt. Andernfalls besteht die Beschreibung aus dem Namen des Ereignisses und dem Wert der einzelnen Nutzlastfeldern.  
  
## <a name="customizing-visualization-of-eventsource-events"></a>Anpassen der Visualisierung von EventSource-Ereignissen  
 Sie können die Anzeige von EventSource-Ereignissen anpassen, indem Sie die entsprechenden Felder wie in den folgenden Abschnitten beschrieben zum Ereignis hinzufügen.  
  
### <a name="marker-type"></a>Markertyp  
 Verwenden Sie das Feld `cvType`, ein Byte, um die Art des Markers festzulegen, der für die Darstellung des Ereignisses verwendet wird. Folgende Werte sind für cvType verfügbar:  
  
|cvType-Wert|Resultierender Markertyp|  
|------------------|---------------------------|  
|0|Meldung|  
|1|Bereichsanfang|  
|2|Bereichsende|  
|3|Flag|  
|Alle anderen Werte|Meldung|  
  
### <a name="importance"></a>Wichtigkeit  
 Mit dem Feld `cvImportance`, einem Byte, können Sie zwar die Wichtigkeitseinstellung für ein EventSource-Ereignis festlegen. Es wird jedoch empfohlen, die angezeigte Wichtigkeit eines Ereignisses über die Ebene festzulegen.  
  
|Wert von cvImportance|Nebenläufigkeitsschnellansicht – Wichtigkeit|  
|------------------------|---------------------------------------|  
|0|Normal|  
|1|Kritisch|  
|2|Hoch|  
|3|Hoch|  
|4|Normal|  
|5|Niedrig|  
|Alle anderen Werte|Niedrig|  
  
### <a name="series-name"></a>Reihenname  
 Verwenden Sie das Ereignisfeld `cvSeries`, eine Zeichenfolge, um den Reihennamen festzulegen, der von der Nebenläufigkeitsschnellansicht für ein EventSource-Ereignis festgelegt wird.  
  
### <a name="category"></a>Kategorie  
 Verwenden Sie das Feld `cvCategory`, ein Byte, um die Kategorie festzulegen, die von der Nebenläufigkeitsschnellansicht für ein EventSource-Ereignis festgelegt wird.  
  
### <a name="text"></a>Text  
 Verwenden Sie das Feld `cvTextW`, eine Zeichenfolge, um die Beschreibung festzulegen, die von der Nebenläufigkeitsschnellansicht für ein EventSource-Ereignis festgelegt wird.  
  
### <a name="spanid"></a>SpanID  
 Verwenden Sie das Feld cvSpanId, eine ganze Zahl, um Ereignisse passend zusammenzustellen. Der Wert der einzelnen Paare aus Start-/Stoppereignissen, die einen Bereich darstellen, müssen eindeutig sein. Für nebenläufigen Code müssen in der Regel Synchronisierungsprimitive wie <xref:System.Threading.Interlocked.Exchange%2A> verwendet werden, um sicherzustellen, dass der Schlüssel (der für CvSpanID verwendete Wert) richtig angegeben wird.  
  
> [!NOTE]
> Wenn zum Schachteln von Bereichen SpanID verwendet wird, wird nicht unterstützt, dass diese sich auf demselben Thread überlappen oder auf einem Thread beginnen und auf einem anderen enden.  
  
## <a name="see-also"></a>Siehe auch  
 [Concurrency Visualizer Markers (Nebenläufigkeitsschnellansichtsmarker)](../profiling/concurrency-visualizer-markers.md)
