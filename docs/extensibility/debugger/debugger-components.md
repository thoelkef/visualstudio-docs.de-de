---
title: Debugger-Komponenten | Microsoft-Dokumentation
ms.date: 11/04/2016
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
ms.openlocfilehash: ea47a75ef943b462b35c06b20b9cd21b2ade7b70
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53894258"
---
# <a name="debugger-components"></a>Debugger-Komponenten
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger wird als ein VSPackage implementiert und verwaltet die gesamte Debugsitzung. Die Debugsitzung umfasst die folgenden Elemente:  
  
- **Debug-Paket:** Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Debugger bietet die gleiche Benutzeroberfläche unabhängig davon, was im Debugmodus befindet.  
  
- **Sitzungsbasierter Debug-Manager (SDM):** Bietet eine konsistente programmatische Benutzeroberfläche für die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger für die Verwaltung einer Vielzahl von Debug-Engines. Durch die Implementierung erfolgt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
- **Prozessbasierter Debug-Manager (PDM):** Verwaltet werden, für alle ausgeführten Instanzen des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], eine Liste aller Programme, die möglich, oder werden gedebuggt wird. Durch die Implementierung erfolgt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
- **Debug-Engine (DE):** Ist verantwortlich für die Überwachung einer zu debuggenden Programms kommuniziert den Status des ausgeführten Programms, das SDM und das PDM und interagieren mit der ausdrucksauswertung und symbolanbieter Echtzeitanalysen des Zustands eines Programms Speicher bereitzustellen und Variablen. Durch die Implementierung erfolgt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (für die Sprachen unterstützt) und von Drittanbietern, die ihre eigenen zur Laufzeit unterstützen möchten. 
  
- **Ausdrucksauswertung (EE):** Bietet Unterstützung für dynamisch Auswerten von Variablen und Ausdrücke, die vom Benutzer bereitgestellt werden, wenn ein Programm zu einem bestimmten Zeitpunkt beendet wurde. Durch die Implementierung erfolgt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (für die Sprachen unterstützt) und von Drittanbietern, die ihre eigenen Sprachen unterstützen möchten.  
  
- **Symbol-Dienstanbieter (SP):** So genannte ordnet Handler für ein Symbol, die Debugsymbole eines Programms mit einer ausgeführten Instanz des Programms, damit sinnvolle Informationen (z. B. auf der Source-Code zu debuggen, und klicken Sie mit der Auswertung des Ausdrucks) bereitgestellt werden kann. Durch die Implementierung erfolgt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (für die Common Language Runtime [CLR] Symbole und die Programmdatenbank-[PDB-Datei] symbol-Dateiformat) und von Drittanbietern, die ihre eigenen proprietären Methode zum Speichern von Debuginformationen zu haben.  
  
  Das folgende Diagramm zeigt die Beziehung zwischen diesen Elementen der Visual Studio-Debugger.  
  
  ![Übersicht über die Komponenten Debuggen](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Debug-Paket](../../extensibility/debugger/debug-package.md)  
 Erläutert das debugpaket, der ausgeführt, in wird der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell und behandelt die gesamte Benutzeroberfläche.  
  
 [Prozessbasierter Debug-manager](../../extensibility/debugger/process-debug-manager.md)  
 Bietet eine Übersicht über die Funktionen von der PDM, wird der Prozess-Manager, die debuggt werden kann.  
  
 [Sitzungsbasierter Debug-manager](../../extensibility/debugger/session-debug-manager.md)  
 Definiert das SDM, für der IDE bietet einen einheitlichen Überblick über die Debugsitzung an. Das SDM verwaltet die DE.  
  
 [Debug-engine](../../extensibility/debugger/debug-engine.md)  
 Beschreibt die Debuggen von Diensten, die die DE bereitstellt.  
  
 [Betriebsmodi](../../extensibility/debugger/operational-modes.md)  
 Bietet einen Überblick über die in der IDE arbeiten kann drei Modi: Entwurfsmodus, Ausführungsmodus, und im Unterbrechungsmodus. Übergangsmechanismen werden ebenfalls erläutert.  
  
 [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator.md)  
 Erläutert den Zweck der EE zur Laufzeit an.  
  
 [Symbolanbieter](../../extensibility/debugger/symbol-provider.md)  
 Erläutert, wie zur Implementierung der symbolanbieter Variablen und Ausdrücke ausgewertet wird.  
  
 [Typschnellansicht und benutzerdefinierter viewer](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 Wird erläutert, was eine typschnellansicht und benutzerdefinierter Viewer sind und welche Rolle spielt die ausdrucksauswertung unterstützt beide.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die wichtigsten Konzepte für das Debuggen Architektur an.  
  
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)  
 Erläutert, wie die DE gleichzeitig in Code, Dokumentationen und Auswertung von ausdruckskontexten arbeitet. Beschreibt, für jede der drei Kontexten, Speicherort, Position oder Auswertung, die für sie relevant.  
  
 [Tasks zum Debuggen](../../extensibility/debugger/debugging-tasks.md)  
 Enthält Links zu verschiedenen Debuggen Aufgaben wie das Starten eines Programms und Auswerten von Ausdrücken.  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)