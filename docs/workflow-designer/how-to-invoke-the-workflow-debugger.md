---
title: "Vorgehensweise: Aufrufen des Workflow-Debuggers | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Vorgehensweise: Aufrufen des Workflow-Debuggers
Grundsätzlich debuggen Sie Workflows genau wie in anderen Visual Studio\-Programmiersprachen geschriebene Programme.Sie können den Workflowdebugger auf folgende Weise starten:  
  
-   Wählen Sie im Menü **Debuggen** die Option **An den Prozess anhängen**, um den ausgeführten Hostprozess für die Workflowinstanz auszuwählen.Dieses Verfahren entspricht dem Anhängen an einen Hostprozess in verwaltetem Code.  
  
-   Drücken Sie **F5**, um eine Instanz des Workflows neu auszuführen oder weiter auszuführen, nachdem ein Haltepunkt erreicht wurde.  
  
-   Verwenden Sie Remotedebuggen.Informationen über die Verwendung des Remotedebuggens finden Sie unter [Vorgehensweise: Aktivieren von Remotedebuggen](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
    > [!NOTE]
    >  Wenn die Workflowanwendung für die x86\-Architektur konzipiert ist und auf einem Computer gehostet wird, auf dem ein 64\-Bit\-Betriebssystem ausgeführt wird, funktioniert das Remotedebuggen nur, wenn [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] auf dem Remotecomputer installiert wird oder das Ziel für die Workflowanwendung zu **Beliebige CPU** geändert wird.  
  
### Schrittweises Durchlaufen des Codes  
  
-   **Einzelschritt**: Sie können mit **F11** eine Aktivität in Einzelschritten ausführen.Der Debugger führt alle definierten Handler in Einzelschritten aus.Ist kein Handler definiert, wird die Aktivität übersprungen. Bei zusammengesetzten Aktivitäten, die andere Aktivitäten enthalten, führen Sie die erste ausgeführte Aktivität in einem Einzelschritt aus.  
  
-   **Ausführen bis Rücksprung**: Sie können eine Aktivität mit **UMSCHALT\+F11** verlassen.Mit dem Verlassen einer Aktivität werden die aktuelle Aktivität und alle dazugehörigen gleichgeordneten Aktivitäten bis zum Abschluss ausgeführt.Der Debugger wird dann auf dem übergeordneten Element der aktuellen Aktivität unterbrochen.Bei der Ausführung bis zum Rücksprung von einem Codehandler unterbricht der Debugger an der Aktivität, der der Handler zugewiesen ist.  
  
-   **Prozedurschritt**: Sie können mit **F10** für eine Aktivität einen Prozedurschritt ausführen.Wird ein Prozedurschritt für eine zusammengesetzte Aktivität ausgeführt, unterbricht der Debugger an der ersten ausführbaren untergeordneten Komponente der zusammengesetzten Aktivität.Wird ein Prozedurschritt für eine nicht zusammengesetzte Aktivität ausgeführt, zum Beispiel eine <xref:System.Activities.Statements.Assign>\-Aktivität, führt der Debugger die Aktivität und die dazugehörigen Handler aus und unterbricht an der nächsten Aktivität.Handelt es sich bei der ausgeführten Aktivität um die letzte untergeordnete Aktivität einer zusammengesetzten Aktivität, hält der Debugger nach der Ausführung an der übergeordneten Aktivität an.  
  
### Debuggen mit F5  
  
-   Wenn Sie ein Workflow\-Konsolenanwendungsprojekt erstellen, drücken Sie einfach **F5**, um mit dem Debuggen der Anwendung und des Workflows zu beginnen.Wenn Sie eine Aktivitätsbibliothek erstellen, muss eine ausführbare Hostanwendung als Startprojekt gegeben sein.Zum Festlegen eines Startprojekts im **Projektmappen\-Explorer** klicken Sie mit der rechten Maustaste auf den Projektnamen und wählen anschließend **Als Startprojekt festlegen** aus.  
  
## Siehe auch  
 [Vorgehensweise: Festlegen von Haltepunkten in Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [Debuggen von Workflows mit dem Workflow\-Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)