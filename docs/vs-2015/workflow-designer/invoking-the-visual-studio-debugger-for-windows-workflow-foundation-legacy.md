---
title: Aufrufen des Visual Studio-Debuggers für Windows Workflow Foundation (Vorgängerversion) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stepping
- Step Over command
- stepping, commands
- debugging, using workflow debugger
- workflows, debugger
- workflow debugger, starting
- Step In command
- debugger, workflow
- Step Out command
- debugging workflows, starting the debugger
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f5fd785de6db5bb951088e56fe13a6d63650bf92
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306097"
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Aufrufen des Visual Studio-Debuggers für Windows Workflow Foundation (Vorgängerversion)
In diesem Thema wird die Verwendung des [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Debuggers zum Debuggen von [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen in der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] beschrieben. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.  
  
 Grundsätzlich debuggen Sie Workflows der Vorgängerversion genau wie in anderen Visual Studio-Programmiersprachen geschriebene Programme. Sie können den [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)]-Debugger für Windows Workflow Foundation folgendermaßen starten:  
  
-   Wählen Sie **an den Prozess anhängen** auf die **Debuggen** im Menü der verfügbaren Prozesse einer ausgeführten Workflowinstanz aus.  
  
-   Drücken Sie **F5** um eine Instanz des Workflows zu starten oder weiter ausgeführt, nachdem ein Haltepunkt erreicht wurde.  
  
## <a name="stepping-through-code"></a>Schrittweises Ausführen von Code  
 Der Debugger unterstützt eine der gängigsten Debugprozeduren, das zeilenweise Ausführen von Code. Für das schrittweise Ausführen von Code stehen drei Befehle zur Verfügung:  
  
-   **Schritt In**: Sie einen Einzelschritt in eine Aktivität mit **F11**. Der Debugger führt alle definierten Handler in Einzelschritten aus. Ist kein Handler definiert, wird die Aktivität übersprungen. Bei zusammengesetzten Aktivitäten, die andere Aktivitäten enthalten, führen Sie die erste ausgeführte Aktivität in einem Einzelschritt aus. Codehandlern vom Designer wird nicht unterstützt für die folgenden Aktivitäten: **Aktivität "IfElseActivity"**, **WhileActivity**, **ConditionedActivityGroup**, oder **ReplicatorActivity**. Um die diesen Aktivitäten zugeordneten Handler zu debuggen, müssen Sie explizite Haltepunkte im Code setzen.  
  
-   **Ausführen bis Rücksprung**: Sie können eine Aktivität mit Rücksprung **UMSCHALT + F11**. Mit dem Verlassen einer Aktivität werden die aktuelle Aktivität und alle dazugehörigen gleichgeordneten Aktivitäten bis zum Abschluss ausgeführt. Der Debugger wird dann auf dem übergeordneten Element der aktuellen Aktivität unterbrochen. Bei der Ausführung bis zum Rücksprung von einem Codehandler unterbricht der Debugger an der Aktivität, der der Handler zugewiesen ist.  
  
-   **Prozedurschritt**: Sie können eine Aktivität mit überspringen **F10**. Wird ein Prozedurschritt für eine zusammengesetzte Aktivität ausgeführt, unterbricht der Debugger an der ersten ausführbaren untergeordneten Komponente der zusammengesetzten Aktivität. Prozedurschritt für eine nicht zusammengesetzte, z. B. eine **CodeActivity** Aktivität, führt der Debugger die Aktivität und die zugeordneten Handler und unterbricht an der nächsten Aktivität. Handelt es sich bei der ausgeführten Aktivität um die letzte untergeordnete Aktivität einer zusammengesetzten Aktivität, hält der Debugger nach der Ausführung an der übergeordneten Aktivität an.  
  
## <a name="attaching-to-a-process"></a>Anhängen an einen Prozess  
 Wählen Sie den verfügbaren Prozess aus, um einen Workflow Debuggen durch Anhängen an einen Prozess, der **verfügbare Prozesse** Listenfeld in der **an den Prozess anhängen** Dialogfeld. Wenn **automatisch: Workflowcode** wird nicht angezeigt, der **Anfügen an** Text, und klicken Sie dann **wählen**. In der **Codetyp auswählen** Dialogfeld klicken Sie auf **diese Codetypen debuggen** , und wählen Sie **Workflow**. Klicken Sie dann auf **OK** , und klicken Sie auf **Anfügen**.  
  
## <a name="debugging-with-f5"></a>Debuggen mit F5  
 Wenn sich eine workflowhostanwendung und eine Workflow-DLL in verschiedenen Visual Studio-Projekten, z. B. befinden, wenn Sie eine workflowaktivitätsbibliothek verwenden, müssen Sie das Workflow-DLL-Projekt als die Visual Studio-lösungsstartprojekt So debuggen Sie den Workflow festlegen Mithilfe von **F5**. Sie müssen auch den Pfad festlegen, an die hostanwendung in des Workflow-DLL-Projekts **externes Programm starten** Eigenschaft.  
  
 Klicken Sie zum Festlegen eines Startprojekts im Projektmappen-Explorer mit der rechten Maustaste in des Namens des Projekts, und wählen Sie **als Startprojekt festlegen**. Den Pfad für den Host festgelegt die **externes Programm starten** -Eigenschaft, doppelklicken Sie auf des Workflowprojekts **Eigenschaften** Knoten im Projektmappen-Explorer, und wählen die **Debuggen** Registerkarte ". Klicken Sie unter **Startaktion**Option **externes Programm starten** , und geben Sie den Pfad zur .exe-Datei, die den Workflow hostet Sie debuggen möchten.  
  
 Wird die Hostanwendung als Startprojekt festgelegt, wird nur der Visual Studio-Debugger zum Debuggen aufgerufen. Der [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)]-Debugger für Windows Workflow Foundation wird nicht aufgerufen. Wird der Visual Studio-Debugger verwendet, werden nur C#- oder Visual Basic-Codehaltepunkte erreicht, im Workflow-Designer festgelegte Haltepunkte werden nicht erreicht. So wird beispielsweise ein für eine <xref:System.Workflow.Activities.ParallelActivity>-Aktivität im Designer festgelegter Haltepunkt mit dem [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)]-Debugger für Windows Workflow Foundation erreicht, nicht jedoch mit dem Visual Studio-Debugger.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Festlegen von Haltepunkten in Workflows (Vorgängerversion)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)