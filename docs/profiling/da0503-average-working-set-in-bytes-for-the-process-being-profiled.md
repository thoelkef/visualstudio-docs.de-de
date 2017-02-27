---
title: "DA0503: Durchschnittliche Arbeitsseite in Bytes f&#252;r den Prozess, f&#252;r den die Profilerstellung ausgef&#252;hrt wird | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.503"
  - "vs.performance.DA0503"
  - "vs.performance.rules.DA0503"
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DA0503: Durchschnittliche Arbeitsseite in Bytes f&#252;r den Prozess, f&#252;r den die Profilerstellung ausgef&#252;hrt wird
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA0503|  
|Kategorie \(Category\)|Ressourcenüberwachung|  
|Profilerstellungsmethode|Alle|  
|Meldung|Diese Information wurde lediglich zu Informationszwecken erhoben.  Vom Leistungsindikator für die Verarbeitung von Arbeitsseiten wird die Belegung des physikalischen Speichers durch den Prozess ermittelt, für den die Profilerstellung ausgeführt wird.  Bei dem gemeldeten Wert handelt es sich um den berechneten Durchschnittswert aus allen Messintervallen.|  
|Regeltyp|Information|  
  
 Wenn Sie mit der Sampling\-, .NET\-Arbeitsspeicher\- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## Regelbeschreibung  
 Diese Meldung gibt Aufschluss über die durchschnittliche Menge an physikalischem Speicher, die gerade von der Arbeitsseite verwendet wird \(in Bytes\).  Die Prozessarbeitsseite stellt Seiten aus dem Prozessadressbereich dar, die sich gegenwärtig im physikalischen Speicher befinden.  
  
 Der gemeldete Wert enthält residente Seiten aus freigegebenen Arbeitsspeichersegmenten, auf die vom Prozess verwiesen wurde.  In den berücksichtigten freigegebenen Arbeitsspeichersegmenten sind auch freigegebene DLLs enthalten, auf die vom Prozess verwiesen wird.  Aufgrund von freigegebenen Arbeitsspeichersegmenten kann der Wert der Prozessarbeitsseite die Menge des virtuellen Arbeitsspeichers übersteigen, der vom Prozess belegt wird.  
  
 Bei dem gemeldeten Wert handelt es sich um den Durchschnittswert aller Messintervalle, in denen der Prozess, dessen Profil erstellt wird, aktiv war.  
  
 Die Größe der Prozessarbeitsseite spiegelt die Menge des virtuellen Arbeitsspeichers wider, die aktiv vom Prozess verwendet wird.  Sie wird auch von der Menge an physikalischem Speicher \(oder RAM\) beeinflusst, die zum Ausführen der Anwendung verfügbar ist, sowie von der Auslastung dieses physikalischen Speichers durch andere ausgeführte Prozesse.  Bei einer Beschränkung des physikalischen Speichers können sich für den Wert der Prozessarbeitsseite deutliche Schwankungen auftreten, wenn vom Betriebssystem versucht wird, die Speicherauslastung durch die aktive Prozesse auszugleichen, indem in regelmäßigen Abständen Seiten mit relativ geringer Aktivität aus Prozessarbeitsseiten gekürzt werden.  
  
 Weitere Informationen über Prozessarbeitsseite, finden Sie unter [Workingset](http://go.microsoft.com/fwlink/?LinkId=177830) in der Speicherverwaltungsdokumentation von Windows.  
  
## Verwenden von Regeldaten  
 Mithilfe des Regelwerts können Sie die Leistung anderer Versionen oder Builds des Programms vergleichen oder die Leistung der Anwendung in unterschiedlichen Profilerstellungsszenarien nachvollziehen.  
  
 Doppelklicken Sie im Fenster "Fehlerliste" auf die Meldung, um zur [Markierungsansicht](../profiling/marks-view.md) der Profilerstellungsdaten zu navigieren.  Suchen Sie die Spalten **Prozess\\Workingset** und **Arbeitsspeicher\\Seiten\/s**.  Vergleichen Sie die beiden Spalten, um zu ermitteln, ob in bestimmten Phasen der Programmausführung ein erhöhtes Maß an E\/A\-Auslagerungsaktivitäten feststellbar ist.