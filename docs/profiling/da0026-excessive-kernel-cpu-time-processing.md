---
title: "DA0026: &#220;berm&#228;&#223;ige CPU-Zeit f&#252;r die Kernelverarbeitung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DA0026"
  - "vs.performance.DA0026"
  - "vs.performance.26"
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# DA0026: &#220;berm&#228;&#223;ige CPU-Zeit f&#252;r die Kernelverarbeitung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|TODO|  
|Kategorie \(Category\)|Verwendung der Profilerstellungstools|  
|Profilerstellungsmethode|Sampling|  
|Meldung|Ein relativ hohes Maß an CPU\-Zeit für den Kernelmodus wurde festgestellt.  Untersuchen Sie die Quelle bei aktiviertem SysCall\-Sampling.|  
|Regeltyp|Information|  
  
 Wenn Sie mit der Sampling\-, .NET\-Arbeitsspeicher\- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## Ursache  
 Die CPU\-Zeit im Kernelmodus war größer als die Zeit im Benutzermodus.  Wiederholen Sie die Profilerstellung, und führen Sie ein Sampling der Anzahl von Systemaufrufen \(syscalls\) aus, um die Ursache für die langen Ausführungszeiten im Kernelmodus zu ermitteln.  
  
## Regelbeschreibung  
 Die relativ lange Zeit, die sich die Anwendung im Kernelmodus befand, rechtfertigt möglicherweise eine nähere Untersuchung.  Von einer Benutzermodusanwendung wird in den Kernelmodus gewechselt, um E\/A\-Vorgänge auszuführen, auf Thread\- oder Prozesssynchronisierungsprimitive zu warten oder Systemaufrufe auszuführen.  Sie können die Arten der von der Anwendung ausgeführten Systemaufrufe sowie die verantwortlichen Funktionen untersuchen, indem Sie die Option zum Sammeln von Beispielaufruflisten auf der Grundlage von Systemaufrufen aktivieren.  
  
## Behandeln von Verstößen  
 Führen Sie das Profil erneut aus, und wählen Sie die Option zum Sammeln von Samplings auf der Grundlage von Systemaufrufen aus, um die Arten der von der Anwendung ausgeführten Systemaufrufe zu untersuchen.  Wenn die Profilerstellungstools in der IDE ausgeführt werden, finden Sie weitere Informationen unter [Gewusst wie: Auswählen von Samplingereignissen](../profiling/how-to-choose-sampling-events.md).  Wenn die Profilerstellungstools über die Befehlszeile ausgeführt werden, finden Sie weitere Informationen in der Befehlszeilentoolreferenz der Profilerstellungstools im Abschnitt **Sampling Interval Options**[VSPerfCmd](../profiling/vsperfcmd.md).