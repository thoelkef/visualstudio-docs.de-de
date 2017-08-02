---
title: "Debuggerkomponenten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Visual Studio], Komponenten"
  - "Komponenten [Visual Studio SDK] Debuggen"
  - "die Komponenten zum Remotedebuggen [Debugging-SDK]"
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 30
---
# Debuggerkomponenten
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger wird als VSPackage implementieren und die gesamte Debugsitzung verwaltet.  Die Debugsitzung enthält die folgenden Elemente:  
  
-   **Debuggen Paket:** Der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger bietet die gleiche Benutzeroberfläche bereit, unabhängig davon, welche gedebuggt wird.  
  
-   **Multithreaded Manager der Sitzung \(SDM\):** Stellt eine konsistente programmgesteuerte Schnittstelle zum [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger für die Verwaltung einer Vielzahl von Debugmodule bereit.  Sie wird von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]implementiert.  
  
-   **Debuggen des Prozesses Manager \(PDM\):** Verwaltet, für alle ausgeführten Instanzen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]eine Liste aller Programme, die verbunden werden können oder gedebuggt werden.  Er wird von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]implementiert.  
  
-   **Modul \(Debug\): DE** Ist zum Überwachen eines Programms, das gedebuggt wird, mitteilend den Zustand des ausgeführten Programms auf den SDM und PDM und interagierend mit dem Hersteller dem angegebenen Symbol und der Ausdrucksauswertung zur Echtzeit Analyse des Zustands des Arbeitsspeichers und der Variablen eines Programms bereitzustellen.  Es wird von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(für die Sprachen, die sie unterstützt\) und von Drittanbietern implementiert, die die eigene Common Language Runtime unterstützen möchten.  
  
-   **Ausdrucksauswertung \(EE\):** Bietet Unterstützung für Variablen und Ausdrücke auswerten dynamisch vom Benutzer angegeben werden, wenn ein Programm zu einem bestimmten Zeitpunkt beendet wurde.  Sie wird von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(für die Sprachen, die sie unterstützt\) und von Drittanbietern implementiert, die ihre eigenen Sprachen unterstützen möchten.  
  
-   **Symbol für \(SP\):** Rief auch ein Symbol zuordnet, für die Debugsymbole eines Programms an eine ausgeführte Instanz des Programms an, damit sinnvolle Informationen zur Verfügung gestellt werden können \(z. B. Debuggen und Ausdrucksauswertung SOURCE\-Code LEVELs\).  Es wird von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementiert \(für die Symbole der Common Language Runtime \[CLR\] und das Symbol dateiformat der Programmdatenbank \[PDB\]\) und von Drittanbietern, die ihre eigene herstellereigene Methode zum Speichern von Debuginformationen besitzen.  
  
 Das folgende Diagramm zeigt die Beziehung mit diesen Elementen des Visual Studio\-Debuggers an.  
  
 ![Übersicht über das Debuggen von Komponenten](~/docs/extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## In diesem Abschnitt  
 [Debug\-Paket](../../extensibility/debugger/debug-package.md)  
 Erläutert das Debuggen Paket, das in die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell ausgeführt wird und die übrigen Benutzeroberfläche behandelt.  
  
 [Prozess\-Debug\-Manager](../../extensibility/debugger/process-debug-manager.md)  
 Bietet eine Übersicht über die Funktionen des PDM bereit, das der Manager der Prozesse, die gedebuggt werden kann.  
  
 [Session\-Debug\-Manager](../../extensibility/debugger/session-debug-manager.md)  
 Definiert das SDM, das eine einheitliche Sicht der Debugsitzung in der IDE bereitgestellt werden.  Das SDM verwaltet. DE  
  
 [Debug\-Modul](../../extensibility/debugger/debug-engine.md)  
 Dokumentiert die Debugdienste, die DE bereitstellt.  
  
 [Betriebsmodi](../../extensibility/debugger/operational-modes.md)  
 Bietet eine Übersicht über die drei Modi bereit, in denen die IDE verwendet werden kann: Entwurfsmodus, Unterbrechungs\- und Ausführmodus.  Überträgt werden ebenfalls Mechanismen besprochen.  
  
 [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator.md)  
 Erläutert den Zweck von EE zur Laufzeit.  
  
 [Symbol\-Anbieter](../../extensibility/debugger/symbol-provider.md)  
 Erläutert, wie bei der Implementierung der Anbieter Symbol Variablen und Ausdrücke auswertet.  
  
 [Typ\-Schnellansicht und benutzerdefinierten Viewer](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 Erläutert, wie ein Typ schnellansicht und einem benutzerdefinierten Viewer sind und welche Rolle spielt, wenn er die Ausdrucksauswertung unterstützt sowohl.  
  
## Verwandte Abschnitte  
 [Debugger\-Konzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die Architektur wichtigsten Konzepte des Debuggens.  
  
 [Debugger\-Kontexte](../../extensibility/debugger/debugger-contexts.md)  
 Erläutert das DE gleichzeitig innerhalb des Codes, der Dokumentation und den Ausdrucksauswertungs kontexte funktioniert.  Beschreibt für jede der drei Kontexten, des Speicherorts, der Position oder der Auswertung, die relevant ist.  
  
 [Debugging\-Aufgaben](../../extensibility/debugger/debugging-tasks.md)  
 Enthält Links zu den verschiedenen Aufgaben Debuggen eines Programms starten, z und Auswerten von Ausdrücken.  
  
## Siehe auch  
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)