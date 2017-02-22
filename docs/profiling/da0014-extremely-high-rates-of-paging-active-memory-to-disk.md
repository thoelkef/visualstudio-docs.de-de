---
title: "DA0014: &#196;u&#223;erst hohes Ma&#223; an Paging von aktivem Speicher auf den Datentr&#228;ger | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAMemoryBound"
  - "vs.performance.DA0014"
  - "vs.performance.14"
  - "vs.performance.rules.DA0014"
ms.assetid: a7fa3749-9191-437a-9331-9d917181e62f
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0014: &#196;u&#223;erst hohes Ma&#223; an Paging von aktivem Speicher auf den Datentr&#228;ger
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA0014|  
|Kategorie \(Category\)|Speicher und Auslagerung|  
|Profilerstellungsmethode|Alle|  
|Meldung|Ein äußerst hohes Maß an Paging von aktivem Speicher auf den Datenträger wurde festgestellt.  Die Anwendung ist möglicherweise speichergebunden.|  
|Regeltyp|Warnung|  
  
 Wenn Sie mit der Sampling\-, .NET\-Arbeitsspeicher\- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 25 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## Ursache  
 Die bei der Profilerstellung erfassten Systemleistungsdaten deuten darauf hin, dass während der Profilerstellung ein sehr hohes Maß an Auslagerungen von aktivem Speicher auf den Datenträger \(und umgekehrt\) aufgetreten ist.  Solch hohe Auslagerungsraten wirken sich in der Regel negativ auf Leistung und Reaktionszeit der Anwendung aus.  Verringern Sie ggf. die Speicherbelegungen, indem Sie die Algorithmen überarbeiten.  Sie müssen möglicherweise auch die Speicheranforderungen der Anwendung berücksichtigt werden. Ausführen auf einem Computer mit mehr Arbeitsspeicher erneut ein Profil erstellen.  
  
## Regelbeschreibung  
 Eine übermäßige Auslagerung auf den Datenträger kann auf einen Mangel an physikalischem Speicher zurückzuführen sein.  Wenn die Verwendung des physikalischen Datenträgers, auf dem sich die Auslagerungsdatei befindet, von Auslagerungsvorgängen dominiert wird, kann dies zu einer Verlangsamung anderer anwendungsorientierter Datenträgervorgänge führen, die den gleichen Datenträger zum Ziel haben.  
  
 Seiten werden häufig in Massenauslagerungsvorgängen vom Datenträger gelesen oder auf den Datenträger geschrieben.  Die Anzahl der geänderten Seiten pro Sekunde ist häufig deutlich größer als beispielsweise die Anzahl der Seiten\-Schreibvorgänge pro Sekunde.  Der Grund: Die geänderten Seiten pro Sekunde beinhalten auch geänderte Datenseiten aus dem Systemdateicache.  Es ist jedoch nicht immer einfach, den direkt für die Auslagerung verantwortlichen Prozess oder den Grund für die Auslagerung zu ermitteln.  
  
> [!NOTE]
>  Diese Regel wird ausgelöst, wenn die Auslagerung des aktiven Speichers eine sehr hohe Rate erreicht.  Wenn die Ebene des Pagings bedeutend ist, aber nicht extrem, wird stattdessen die Informationsregel [DA0017: Hohes Maß an Paging von aktivem Speicher auf den Datenträger](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md) ausgelöst.  
  
## Behandeln von Verstößen  
 Doppelklicken Sie im Fenster "Fehlerliste" auf die Meldung, um zur Ansicht [Markierungen](../profiling/marks-view.md) zu navigieren.  Suchen Sie die Spalte **Arbeitsspeicher\\Seiten\/s**.  Überprüfen Sie, ob die E\/A\-Auslagerungsaktivitäten in bestimmten Phasen der Programmausführung besonders hoch ausfallen.  
  
 Wenn Sie in einem Auslastungstest\-Szenario Profildaten für eine ASP.NET\-Anwendung erfassen, führen Sie den Auslastungstest auf einem Computer mit zusätzlichem physikalischem Speicher \(oder RAM\) erneut aus.  
  
 Erwägen Sie, Speicherbelegungen durch das Überarbeiten von Algorithmen und Vermeiden von speicherintensiven APIs wie "String.Concat" und "String.Substring" zu reduzieren.