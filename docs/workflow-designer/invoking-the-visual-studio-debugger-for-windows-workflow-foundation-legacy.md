---
title: Aufrufen von Visual Studio-Debugger für Windows Workflow Foundation (Vorgängerversion) | Microsoft Docs
ms.date: 11/04/2016
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e3563b175359e00a051138451292eb015958480
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Aufrufen des Visual Studio-Debuggers für Windows Workflow Foundation (Vorgängerversion)
In diesem Thema wird beschrieben, wie die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Debugger zum Debuggen [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] Anwendungen in älteren Windows Workflow-Designer. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen möchten.

 Grundsätzlich debuggen Sie Workflows der Vorgängerversion genau wie in anderen Visual Studio-Programmiersprachen geschriebene Programme. Sie können den [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)]-Debugger für Windows Workflow Foundation folgendermaßen starten:

-   Wählen Sie **an den Prozess anhängen** auf die **Debuggen** Menü der verfügbaren Prozesse einer ausgeführten Workflowinstanz aus.

-   Drücken Sie **F5** um mit einer Instanz des Workflows neu auszuführen oder weiter auszuführen, nachdem ein Haltepunkt erreicht wurde.

## <a name="stepping-through-code"></a>Schrittweises Ausführen von Code
 Der Debugger unterstützt eine der gängigsten Debugprozeduren, das zeilenweise Ausführen von Code. Für das schrittweise Ausführen von Code stehen drei Befehle zur Verfügung:

-   **Schritt In**: Sie können in eine Aktivität mit einem Einzelschritt **F11**. Der Debugger führt alle definierten Handler in Einzelschritten aus. Ist kein Handler definiert, wird die Aktivität übersprungen. Bei zusammengesetzten Aktivitäten, die andere Aktivitäten enthalten, führen Sie die erste ausgeführte Aktivität in einem Einzelschritt aus. Codehandlern vom Designer wird nicht unterstützt für die folgenden Aktivitäten: **IfElseActivity**, **WhileActivity**, **ConditionedActivityGroup**, oder die **ReplicatorActivity**. Um die diesen Aktivitäten zugeordneten Handler zu debuggen, müssen Sie explizite Haltepunkte im Code setzen.

-   **Ausführen bis Rücksprung**: Sie können eine Aktivität mit schrittweise **UMSCHALT + F11**. Mit dem Verlassen einer Aktivität werden die aktuelle Aktivität und alle dazugehörigen gleichgeordneten Aktivitäten bis zum Abschluss ausgeführt. Der Debugger wird dann auf dem übergeordneten Element der aktuellen Aktivität unterbrochen. Bei der Ausführung bis zum Rücksprung von einem Codehandler unterbricht der Debugger an der Aktivität, der der Handler zugewiesen ist.

-   **Prozedurschritt**: Sie können eine Aktivität mit Prozedurschritt **F10**. Wird ein Prozedurschritt für eine zusammengesetzte Aktivität ausgeführt, unterbricht der Debugger an der ersten ausführbaren untergeordneten Komponente der zusammengesetzten Aktivität. Prozedurschritt für eine nicht zusammengesetzte, z. B. eine **CodeActivity** Aktivität, führt der Debugger die Aktivität sowie der zugeordneten Handler und hält an der nächsten Aktivität. Handelt es sich bei der ausgeführten Aktivität um die letzte untergeordnete Aktivität einer zusammengesetzten Aktivität, hält der Debugger nach der Ausführung an der übergeordneten Aktivität an.

## <a name="attaching-to-a-process"></a>Anhängen an einen Prozess
 Wählen Sie zum Debuggen eines Workflows durch Anhängen eines Prozesses den verfügbaren Prozess aus dem **verfügbare Prozesse** Listenfeld in der **an den Prozess anhängen** (Dialogfeld). Wenn **automatisch: Workflowcode** wird nicht angezeigt, der **zuordnen** Text Feld, und klicken Sie auf **wählen**. In der **Codetyp auswählen** (Dialogfeld), klicken Sie auf **diese Codetypen debuggen** , und wählen Sie **Workflow**. Klicken Sie dann auf **OK** , und klicken Sie auf **Anfügen**.

## <a name="debugging-with-f5"></a>Debuggen mit F5
 Wenn eine workflowhostanwendung und Workflow-DLL in verschiedenen Visual Studio-Projekten, z. B. befinden, wenn Sie eine workflowaktivitätsbibliothek verwenden, müssen Sie das Workflow-DLL-Projekt als Startprojekt Visual Studio-Lösung, um den Workflow zu Debuggen festlegen mit **F5**. Sie müssen auch den Pfad zur hostanwendung des Workflow-DLL-Projekts festlegen **externes Programm starten** Eigenschaft.

 Klicken Sie zum Festlegen eines Startprojekts im Projektmappen-Explorer mit der rechten Maustaste des Projektnamens, und wählen Sie **als Startprojekt festlegen**. Festzulegende des Pfads zum Host in der **externes Programm starten** -Eigenschaft, doppelklicken Sie auf des Workflowprojekt **Eigenschaften** Knoten im Projektmappen-Explorer, und wählen die **Debuggen** Registerkarte ". Klicken Sie unter **Startaktion**Option **externes Programm starten** und geben Sie den Pfad zur .exe-Datei, die den Workflow hostet Sie debuggen möchten.

 Wird die Hostanwendung als Startprojekt festgelegt, wird nur der Visual Studio-Debugger zum Debuggen aufgerufen. Der [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)]-Debugger für Windows Workflow Foundation wird nicht aufgerufen. Wird der Visual Studio-Debugger verwendet, werden nur C#- oder Visual Basic-Codehaltepunkte erreicht, im Workflow-Designer festgelegte Haltepunkte werden nicht erreicht. So wird beispielsweise ein für eine <xref:System.Workflow.Activities.ParallelActivity>-Aktivität im Designer festgelegter Haltepunkt mit dem [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)]-Debugger für Windows Workflow Foundation erreicht, nicht jedoch mit dem Visual Studio-Debugger.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Festlegen von Haltepunkten in Workflows (Vorgängerversion)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)
- [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)