---
title: "Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "vs.progression.codemapanalyzers"
helpviewer_keywords: 
  - "Codeanalyse, Abhängigkeitsdiagramme"
  - "Abhängigkeitsdiagramme, Analysieren von Code"
  - "Diagrammdokumente, Analysieren"
ms.assetid: 9dd799a7-f7eb-42ff-8612-b19dde7ff4eb
caps.latest.revision: 11
author: "alexhomer1"
ms.author: "ahomer"
manager: "douge"
caps.handback.revision: 11
---
# Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Führen Sie Analyzer auf Code Maps aus, die Ihnen beim Auffinden sehr komplexer oder verbesserungswürdiger Codeabschnitte helfen. Sie können beispielsweise folgende Analyzer verwenden:  
  
|**Um Code mit diesem Problem zu finden**|**Prüfen Sie, ob diese Abschnitte...**|  
|----------------------------------------------|--------------------------------------------|  
|Schleifen oder Ringabhängigkeiten|...vereinfacht werden können, und überlegen Sie, ob sich diese Kreisläufe auflösen lassen.|  
|Zu viele Abhängigkeiten|...zu viele Funktionen durchführen oder stellen Sie die Auswirkungen einer Änderung in diesen Bereichen fest. Eine wohlgeformte Code Map weist eine minimale Anzahl von Abhängigkeiten auf. Damit Code einfacher zu verwalten, zu ändern, zu testen und wiederzuverwenden ist, erwägen Sie, ob Sie diese Bereiche so umgestalten können, dass sie eindeutig definiert sind, oder ob Code zusammengeführt werden kann, der ähnliche Funktionen ausführt.|  
|Keine Abhängigkeiten|...wirklich benötigt werden oder ob Sie diesen Code entfernen können.|  
  
## Analysieren von Code Maps  
  
1.  Wählen Sie auf der Symbolleiste der Map **Layout** \> **Analyzer** aus, und klicken Sie dann auf den Analyzer, die Sie ausführen möchten:  
  
    |**Analyse**|**Zur Identifizierung der Knoten, die...**|  
    |-----------------|------------------------------------------------|  
    |**Zirkelverweis\-Analyzer**|...Ringabhängigkeiten untereinander aufweisen. **Note:**  Ringabhängigkeiten in der Gruppe **Generika** werden auf der Map nicht angezeigt, wenn Sie die Gruppe erweitern.|  
    |**Hubs Analyzer suchen**|...zu den obersten 25 % der Knoten mit den meisten Verbindungen gehören<br /><br /> **So blenden Sie alle anderen Knoten auf der Map aus**<br /><br /> -   Öffnen Sie das Kontextmenü für die Map, wählen Sie **Erweitert** \> **Auswählen** \> **Nicht markierte ausblenden**.<br />     Nicht markierte Knoten werden auf der Map ausgeblendet und neue Knoten werden vom Analyzer als Hubs identifiziert.|  
    |**Analyzer für Knoten, auf die nicht verwiesen wird**|...keine Verweise aus anderen Knoten haben. **Caution:**  Überprüfen Sie jeden dieser Fälle, bevor Sie davon ausgehen, dass der Code nicht verwendet wird. Bestimmte Abhängigkeiten wie XAML\- und Laufzeitabhängigkeiten können im Code nicht statisch gefunden werden.|  
  
 Code Map Analyzer werden weiterhin ausgeführt, nachdem Sie sie anwenden. Wenn Sie die Map ändern, verarbeiten alle angewendeten Analyzer automatisch die aktualisierte Map erneut. Wählen Sie zum Beenden eines Analyzers auf der Symbolleiste der Map **Layout** \> **Analyzer** aus. Deaktivieren Sie den ausgewählten Analyzer.  
  
> [!TIP]
>  Bei einer sehr großen Map tritt bei der Ausführung eines Analyzers,möglicherweise eine Ausnahme aufgrund unzureichenden Arbeitsspeichers auf. Bearbeiten Sie in diesem Fall die Map, um den Umfang zu verringern oder eine kleinere Map zu generieren, und führen Sie dann den Analyzer aus.  
  
## Siehe auch  
 [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md)   
 [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Zuordnen von Methoden in der Aufrufliste beim Debuggen](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)