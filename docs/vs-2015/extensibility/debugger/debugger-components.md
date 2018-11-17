---
title: Debugger-Komponenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aabd6311212b866b9171758c8bec39e3beebbfea
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797493"
---
# <a name="debugger-components"></a>Debuggerkomponenten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debugger wird als ein VSPackage implementiert und verwaltet die gesamte Debugsitzung. Die Debugsitzung umfasst die folgenden Elemente:  
  
- **Debugpaket:** der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -Debugger bietet die gleiche Benutzeroberfläche unabhängig davon, was im Debugmodus befindet.  
  
- **Sitzungsbasierter Debug-Manager (SDM):** bietet eine konsistente programmatische Benutzeroberfläche für die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debugger für die Verwaltung einer Vielzahl von Debug-Engines. Durch die Implementierung erfolgt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
- **Prozessbasierter Debug-Manager (PDM):** verwaltet, die für alle ausgeführten Instanzen des [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], eine Liste aller Programme, die möglich, oder werden gedebuggt wird. Durch die Implementierung erfolgt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
- **Debug-Engine (DE):** ist verantwortlich für die Überwachung einer zu debuggende Programm wird, den Status des ausgeführten Programms, das SDM und das PDM Kommunikation und Interaktion mit der ausdrucksauswertung und die symbolanbieter, um Echtzeitanalyse bereitzustellen der Status der Arbeitsspeicher und in der Variablen eines Programms. Durch die Implementierung erfolgt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (für die Sprachen unterstützt) und von Drittanbietern, die ihre eigenen zur Laufzeit unterstützen möchten.  
  
- **Ausdrucksauswertung (EE):** bietet Unterstützung für dynamisch Auswerten von Variablen und Ausdrücke, die vom Benutzer bereitgestellt werden, wenn ein Programm zu einem bestimmten Zeitpunkt beendet wurde. Durch die Implementierung erfolgt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (für die Sprachen unterstützt) und von Drittanbietern, die ihre eigenen Sprachen unterstützen möchten.  
  
- **Symbol-Dienstanbieter (SP):** so genannte Handler für ein Symbol, ordnet die Debugsymbole eines Programms mit einer ausgeführten Instanz des Programms, damit sinnvolle Informationen (z. B. Source-Code-Level-Debugfunktionen und Auswertung) bereitgestellt werden kann. Durch die Implementierung erfolgt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (für die Common Language Runtime [CLR] Symbole und die Programmdatenbank-[PDB-Datei] symbol-Dateiformat) und von Drittanbietern, die ihre eigenen proprietären Methode zum Speichern von Debuginformationen zu haben.  
  
  Das folgende Diagramm zeigt die Beziehung zwischen diesen Elementen der Visual Studio-Debugger.  
  
  ![Übersicht über die Komponenten Debuggen](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Debuggen eines Pakets](../../extensibility/debugger/debug-package.md)  
 Erläutert das debugpaket, der ausgeführt, in wird der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] shell und behandelt die gesamte Benutzeroberfläche.  
  
 [Prozessbasierter Debug-Manager](../../extensibility/debugger/process-debug-manager.md)  
 Bietet eine Übersicht über die Funktionen von der PDM, wird der Prozess-Manager, die debuggt werden kann.  
  
 [Sitzungsbasierter Debug-Manager](../../extensibility/debugger/session-debug-manager.md)  
 Definiert das SDM, für der IDE bietet einen einheitlichen Überblick über die Debugsitzung an. Das SDM verwaltet die DE.  
  
 [Debug-Engine](../../extensibility/debugger/debug-engine.md)  
 Beschreibt die Debuggen von Diensten, die die DE bereitstellt.  
  
 [Betriebsmodi](../../extensibility/debugger/operational-modes.md)  
 Bietet einen Überblick über die in der IDE arbeiten kann drei Modi: Entwurfsmodus, Ausführungsmodus, und im Unterbrechungsmodus. Übergangsmechanismen werden ebenfalls erläutert.  
  
 [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator.md)  
 Erläutert den Zweck der EE zur Laufzeit an.  
  
 [Symbolanbieter](../../extensibility/debugger/symbol-provider.md)  
 Erläutert, wie zur Implementierung der symbolanbieter Variablen und Ausdrücke ausgewertet wird.  
  
 [Typschnellansicht und benutzerdefinierter Viewer](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 Wird erläutert, was eine typschnellansicht und benutzerdefinierter Viewer sind und welche Rolle spielt die ausdrucksauswertung unterstützt beide.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die wichtigsten Konzepte für das Debuggen Architektur an.  
  
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)  
 Erläutert, wie die DE gleichzeitig in Code, Dokumentationen und Auswertung von ausdruckskontexten arbeitet. Beschreibt, für jede der drei Kontexten, Speicherort, Position oder Auswertung, die für sie relevant.  
  
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)  
 Enthält Links zu verschiedenen Debuggen Aufgaben wie das Starten eines Programms und Auswerten von Ausdrücken.  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)

