---
title: Debugger-Komponenten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12f865e7d4c44cfa4002b330ed85ec95f95a8ef9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200668"
---
# <a name="debugger-components"></a>Debuggerkomponenten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debugger wird als VSPackage implementiert und verwaltet die gesamte Debugsitzung. Die Debugsitzung umfasst die folgenden Elemente:  
  
- **Paket Debuggen:** Der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debugger stellt die gleiche Benutzeroberfläche bereit, unabhängig davon, was gerade gedebuggt wird.  
  
- **Sitzungsdebug-Manager (SDM):** Stellt eine konsistente programmgesteuerte Schnittstelle [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] für den Debugger zur Verwaltung einer Vielzahl von Debug-engines bereit. Sie wird von implementiert [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- **Process Debug Manager (PDM):** Verwaltet für alle ausgelaufenden Instanzen von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] eine Liste aller Programme, die bzw. das gedebuggt werden kann. Sie wird von implementiert [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- **Debug-Engine (de):** Ist für die Überwachung eines Programms zuständig, das gedebuggt wird, wobei der Status des ausgelaufenden Programms an SDM und PDM kommuniziert und mit der Ausdrucks Auswertung und dem Symbol Anbieter interagiert wird, um Echtzeitanalysen des Zustands des Arbeitsspeichers und der Variablen eines Programms zu ermöglichen. Sie wird von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (für die unterstützten Sprachen) und von Drittanbietern implementiert, die ihre eigene Laufzeit unterstützen möchten.  
  
- **Ausdrucks Auswertung (EE):** Bietet Unterstützung für das dynamische Auswerten von Variablen und Ausdrücken, die vom Benutzer bereitgestellt werden, wenn ein Programm an einem bestimmten Punkt angehalten wurde. Sie wird von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (für die unterstützten Sprachen) und von Drittanbietern implementiert, die ihre eigenen Sprachen unterstützen möchten.  
  
- **Symbol Anbieter (SP):** Wird auch als Symbol Handler bezeichnet und ordnet die Debugsymbole eines Programms einer ausgelaufenden Instanz des Programms zu, damit sinnvolle Informationen bereitgestellt werden können (z. b. Debuggen auf Quell Code Ebene und Ausdrucks Auswertung). Sie wird von implementiert [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (für die CLR-Symbole (Common Language Runtime) und das Format der Programmdatenbank [PDB]-Symbol Datei) und von Drittanbietern, die über eine eigene proprietäre Methode zum Speichern von Debuginformationen verfügen.  
  
  Das folgende Diagramm zeigt die Beziehung zwischen diesen Elementen des Visual Studio-Debuggers.  
  
  ![Übersicht über das Debuggen von Komponenten](../../extensibility/debugger/media/dbugcompovrview.gif "Dbugcompovrview")  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Debuggen eines Pakets](../../extensibility/debugger/debug-package.md)  
 Erläutert das Debugpaket, das in der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Shell ausgeführt wird und die gesamte Benutzeroberfläche verarbeitet.  
  
 [Prozessbasierter Debug-Manager](../../extensibility/debugger/process-debug-manager.md)  
 Bietet eine Übersicht über die Features des PDM, das der Manager der Prozesse ist, die gedebuggten werden können.  
  
 [Sitzungsbasierter Debug-Manager](../../extensibility/debugger/session-debug-manager.md)  
 Definiert das SDM, das eine einheitliche Ansicht der Debugsitzung für die IDE bereitstellt. Der SDM verwaltet den de.  
  
 [Debug-Engine](../../extensibility/debugger/debug-engine.md)  
 Dokumentiert die Debugdienste, die von der de bereitstellt werden.  
  
 [Betriebsmodi](../../extensibility/debugger/operational-modes.md)  
 Bietet eine Übersicht über die drei Modi, in denen die IDE funktionieren kann: Entwurfs Modus, Lauf Modus und Abbruch Modus. Übergangsmechanismen werden ebenfalls erläutert.  
  
 [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator.md)  
 Erläutert den Zweck der EE zur Laufzeit.  
  
 [Symbolanbieter](../../extensibility/debugger/symbol-provider.md)  
 Erläutert, wie der Symbol Anbieter bei der Implementierung Variablen und Ausdrücke auswertet.  
  
 [Typschnellansicht und benutzerdefinierter Viewer](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 Erläutert, worum es sich bei einer typschnell Ansicht und einem benutzerdefinierten Viewer handelt und welche Rolle die Ausdrucks Auswertung bei der Unterstützung von beidem spielt.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die wichtigsten Konzepte der debuggingarchitektur.  
  
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)  
 Erläutert die gleichzeitige Funktionsweise von de innerhalb von Code-, Dokumentations-und Ausdrucks Auswertungs Kontexten. Beschreibt für jeden der drei Kontexte den Speicherort, die Position oder die Auswertung, die für ihn relevant sind.  
  
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)  
 Enthält Links zu verschiedenen Debuggingaufgaben, z. b. das Starten eines Programms und Auswerten von Ausdrücken.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
