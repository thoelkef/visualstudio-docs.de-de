---
title: Debuggerkomponenten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03c400fd03c5ee0f2629e9f436b65f53f8f2ac8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739013"
---
# <a name="debugger-components"></a>Debugger-Komponenten
Der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger wird als VSPackage implementiert und verwaltet die gesamte Debugsitzung. Die Debugsitzung umfasst die folgenden Elemente:

- **Debugpaket:** Der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger stellt die gleiche Benutzeroberfläche bereit, unabhängig davon, was gedebugft wird.

- **Sitzungsdebug-Manager (SDM):** Stellt eine konsistente programmgesteuerte Schnittstelle zum [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger für die Verwaltung einer Vielzahl von Debugmodulen bereit. Es wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]von implementiert.

- **Prozess-Debug-Manager (PDM):** Verwaltet für alle ausgeführten Instanzen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], eine Liste aller Programme, die gedebuggt werden können oder werden. Es wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]von implementiert.

- **Debug-Engine (DE):** Ist verantwortlich für die Überwachung eines zu debuggenden Programms, die Kommunikation des Status des laufenden Programms an das SDM und das PDM und die Interaktion mit dem Ausdrucksevaluator und Symbolanbieter, um eine Echtzeitanalyse des Zustands des Speichers und der Variablen eines Programms bereitzustellen. Es wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] von (für die Sprachen, die es unterstützt) und Drittanbietern implementiert, die ihre eigene Laufzeit unterstützen möchten.

- **Ausdrucksevaluator (EE):** Bietet Unterstützung für die dynamische Auswertung von Variablen und Ausdrücken, die vom Benutzer bereitgestellt werden, wenn ein Programm an einem bestimmten Punkt angehalten wurde. Es wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] von (für die Sprachen, die es unterstützt) und Drittanbietern implementiert, die ihre eigenen Sprachen unterstützen möchten.

- **Symbolanbieter (SP):** Auch als Symbolhandler bezeichnet, ordnet die Debugsymbole eines Programms einer laufenden Instanz des Programms zu, sodass aussagekräftige Informationen bereitgestellt werden können (z. B. Debugging auf Quellcodeebene und Ausdrucksauswertung). Es wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] von (für die Common Language Runtime [CLR] Symbole und das Program DataBase [PDB] Symboldateiformat) und von Drittanbietern implementiert, die ihre eigene proprietäre Methode zum Speichern von Debugging-Informationen haben.

  Das folgende Diagramm zeigt die Beziehung zwischen diesen Elementen des Visual Studio-Debuggers.

  ![Übersicht über das Debuggen von Komponenten](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>In diesem Abschnitt
 [Debug-Paket](../../extensibility/debugger/debug-package.md) Erläutert das Debugpaket, das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in der Shell ausgeführt wird und die gesamte Benutzeroberfläche verarbeitet.

 [Prozess-Debug-Manager](../../extensibility/debugger/process-debug-manager.md) Bietet einen Überblick über die Funktionen des PDM, der der Manager der Prozesse ist, die gedebuggt werden können.

 [Sitzungsdebug-Manager](../../extensibility/debugger/session-debug-manager.md) Definiert das SDM, das der IDE eine einheitliche Ansicht der Debugsitzung bietet. Das SDM verwaltet die DE.

 [Debug-Engine](../../extensibility/debugger/debug-engine.md) Dokumentiert die von der DE-Dienstdienstleiste angebotenen Debugdienst.

 [Betriebsmodi](../../extensibility/debugger/operational-modes.md) Bietet einen Überblick über die drei Modi, in denen die IDE betrieben werden kann: Entwurfsmodus, Ausführungsmodus und Unterbrechungsmodus. Übergangsmechanismen werden ebenfalls diskutiert.

 [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator.md) Erläutert den Zweck der EE zur Laufzeit.

 [Symbolanbieter](../../extensibility/debugger/symbol-provider.md) Erläutert, wie der Symbolanbieter bei der Implementierung Variablen und Ausdrücke auswertet.

 [Typvisualisierung und benutzerdefinierter Viewer](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Erläutert, was eine Typvisualisierung und ein benutzerdefinierter Viewer sind und welche Rolle der Ausdrucksauswertungswert bei der Unterstützung beider spielt.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md) Beschreibt die wichtigsten Architekturkonzepte für das Debuggen.

 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md) Erläutert, wie die DE gleichzeitig in Code-, Dokumentations- und Ausdrucksauswertungskontexten arbeitet. Beschreibt für jeden der drei Kontexte den Standort, die Position oder die Bewertung, die für ihn relevant sind.

 [Debug-Aufgaben](../../extensibility/debugger/debugging-tasks.md) Enthält Links zu verschiedenen Debugaufgaben, z. B. zum Starten eines Programms und Auswerten von Ausdrücken.

## <a name="see-also"></a>Weitere Informationen
- [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
