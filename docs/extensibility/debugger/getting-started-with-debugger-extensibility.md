---
title: "Erste Schritte mit dem Debugger-Erweiterbarkeit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Erste Schritte Debugging-SDK"
  - "Debuggen [Debuggen SDK], erste Schritte"
  - "Debugging-SDK, erste Schritte"
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Erste Schritte mit dem Debugger-Erweiterbarkeit
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] enthält die Informationen, die der Debugger Komponenten erstellen und anpassen müssen, müssen die Testprogrammen aus der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung verwendet werden.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen besitzt die Verbesserungen hinzugefügt, die von den Tests Benutzerfreundlichkeits umfangreichen abgeleitet sind, die auf früheren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger ausgeführt werden.  Sie können [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen verwenden, um eine mehrsprachige Anwendung zu durchlaufen, oder Sie können die direkte Bearbeitung von Variablen beim Debuggen von Anwendungen und mehrsprachigen Projektmappe implementieren.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen ist mit dem prozessexterne auf Programm, das gedebuggt wird und daher im Prozessbereich der Anwendung weniger intrusiv.  Daher ist es einfacher, Komponenten zu schreiben, die mit dem Debugger interagieren, ohne das Debugprogramm zu beeinflussen.  
  
 Zur optimalen Verwendung [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], sollten Sie mit folgendem vertraut sein:  
  
-   Die integrierte Entwicklungsumgebung \(IDE\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]  
  
-   Die C\+\+\-Programmiersprache  
  
-   ATL  
  
## In diesem Abschnitt  
 [Roadmap für die Erweiterung des Debuggers](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Erläutert die Schritte zum Implementieren des Debuggens im Produkt abhängig vom Compiler und seiner Ausgabe.  
  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)  
 Bietet eine Übersicht über [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Komponenten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , das Debuggen, die das Debugmodul \(DE\), Ausdrucksauswertung \(Symbol\) und EE Klassenhandler \(SH\) enthalten.  
  
 [Debugger\-Konzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die Architektur wichtigsten Konzepte des Debuggens.  
  
 [Debugger\-Kontexte](../../extensibility/debugger/debugger-contexts.md)  
 Erläutert, wie das Debugmodul \(DE\) gleichzeitig innerhalb des Codes, der Dokumentation und den Ausdrucksauswertungs kontexte funktioniert.  Beschreibt für jede der drei Kontexten, des Speicherorts, der Position oder der Auswertung, die relevant sind.  
  
 [Debugging\-Aufgaben](../../extensibility/debugger/debugging-tasks.md)  
 Enthält Links zu den verschiedenen Aufgaben Debuggen eines Programms starten, z und Auswerten von Ausdrücken.