---
title: Erste Schritte mit dem Debugger-Erweiterbarkeit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f8f056ed8fff53eb166b37f2adba9daa17f12916
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515763"
---
# <a name="getting-started-with-debugger-extensibility"></a>Erste Schritte mit der Erweiterbarkeit des Debuggers
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [erste Schritte mit dem Debugger-Erweiterbarkeit](https://docs.microsoft.com/visualstudio/extensibility/debugger/getting-started-with-debugger-extensibility).  
  
Die [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] enthält die Informationen, die Sie zum Erstellen und Anpassen von Debugger-Komponenten verwendet, um das Debuggen von Programmen innerhalb der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Umgebung.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debuggen von Verbesserungen, die die umfassende benutzerfreundlichkeit, die auf vorherigen durchgeführten Tests abgeleitet wurden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debugger. Sie können [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugging für Schritt durch eine Anwendung mehrsprachig, oder Sie können auf dynamische Bearbeitung von Variablen beim Debuggen von Anwendungen und Lösungen mit mehreren Sprachen implementieren.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debuggen ist ausgeführten Out-of-Process mit dem Programm im Debugmodus befindlichen und daher weniger intrusiv im Prozessbereich der Anwendung. Daher ist es einfacher, Komponenten, die Interaktion mit dem Debugger zu schreiben, ohne Auswirkungen auf das Programm debuggen.  
  
 Die optimale Verwendung der [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], Sie sollten mit den folgenden vertraut sein:  
  
-   Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (IDE)  
  
-   Die Programmiersprache C++  
  
-   ATL-COM  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Roadmap für die Erweiterung des Debuggers](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Beschreibt den Prozess der Implementierung Debuggen in Ihrem Produkt, je nach dem Compiler und seine Ausgabe an.  
  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)  
 Bietet eine Übersicht über die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugging-Komponenten, die die Debug-Engine (DE), die ausdrucksauswertung (EE) und die Symbol-Handler (SH) enthalten.  
  
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die wichtigsten Konzepte für das Debuggen Architektur an.  
  
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)  
 Erläutert, wie die Debug-Engine (DE) gleichzeitig in Code, Dokumentationen und Auswertung von ausdruckskontexten arbeitet. Beschreibt, für jede der drei Kontexten, Speicherort, Position oder Auswertung, die für sie relevant.  
  
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)  
 Enthält Links zu verschiedenen Debuggen Aufgaben wie das Starten eines Programms und Auswerten von Ausdrücken.

