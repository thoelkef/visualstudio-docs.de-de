---
title: Debuggen von Legacyworkflows | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b98c520dc96b6f3c6467bbcaf8e48d9cff8791d2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60048735"
---
# <a name="debugging-legacy-workflows"></a>Debuggen von Legacyworkflows
Wenn Sie mit der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] in [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] arbeiten, um [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen für .NET Framework 3.0 oder 3.5 zu erstellen, können Sie die Workflows genau wie jedes andere Programm debuggen, indem Sie Haltepunkte festlegen, Anfügungen an Prozesse vornehmen und Threads und die Aufrufliste überprüfen. Sie haben auch die Möglichkeit, remote zu debuggen.  
  
> [!NOTE]
>  Wenn mehrere Visual Studio-Versionen auf dem Computer installiert und deinstalliert wurden, kann das WF3-Debuggen aus einem der beiden folgenden Gründe fehlschlagen:  
> 
> - Die Haltepunkte werden nicht erreicht.  
>   - Folgende Meldung wird angezeigt:  
> 
>   **Debuggen kann nicht auf dem Webserver. Der Debugger ist nicht ordnungsgemäß installiert.  Der angeforderte Codetyp kann nicht debuggt werden.  Führen Sie Setup zum Installieren oder reparieren den Debugger an.**  
> 
>   Wenn eines dieser Szenarien beim Debuggen von .NET Framework 3.0- oder 3.5-Workflows auftritt, führen Sie eine Reparatur der Visual Studio-Installation aus.  
  
 [!INCLUDE[wf2](../includes/wf2-md.md)] kann in die folgenden standardmäßigen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Debugfenster integriert werden:  
  
- **Breakpoint**: Wie erwartet funktioniert, aber es eine Aktivität für den Namen der Funktion anzugeben.  
  
- **Aufrufliste**: So geben Sie einen Überblick über die Aktivitäten, die in einer Workflowinstanz ausgeführt wurden geändert. Die Einträge in der **Aufrufliste** Fenster sind eine Tiefensuche der ausgeführten Aktivitäten. Sie können auf einen Eintrag doppelklicken, um den Fokus auf die ausgewählte Aktivität zu lenken.  
  
- **Threads**: Stellt die Instanz-ID der Workflowinstanz, die gedebuggt wird.  
  
  Die folgenden Debugfunktionen werden von Visual Studio für Windows Workflow Foundation nicht unterstützt.  
  
- Bedingte Haltepunkte auf der Entwurfsoberfläche  
  
- Schnellüberwachung  
  
- Nächste Anweisung festlegen  
  
- Ausführen bis Cursor  
  
- Bearbeiten und Fortfahren  
  
- Just-In-Time-Debuggen  
  
- Debuggen im gemischten Modus  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Aufrufen des Visual Studio-Debuggers für Windows Workflow Foundation (Vorgängerversion)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Deaktivieren des Visual Studio-Debuggers für Windows Workflow Foundation (Vorgängerversion)](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Vorgehensweise: Debuggen von ASP.NET-basierten Workflows (Vorgängerversion)](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)  
  
 [Vorgehensweise: Festlegen von Haltepunkten in Workflows (Vorgängerversion)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)  
  
 [Debuggen von Workflows von einem Remotecomputer (Vorgängerversion)](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)  
  
 [Optionen zum schrittweisen Debuggen (Vorgängerversion)](../workflow-designer/debug-stepping-options-legacy.md)  
  
 [Vorgehensweise: Ändern der Option zum schrittweisen Debuggen (Vorgängerversion)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)