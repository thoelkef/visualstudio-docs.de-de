---
title: Aufrufen des Debuggers für Windows Workflow Foundation (Legacy) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bcceca362f3c2a891d36f8f4e8071d0e35c8f164
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658977"
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Aufrufen des Visual Studio-Debuggers für Windows Workflow Foundation (Vorgängerversion)
In diesem Thema wird die Verwendung des [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Debuggers zum Debuggen von [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen in der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] beschrieben. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.

 Grundsätzlich debuggen Sie Workflows der Vorgängerversion genau wie in anderen Visual Studio-Programmiersprachen geschriebene Programme. Sie können den [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)]-Debugger für Windows Workflow Foundation folgendermaßen starten:

- Wählen Sie im Menü **Debuggen** die Option **an den Prozess anhängen** , um eine ausgelaufende Workflow Instanz aus den verfügbaren Prozessen auszuwählen.

- Drücken Sie **F5** , um die Ausführung einer Instanz des Workflows zu starten, oder, um die Ausführung nach dem Erreichen eines Breakpoints fortzusetzen.

## <a name="stepping-through-code"></a>Schrittweises Ausführen von Code
 Der Debugger unterstützt eine der gängigsten Debugprozeduren, das zeilenweise Ausführen von Code. Für das schrittweise Ausführen von Code stehen drei Befehle zur Verfügung:

- Einzel **Schritt**: Sie können mit **F11**eine Aktivität in Einzelschritten ausführen. Der Debugger führt alle definierten Handler in Einzelschritten aus. Ist kein Handler definiert, wird die Aktivität übersprungen. Bei zusammengesetzten Aktivitäten, die andere Aktivitäten enthalten, führen Sie die erste ausgeführte Aktivität in einem Einzelschritt aus. Das Ausführen eines durch Laufens von Code Handlern aus dem Designer wird für die folgenden Aktivitäten nicht unterstützt: **IfElseActivity**, **WhileActivity**, **ConditionedActivityGroup**oder **repligatoractivity**. Um die diesen Aktivitäten zugeordneten Handler zu debuggen, müssen Sie explizite Haltepunkte im Code setzen.

- Rück **Sprung**: Sie können eine Aktivität mit **UMSCHALT + F11**schrittweise ausführen. Mit dem Verlassen einer Aktivität werden die aktuelle Aktivität und alle dazugehörigen gleichgeordneten Aktivitäten bis zum Abschluss ausgeführt. Der Debugger wird dann auf dem übergeordneten Element der aktuellen Aktivität unterbrochen. Bei der Ausführung bis zum Rücksprung von einem Codehandler unterbricht der Debugger an der Aktivität, der der Handler zugewiesen ist.

- Prozedur **Schritt**: Sie können eine Aktivität mithilfe von **F10**überspringen. Wird ein Prozedurschritt für eine zusammengesetzte Aktivität ausgeführt, unterbricht der Debugger an der ersten ausführbaren untergeordneten Komponente der zusammengesetzten Aktivität. Beim Durchlaufen eines nicht zusammengesetzten, wie z. b. einer **CodeActivity** -Aktivität, führt der Debugger die Aktivität und die dazugehörigen Handler aus und unterbricht bei der nächsten Aktivität. Handelt es sich bei der ausgeführten Aktivität um die letzte untergeordnete Aktivität einer zusammengesetzten Aktivität, hält der Debugger nach der Ausführung an der übergeordneten Aktivität an.

## <a name="attaching-to-a-process"></a>Anhängen an einen Prozess
 Um einen Workflow durch Anhängen an einen Prozess zu debuggen, wählen Sie den verfügbaren Prozess im Listenfeld **Verfügbare Prozesse** im Dialogfeld **an den Prozess anhängen** aus. Wenn **automatisch: Workflow Code** wird im Textfeld **Anfügen an** nicht angezeigt. Klicken Sie dann auf **auswählen**. Klicken Sie im Dialogfeld **Codetyp auswählen** auf **Diese Codetypen debuggen** , und wählen Sie **Workflow**aus. Klicken Sie dann auf **OK** und dann auf **Anfügen**.

## <a name="debugging-with-f5"></a>Debuggen mit F5
 Wenn sich eine Workflow Host Anwendung und eine Workflow-dll in verschiedenen Visual Studio-Projekten befinden, z. b. Wenn Sie eine Workflow Aktivitäts Bibliothek verwenden, müssen Sie das Workflow-DLL-Projekt als Visual Studio-projektmappenstartprojekt festlegen, um den Workflow zu debuggen. mit **F5**. Sie müssen auch den Pfad zur Host Anwendung in der Eigenschaft **externes Programm starten** des Workflow-DLL-Projekts festlegen.

 Zum Festlegen eines Start Projekts in Projektmappen-Explorer klicken Sie mit der rechten Maustaste auf den Projektnamen, und wählen Sie **als Startprojekt festlegen**aus. Zum Festlegen des Pfads zum Host in der Eigenschaft **externes Programm starten** Doppelklicken Sie in Projektmappen-Explorer auf den Knoten **Eigenschaften** des Workflow Projekts, und wählen Sie die Registerkarte **Debuggen** aus. Wählen Sie unter **Start Aktion**die Option **externes Programm starten** aus, und geben Sie den Pfad zu der exe-Datei ein, die den zu debuggenden Workflow hostet.

 Wird die Hostanwendung als Startprojekt festgelegt, wird nur der Visual Studio-Debugger zum Debuggen aufgerufen. Der [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)]-Debugger für Windows Workflow Foundation wird nicht aufgerufen. Wird der Visual Studio-Debugger verwendet, werden nur C#- oder Visual Basic-Codehaltepunkte erreicht, im Workflow-Designer festgelegte Haltepunkte werden nicht erreicht. So wird beispielsweise ein für eine <xref:System.Workflow.Activities.ParallelActivity>-Aktivität im Designer festgelegter Haltepunkt mit dem [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)]-Debugger für Windows Workflow Foundation erreicht, nicht jedoch mit dem Visual Studio-Debugger.

## <a name="see-also"></a>Siehe auch
 Gewusst [wie: Festlegen von Haltepunkten in Workflows (Legacy)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [Debuggen von Legacy Workflows](../workflow-designer/debugging-legacy-workflows.md)