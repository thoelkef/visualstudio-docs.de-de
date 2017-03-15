---
title: "Debuggen von Legacyworkflows | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Debuggen von Workflows"
  - "Debuggen, Workflows"
  - "Workflows, Debuggen"
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
caps.latest.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Debuggen von Legacyworkflows
Wenn Sie mit der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] in [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] arbeiten, um [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]\-Anwendungen für .NET Framework 3.0 oder 3.5 zu erstellen, können Sie die Workflows genau wie jedes andere Programm debuggen, indem Sie Haltepunkte festlegen, Anfügungen an Prozesse vornehmen und Threads und die Aufrufliste überprüfen.Sie haben auch die Möglichkeit, remote zu debuggen.  
  
> [!NOTE]
>  Wenn mehrere Visual Studio\-Versionen auf dem Computer installiert und deinstalliert wurden, kann das WF3\-Debuggen aus einem der beiden folgenden Gründe fehlschlagen:  
>   
>  -   Die Haltepunkte werden nicht erreicht.  
> -   Folgende Meldung wird angezeigt:  
>   
>  **Das Debuggen kann auf dem Webserver nicht gestartet werden.Der Debugger ist nicht ordnungsgemäß installiert.Der angeforderte Codetyp kann nicht debuggt werden.Führen Sie das Setup aus, um den Debugger zu installieren oder zu reparieren.**  
>   
>  Wenn eines dieser Szenarien beim Debuggen von .NET Framework 3.0\- oder 3.5\-Workflows auftritt, führen Sie eine Reparatur der Visual Studio\-Installation aus.  
  
 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] kann in die folgenden standardmäßigen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Debugfenster integriert werden:  
  
-   **Haltepunkt**: Funktioniert wie erwartet, Sie geben jedoch eine Aktivität für den Funktionsnamen an.  
  
-   **Aufrufliste**: Wurde geändert, um eine Gliederung der Aktivitäten bereitzustellen, die in einer Workflowinstanz ausgeführt wurden.Die Einträge im Fenster **Aufrufliste** stehen für eine Suche nach den tiefsten Elementen der ausgeführten Aktivitäten.Sie können auf einen Eintrag doppelklicken, um den Fokus auf die ausgewählte Aktivität zu lenken.  
  
-   **Threads**: Stellt die Instanz\-ID der Workflowinstanz bereit, die gedebuggt wird.  
  
 Die folgenden Debugfunktionen werden von Visual Studio für Windows Workflow Foundation nicht unterstützt.  
  
-   Bedingte Haltepunkte auf der Entwurfsoberfläche  
  
-   Schnellüberwachung  
  
-   Nächste Anweisung festlegen  
  
-   Ausführen bis Cursor  
  
-   Bearbeiten und Fortfahren  
  
-   Just\-In\-Time\-Debuggen  
  
-   Debuggen im gemischten Modus  
  
## In diesem Abschnitt  
 [Aufrufen des Visual Studio\-Debuggers für Windows Workflow Foundation \(Vorgängerversion\)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Deaktivieren des Visual Studio\-Debuggers für Windows Workflow Foundation \(Vorgängerversion\)](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Vorgehensweise: Debuggen von ASP.NET\-basierten Workflows \(Vorgängerversion\)](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)  
  
 [Vorgehensweise: Festlegen von Haltepunkten in Workflows \(Vorgängerversion\)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)  
  
 [Debuggen von Workflows von einem Remotecomputer \(Vorgängerversion\)](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)  
  
 [Optionen zum schrittweisen Debuggen \(Vorgängerversion\)](../workflow-designer/debug-stepping-options-legacy.md)  
  
 [Vorgehensweise: Ändern der Option zum schrittweisen Debuggen \(Vorgängerversion\)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)