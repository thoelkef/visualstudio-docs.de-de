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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04865145afc5df7edc21611511878263021d4e37
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889986"
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
 [Debuggen des Pakets](../../extensibility/debugger/debug-package.md) wird erläutert, das debugpaket, der ausgeführt, in wird der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell und behandelt die gesamte Benutzeroberfläche.

 [Prozessbasierter Debug-Manager](../../extensibility/debugger/process-debug-manager.md) bietet eine Übersicht über die Funktionen von der PDM, wird der Prozess-Manager, die debuggt werden kann.

 [Sitzungsbasierter Debug-Manager](../../extensibility/debugger/session-debug-manager.md) definiert, das SDM, für der IDE bietet eine einheitliche Ansicht der Debugsitzung. Das SDM verwaltet die DE.

 [Debug-Engine](../../extensibility/debugger/debug-engine.md) beschreibt die Debuggen von Diensten, die die DE bereitstellt.

 [Betriebsmodi](../../extensibility/debugger/operational-modes.md) bietet einen Überblick über die in der IDE arbeiten kann drei Modi: Entwurfsmodus, Ausführungsmodus, und im Unterbrechungsmodus. Übergangsmechanismen werden ebenfalls erläutert.

 [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator.md) erläutert den Zweck der EE zur Laufzeit.

 [Symbolanbieter](../../extensibility/debugger/symbol-provider.md) wird erläutert, wie zur Implementierung der symbolanbieter Variablen und Ausdrücke ausgewertet wird.

 [Typ der Schnellansicht und den benutzerdefinierten Viewer](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) erläutert, welche eine typschnellansicht und benutzerdefinierter Viewer sind und welche Rolle spielt die ausdrucksauswertung unterstützt beide.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md) beschreibt die wichtigsten Konzepte für das Debuggen Architektur.

 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md) wird erläutert, wie die DE gleichzeitig innerhalb von Code, Dokumentationen und Ausdruck Auswertung Kontexten ausgeführt wird. Beschreibt, für jede der drei Kontexten, Speicherort, Position oder Auswertung, die für sie relevant.

 [Debugtasks](../../extensibility/debugger/debugging-tasks.md) enthält Links zu verschiedenen Debuggingaufgaben ausführen, z. B. Starten eines Programms und Auswerten von Ausdrücken.

## <a name="see-also"></a>Siehe auch
- [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)