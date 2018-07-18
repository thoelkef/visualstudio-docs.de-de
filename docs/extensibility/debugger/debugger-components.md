---
title: Debugger-Komponenten | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b465772f8d3ddba173ecb406845f978765f63cdc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108348"
---
# <a name="debugger-components"></a>Debuggerkomponenten
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger wird als ein VSPackage implementiert und verwaltet die gesamte Debugsitzung. Die Debugsitzung umfasst die folgenden Elemente:  
  
-   **Debugpaket:** der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Debugger bietet die gleiche Benutzeroberfläche unabhängig davon, was debuggt wird.  
  
-   **Sitzungs-Debug-Manager (SDM):** bietet eine konsistente programmgesteuerte Schnittstelle für die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger für die Verwaltung von einer Vielzahl von Debugmodule. Durch die Implementierung erfolgt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **Prozess-Debug-Manager (PDM):** Management, für alle ausgeführten Instanzen des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], eine Liste aller Programme, die ist möglich, oder werden gerade gedebuggt wird. Durch die Implementierung erfolgt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **Datenbankmodul (DE) Debuggen:** ist verantwortlich für die Überwachung eines Programms, der debuggt wird, für die Kommunikation von des Status des ausgeführten Programms ein, das SDM und die PDM und Interaktion mit der ausdrucksauswertung und den Symbol-Anbieter, um Echtzeitanalyse bereitzustellen der Status des Programms Speicher und Variablen. Durch die Implementierung erfolgt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (für die Sprachen, die es unterstützt wird) und von Drittanbietern, die ihre eigenen zur Laufzeit unterstützt werden soll.  
  
-   **Ausdrucksauswertung (EE):** bietet Unterstützung für dynamisch Auswerten von Variablen und Ausdrücke, die vom Benutzer angegeben werden, wenn ein Programm zu einem bestimmten Zeitpunkt beendet wurde. Durch die Implementierung erfolgt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (für die Sprachen, die es unterstützt wird) und von Drittanbietern, die ihre eigenen Sprachen unterstützen möchten.  
  
-   **Symbol-Dienstanbieter (SP):** genannte Handler für ein Symbol, ordnet die Debugsymbole eines Programms mit einer ausgeführten Instanz des Programms, damit sinnvolle Informationen (z. B. Quellcodeebene Debugfunktionen und evaluieren) bereitgestellt werden kann. Durch die Implementierung erfolgt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (für die Common Language Runtime [CLR] Symbole und die Programmdatenbank [PDB]-Symbol Dateiformat) und von Drittanbietern, die ihre eigenen proprietären Methode zum Speichern von Debuginformationen zu haben.  
  
 Das folgende Diagramm zeigt die Beziehung zwischen diesen Elementen von Visual Studio-Debugger.  
  
 ![Debuggen von Komponenten (Übersicht)](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Debuggen eines Pakets](../../extensibility/debugger/debug-package.md)  
 Erläutert das debugpaket, die ausgeführt, in wird der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell und verarbeitet alle der Benutzeroberfläche.  
  
 [Prozessbasierter Debug-Manager](../../extensibility/debugger/process-debug-manager.md)  
 Bietet eine Übersicht über die Funktionen von der PDM, also den Manager der Prozesse, die gedebuggt werden kann.  
  
 [Sitzungsbasierter Debug-Manager](../../extensibility/debugger/session-debug-manager.md)  
 Definiert die SDM, die einen schnellen Überblick über die Debugsitzung der IDE bereitstellt. Die SDM verwaltet die Deutschland.  
  
 [Debugmodul](../../extensibility/debugger/debug-engine.md)  
 Dokumentiert die debugging-Dienste, die DE bereitstellt.  
  
 [Betriebsmodi](../../extensibility/debugger/operational-modes.md)  
 Bietet einen Überblick über die in der IDE stehen drei Modi: Entwurfsmodus, Ausführungsmodus, und sich im Unterbrechungsmodus befinden. Übergang Mechanismen werden außerdem erläutert.  
  
 [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator.md)  
 Erläutert den Zweck der EE zur Laufzeit an.  
  
 [Symbolanbieter](../../extensibility/debugger/symbol-provider.md)  
 Erläutert, wie zur Implementierung der Symbol-Anbieter Variablen und Ausdrücke ausgewertet wird.  
  
 [Typschnellansicht und benutzerdefinierter Viewer](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 Erläutert, was ein Typ Schnellansicht und den benutzerdefinierten Viewer sind und welche Rolle spielt die ausdrucksauswertung unterstützen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die wichtigsten Konzepte für das Debuggen Architektur.  
  
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)  
 Erläutert, wie die DE gleichzeitig in Code, Dokumentation und ausdruckskontexten für die Auswertung ausgeführt wird. Beschreibt, für jede der drei Kontexten, die Position, Position oder Evaluation für sie relevant.  
  
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)  
 Enthält Links zu verschiedenen Debugaufgaben, z. B. ein Programm starten und Auswerten von Ausdrücken.  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)