---
title: Erste Schritte mit Debugger-Erweiterbarkeits | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 964b6bcc18e74174aa59e7a1bb4441e24d3918d7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-debugger-extensibility"></a>Erste Schritte mit Debugger-Erweiterbarkeits-
Die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] enthält Informationen, die Sie zum Erstellen und Anpassen von Debuggerkomponenten verwendet benötigen, um das Debuggen von Programmen innerhalb der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Debuggen wurde hinzugefügt, Verbesserungen, die eine umfangreiche Verwendbarkeit auf vorherige durchgeführten Tests abgeleitet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger. Sie können [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen schrittweise Durchlaufen einer mehrsprachigen-Anwendung, oder Sie können auf dynamische Bearbeitung von Variablen beim Debuggen von Anwendungen und Lösungen von mehrsprachigen implementieren.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Debuggen ist ausgeführten Out-of-Process mit dem Programm, das gerade gedebuggt wird und daher weniger intrusiv im Prozessbereich der Anwendung. Daher ist es einfacher, Komponenten zu schreiben, die Interaktion mit dem Debugger ohne Auswirkungen auf Ihre Anwendung debuggen.  
  
 Die optimale Verwendung der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], Sie sollten mit den folgenden vertraut sein:  
  
-   Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE)  
  
-   Die Programmiersprache C++  
  
-   ATL COM  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Roadmap für die Erweiterung des Debuggers](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Beschreibt den Prozess der Implementierung Ihres Produkts, je nach dem Compiler und dessen Ausgabe Debuggen.  
  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)  
 Bietet eine Übersicht über die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen von Komponenten, z. B. die Debugging-Modul (DE), ausdrucksauswertung (EE) und Symbol Handler ("SH").  
  
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die wichtigsten Konzepte für das Debuggen Architektur.  
  
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)  
 Erläutert, wie die Debugging-Modul (DE) gleichzeitig in Code, Dokumentation und ausdruckskontexten für die Auswertung ausgeführt wird. Beschreibt, für jede der drei Kontexten, Speicherort, Position oder Evaluation für sie relevant.  
  
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)  
 Enthält Links zu verschiedenen Debugaufgaben, z. B. ein Programm starten und Auswerten von Ausdrücken.