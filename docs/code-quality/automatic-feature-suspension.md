---
title: Funktion zum automatischen Unterbrechung | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.workload: multiple
ms.openlocfilehash: 0bb8155f2ec1ed6815ac37f1124dfbf57cf838b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="automatic-feature-suspension"></a>Funktion zum automatischen anhalten
Wenn Ihre verfügbaren Systemarbeitsspeicher auf 200 MB oder weniger fällt, zeigt Visual Studio die folgende Meldung im Code-Editor.  
  
 ![Text der Warnung bis zum Anhalten der vollständige projektmappenanalyse](../code-quality/media/fsa_alert.png "FSA_Alert")  
  
 Wenn Visual Studio eine Bedingung nicht genügenden Arbeitsspeichers erkennt, hält es automatisch bestimmte erweiterten Funktionen, um es stabil bleiben kann. Wenn diese erweiterte Feature anhalten Warnung angezeigt wird, Visual Studio funktionieren auch weiterhin wie zuvor, aber die Leistung leicht beeinträchtigt.  
  
 In einer nicht genügend Arbeitsspeicher verfügbar ist geschieht Folgendes:  
  
-   Vollständige projektmappenanalyse für Visual c# und Visual Basic ist deaktiviert.  
  
-   [Garbagecollection](/dotnet/standard/garbage-collection/index) (GC) mit niedriger Latenz Modus für Visual c# und Visual Basic sind deaktiviert.  
  
-   Visual Studio-Caches geleert werden.  
  
## <a name="improve-visual-studio-performance"></a>Visual Studio zur Leistungssteigerung  
 Tipps und Tricks zum Visual Studio-Leistung zu verbessern, bei der Arbeit mit großen Projektmappen oder niedriger Arbeitsspeicherstatus finden Sie unter [Überlegungen zur Leistung bei großen Projektmappen](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).  
  
## <a name="full-solution-analysis-suspended"></a>Vollständige projektmappenanalyse angehalten  
 Standardmäßig wird vollständige projektmappenanalyse für Visual Basic aktiviert und deaktiviert für Visual c#. Allerdings wird in einer nicht genügend Arbeitsspeicher verfügbar, vollständige projektmappenanalyse automatisch für Visual Basic und Visual C#-, unabhängig von den Einstellungen im Dialogfeld Optionen deaktiviert. Allerdings können Sie vollständige projektmappenanalyse erneut aktivieren, indem Sie auswählen der **reaktivieren** Schaltfläche in der Info Balken-, wenn sie dazu angezeigt wird der **vollständige projektmappenanalyse aktivieren** Kontrollkästchen im Dialogfeld "Optionen" oder durch Visual Studio neu starten. Das Dialogfeld "Optionen" zeigt der aktuelle, vollständigen Lösung immer analyseeinstellungen. Weitere Informationen finden Sie unter [How to: Enable and Disable Full Solution Analysis](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).  
  
## <a name="gc-low-latency-disabled"></a>GC latenzarmen deaktiviert  
 Um GC mit geringer Latenz Modus wieder zu aktivieren, starten Sie Visual Studio neu.  Standardmäßig kann Visual Studio GC mit geringer Latenz Modus aus, wenn Sie eingeben, um sicherzustellen, dass Ihre Eingabe keine GC-Vorgänge blockiert wird. Wenn eine Bedingung nicht genügenden Arbeitsspeichers führt dazu, Visual Studio die automatische Aufhebung Warnung anzeigen dass, ist GC mit geringer Latenz Modus für diese Sitzung deaktiviert. Visual Studio neu zu starten wird der GC-Standardverhalten erneut aktivieren. Weitere Informationen finden Sie unter [GCLatencyMode Enumeration](http://msdn.microsoft.com/Library/057757a5-cd62-4d13-8a40-370eb7f47c87).  
  
## <a name="visual-studio-caches-flushed"></a>Visual Studio-Caches geleert  
 Alle Visual Studio-Caches sofort geleert werden, jedoch werden neu auffüllen, wenn Sie die aktuelle Sitzung für die Entwicklung weiterhin, oder starten Sie Visual Studio neu gestartet. Die Caches geleert enthalten Caches für die folgenden Funktionen.  
  
-   "Suchen Sie alle Verweise"  
  
-   Navigieren zu  
  
-   Fügen mit hinzu  
  
 Darüber hinaus sind Caches für interne Vorgänge für Visual Studio verwendet, ebenfalls gelöscht.  
  
> [!NOTE]
>  Die Funktion zum automatischen Unterbrechung Warnung tritt nur einmal auf der Grundlage einer pro-Projektmappe nicht auf einer sitzungsbasis. Dies bedeutet, dass wenn Sie aus Visual Basic, Visual c# (oder umgekehrt) wechseln, und führen Sie in einem anderen nicht genügend Arbeitsspeicher verfügbar, können Sie eine andere Funktion zum automatischen Unterbrechung Warnung möglicherweise erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Aktivieren und deaktivieren Sie die vollständige Projektmappenanalyse](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)   
 [Grundlagen der Garbagecollection](/dotnet/standard/garbage-collection/fundamentals)   
 [Überlegungen zur Leistung bei großen Projektmappen](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)