---
title: 'Vorgehensweise: Aufrufen des Workflow-Debuggers | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 6142e12da9a32ccb325c6a8a199f67599c7228c8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509935"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Vorgehensweise: Aufrufen des Workflow-Debuggers
Grundsätzlich debuggen Sie Workflows genau wie in anderen Visual Studio-Programmiersprachen geschriebene Programme. Sie können den Workflowdebugger auf folgende Weise starten:  
  
-   Wählen Sie **an den Prozess anhängen** auf die **Debuggen** Menü Wählen Sie den ausgeführten Hostprozess für Ihre Workflowinstanz. Dieses Verfahren entspricht dem Anhängen an einen Hostprozess in verwaltetem Code.  
  
-   Drücken Sie **F5** um eine Instanz des Workflows zu starten oder weiter ausgeführt, nachdem ein Haltepunkt erreicht wurde.  
  
-   Verwenden Sie Remotedebuggen. Weitere Informationen zur Verwendung des Remotedebuggens finden Sie unter [Vorgehensweise: Aktivieren von Remotedebuggen](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
    > [!NOTE]
    >  Wenn die workflowanwendung die X86 abzielt Architektur und gehostet wird, auf einem Computer unter einem 64-Bit-Betriebssystem, das Remotedebuggen funktioniert nur, wenn wird [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] auf dem Remotecomputer oder das Ziel installiert ist, für die workflowanwendung in geändert wird **Beliebige CPU**.  
  
### <a name="stepping-through-code"></a>Schrittweises Durchlaufen des Codes  
  
-   **Schritt In**: Sie einen Einzelschritt in eine Aktivität mit **F11**. Der Debugger führt alle definierten Handler in Einzelschritten aus. Ist kein Handler definiert, wird die Aktivität übersprungen. Bei zusammengesetzten Aktivitäten, die andere Aktivitäten enthalten, führen Sie die erste ausgeführte Aktivität in einem Einzelschritt aus.  
  
-   **Schritt-Out:** Rücksprung Sie können eine Aktivität mit **UMSCHALT + F11**. Mit dem Verlassen einer Aktivität werden die aktuelle Aktivität und alle dazugehörigen gleichgeordneten Aktivitäten bis zum Abschluss ausgeführt. Der Debugger wird dann auf dem übergeordneten Element der aktuellen Aktivität unterbrochen. Bei der Ausführung bis zum Rücksprung von einem Codehandler unterbricht der Debugger an der Aktivität, der der Handler zugewiesen ist.  
  
-   **Prozedurschritt**: Sie können eine Aktivität mit überspringen **F10**. Wird ein Prozedurschritt für eine zusammengesetzte Aktivität ausgeführt, unterbricht der Debugger an der ersten ausführbaren untergeordneten Komponente der zusammengesetzten Aktivität. Wird ein Prozedurschritt für eine nicht zusammengesetzte Aktivität ausgeführt, zum Beispiel eine <xref:System.Activities.Statements.Assign>-Aktivität, führt der Debugger die Aktivität und die dazugehörigen Handler aus und unterbricht an der nächsten Aktivität. Handelt es sich bei der ausgeführten Aktivität um die letzte untergeordnete Aktivität einer zusammengesetzten Aktivität, hält der Debugger nach der Ausführung an der übergeordneten Aktivität an.  
  
### <a name="debugging-with-f5"></a>Debuggen mit F5  
  
-   Wenn Sie ein Workflow-Konsolenanwendungsprojekt erstellen, drücken Sie einfach **F5** um Debuggen der Anwendung und den Workflow zu starten. Wenn Sie eine Aktivitätsbibliothek erstellen, muss eine ausführbare Hostanwendung als Startprojekt gegeben sein. Zum Festlegen eines Startprojekts im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektnamen, der den Host, und wählen Sie **als Startprojekt festlegen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Festlegen von Haltepunkten in Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [Debuggen von Workflows mit dem Workflow-Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)