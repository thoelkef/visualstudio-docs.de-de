---
title: "DA0504: Maximale Arbeitsseite in Bytes f&#252;r den Prozess, f&#252;r den die Profilerstellung ausgef&#252;hrt wird | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0504"
  - "vs.performance.504"
  - "vs.performance.rules.DA0504"
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# DA0504: Maximale Arbeitsseite in Bytes f&#252;r den Prozess, f&#252;r den die Profilerstellung ausgef&#252;hrt wird
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA0504|  
|Kategorie \(Category\)|Ressourcenverwaltung|  
|Profilerstellungsmethode|Alle|  
|Meldung|Diese Information wurde lediglich zu Informationszwecken erhoben.  Vom Leistungsindikator für die Verarbeitung von Arbeitsseiten wird die Belegung des physikalischen Speichers durch den Prozess ermittelt, für den die Profilerstellung ausgeführt wird.  Bei dem gemeldeten Wert handelt es sich um den Maximalwert aus allen Messintervallen.|  
|Regeltyp|Information|  
  
 Wenn Sie mit der Sampling\-, .NET\-Arbeitsspeicher\- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## Regelbeschreibung  
 In dieser Meldung wird die maximale Menge an virtuellem Arbeitsspeicher \(in Bytes\) gemeldet, die derzeit vom Prozess verwendet wird.  Die Prozessarbeitsseite stellt Seiten aus dem Prozessadressbereich dar, die sich gegenwärtig im physikalischen Speicher befinden.  Von dieser Regel wird der maximale Wert für die Prozessarbeitsseite bei aktiver Profilerstellung gemeldet.  
  
 Der gemeldete Wert enthält residente Seiten aus freigegebenen Arbeitsspeichersegmenten, auf die vom Prozess verwiesen wurde.  In den berücksichtigten freigegebenen Arbeitsspeichersegmenten sind auch freigegebene DLLs enthalten, auf die vom Prozess verwiesen wird.  Aufgrund von freigegebenen Arbeitsspeichersegmenten kann der Wert der Prozessarbeitsseite die Menge des virtuellen Arbeitsspeichers übersteigen, der vom Prozess belegt wird.  
  
 Die Größe der Prozessarbeitsseite spiegelt die Menge des virtuellen Arbeitsspeichers wider, die aktiv vom Prozess verwendet wird.  Sie wird auch von der Menge an physikalischem Speicher \(oder RAM\) beeinflusst, die zum Ausführen der Anwendung verfügbar ist, sowie von der Auslastung dieses physikalischen Speichers durch andere ausgeführte Prozesse.  Weitere Informationen über Prozessarbeitsseite, finden Sie unter [Workingset](http://go.microsoft.com/fwlink/?LinkId=177830) in der Speicherverwaltungsdokumentation von Windows.  
  
## Verwenden von Regeldaten  
 Diese Messdaten stammen aus der Windows\-Leistungsüberwachung und dienen lediglich als Information.  Mithilfe der Daten können Sie die Leistung anderer Versionen oder Builds des Programms vergleichen oder die Leistung der Anwendung in unterschiedlichen Testszenarien nachvollziehen.  
  
 Doppelklicken Sie im Fenster "Fehlerliste" auf die Meldung, um zur [Markierungsansicht](../profiling/marks-view.md) der Profilerstellungsdaten zu navigieren.  Suchen Sie die Leistungsindikatorspalten **Prozess\\Workingset** und **Arbeitsspeicher\\Seiten\/s**.  Suchen Sie anschließend den maximalen Wert von **Prozess\\Workingset**, und vergleichen Sie ihn mit dem Wert von **Arbeitsspeicher\\Seiten\/s**.  Häufig hängt der Maximalwert für Arbeitsseiten mit einem Intervall mit geringerer E\/A\-Auslagerungsaktivität zusammen. Dies gilt besonders bei Computern mit eingeschränktem Arbeitsspeicher.