---
title: Einstieg in die debuggererweiterbarkeit | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1c616c7cf8ed90ec3d76046892167b9b742a1b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152703"
---
# <a name="getting-started-with-debugger-extensibility"></a>Erste Schritte mit der Erweiterbarkeit des Debuggers
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]Stellt die Informationen bereit, die Sie zum Erstellen und Anpassen von Debugger-Komponenten benötigen, die zum Debuggen von Programmen in der Umgebung verwendet werden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] beim Debuggen wurden Verbesserungen hinzugefügt, die von den umfassenden Nutz barkeits Tests für vorherige [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debugger abgeleitet wurden Sie können das [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debuggen verwenden, um eine mehrsprachige Anwendung zu durchlaufen, oder Sie können die dynamische Bearbeitung von Variablen beim Debuggen von Anwendungen und mehrsprachigen Lösungen implementieren.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] das Debuggen wird außerhalb des Prozesses ausgeführt, während das Programm gedebuggt wird und daher im Prozessbereich der Anwendung weniger eindringlich ist. Folglich ist es einfacher, Komponenten zu schreiben, die mit dem Debugger interagieren, ohne dass sich dies auf das debugprogramm auswirkt.  
  
 Um das bestmögliche zu verwenden [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] , sollten Sie mit folgendem vertraut sein:  
  
- Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (Integrated Development Environment, IDE)  
  
- Programmiersprache C++  
  
- ATL-COM  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Roadmap für die Erweiterung des Debuggers](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Beschreibt den Prozess der Implementierung des Debuggens in Ihrem Produkt, abhängig von Ihrem Compiler und seiner Ausgabe.  
  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)  
 Bietet eine Übersicht über die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debuggingkomponenten, einschließlich Debug-Engine (de), Ausdrucks Auswertung (EE) und Symbol Handler (SH).  
  
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die wichtigsten Konzepte der debuggingarchitektur.  
  
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)  
 Erläutert, wie die Debug-Engine (de) parallel innerhalb von Code-, Dokumentations-und Ausdrucks Auswertungs Kontexten funktioniert. Beschreibt für jeden der drei Kontexte den Speicherort, die Position oder die Auswertung, die für ihn relevant sind.  
  
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)  
 Enthält Links zu verschiedenen Debuggingaufgaben, z. b. das Starten eines Programms und Auswerten von Ausdrücken.
