---
title: "Aufrufen des Visual Studio-Debuggers f&#252;r Windows Workflow Foundation (Vorg&#228;ngerversion) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Debugger, Workflow"
  - "Debuggen von Workflows, Starten des Debuggers"
  - "Debuggen, Verwenden des Workflowdebuggers"
  - "Einzelschritt (Befehl)"
  - "Ausführen bis Rücksprung (Befehl)"
  - "Prozedurschritt (Befehl)"
  - "schrittweises Ausführen"
  - "schrittweises Ausführen, Befehle"
  - "Debuggen von Workflows, Starten"
  - "Workflows, Debugger"
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Aufrufen des Visual Studio-Debuggers f&#252;r Windows Workflow Foundation (Vorg&#228;ngerversion)
In diesem Thema wird die Verwendung des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Debuggers zum Debuggen von [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]\-Anwendungen in der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] beschrieben.Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen möchten.  
  
 Grundsätzlich debuggen Sie Workflows der Vorgängerversion genau wie in anderen Visual Studio\-Programmiersprachen geschriebene Programme.Sie können den [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)]\-Debugger für Windows Workflow Foundation folgendermaßen starten:  
  
-   Wählen Sie im Menü **Debuggen** die Option **An den Prozess anhängen**, um eine ausgeführte Workflowinstanz für die verfügbaren Prozesse auszuwählen.  
  
-   Drücken Sie **F5**, um eine Instanz des Workflows neu auszuführen oder weiter auszuführen, nachdem ein Haltepunkt erreicht wurde.  
  
## Schrittweises Ausführen von Code  
 Der Debugger unterstützt eine der gängigsten Debugprozeduren, das zeilenweise Ausführen von Code.Für das schrittweise Ausführen von Code stehen drei Befehle zur Verfügung:  
  
-   **Einzelschritt**: Sie können mit **F11** eine Aktivität in Einzelschritten ausführen.Der Debugger führt alle definierten Handler in Einzelschritten aus.Ist kein Handler definiert, wird die Aktivität übersprungen. Bei zusammengesetzten Aktivitäten, die andere Aktivitäten enthalten, führen Sie die erste ausgeführte Aktivität in einem Einzelschritt aus.Für die nachstehenden Aktivitäten wird die schrittweise Ausführung von Codehandlern vom Designer nicht unterstützt: **IfElseActivity**, **WhileActivity**, **ConditionedActivityGroup** oder **ReplicatorActivity**.Um die diesen Aktivitäten zugeordneten Handler zu debuggen, müssen Sie explizite Haltepunkte im Code setzen.  
  
-   **Ausführen bis Rücksprung**: Sie können eine Aktivität mit **Shift\-F11** verlassen.Mit dem Verlassen einer Aktivität werden die aktuelle Aktivität und alle dazugehörigen gleichgeordneten Aktivitäten bis zum Abschluss ausgeführt.Der Debugger wird dann auf dem übergeordneten Element der aktuellen Aktivität unterbrochen.Bei der Ausführung bis zum Rücksprung von einem Codehandler unterbricht der Debugger an der Aktivität, der der Handler zugewiesen ist.  
  
-   **Prozedurschritt**: Sie können mit **F10** für eine Aktivität einen Prozedurschritt ausführen.Wird ein Prozedurschritt für eine zusammengesetzte Aktivität ausgeführt,unterbricht der Debugger an der ersten ausführbaren untergeordneten Komponente der zusammengesetzten Aktivität.Wird ein Prozedurschritt für eine nicht zusammengesetzte Aktivität ausgeführt, wie zum Beispiel eine **CodeActivity**\-Aktivität, führt der Debugger die Aktivität und die dazugehörigen Handler aus und unterbricht an der nächsten Aktivität.Handelt es sich bei der ausgeführten Aktivität um die letzte untergeordnete Aktivität einer zusammengesetzten Aktivität, hält der Debugger nach der Ausführung an der übergeordneten Aktivität an.  
  
## Anhängen an einen Prozess  
 Wählen Sie zum Debuggen eines Workflows durch Anhängen eines Prozesses den verfügbaren Prozess aus dem Listenfeld **Verfügbare Prozesse** des Dialogfelds **An den Prozess anhängen** aus.Wird **Automatisch: Workflowcode** nicht im Textfeld **Anhängen an** angezeigt, klicken Sie auf **Auswählen**.Klicken Sie im Dialogfeld **Codetyp auswählen** auf **Diese Codetypen debuggen**, und wählen Sie **Workflow** aus.Klicken Sie dann auf **OK** und anschließend auf **Anhängen**.  
  
## Debuggen mit F5  
 Befinden sich eine Workflowhostanwendung und eine Workflow\-DLL in verschiedenen Visual Studio\-Projekten, beispielsweise, wenn Sie eine Workflowaktivitätsbibliothek verwenden, müssen Sie das Workflow\-DLL\-Projekt als Visual Studio\-Lösungsstartprojekt festlegen, um den Workflow mit **F5** zu debuggen.Sie müssen außerdem den Pfad zur Hostanwendung in der **Externes Programm starten**\-Eigenschaft des Workflow\-DLL\-Projekts festlegen.  
  
 Zum Festlegen eines Startprojekts im Projektmappen\-Explorer klicken Sie mit der rechten Maustaste auf den Projektnamen und wählen anschließend **Als Startprojekt festlegen** aus.Zum Festlegen des Pfads zum Host in der **Externes Programm starten**\-Eigenschaft des Workflowprojekts doppelklicken Sie auf den **Eigenschaften**\-Knoten des Workflowprojekts im Projektmappen\-Explorer und wählen die Registerkarte **Debuggen** aus.Wählen Sie unter **Startaktion** die Option **Externes Programm starten**, und geben Sie den Pfad zur .exe\-Datei ein, die den zu debuggenden Workflow hostet.  
  
 Wird die Hostanwendung als Startprojekt festgelegt, wird nur der Visual Studio\-Debugger zum Debuggen aufgerufen. Der [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)]\-Debugger für Windows Workflow Foundation wird nicht aufgerufen.Wird der Visual Studio\-Debugger verwendet, werden nur C\#\- oder Visual Basic\-Codehaltepunkte erreicht, im Workflow\-Designer festgelegte Haltepunkte werden nicht erreicht.So wird beispielsweise ein für eine <xref:System.Workflow.Activities.ParallelActivity>\-Aktivität im Designer festgelegter Haltepunkt mit dem [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)]\-Debugger für Windows Workflow Foundation erreicht, nicht jedoch mit dem Visual Studio\-Debugger.  
  
## Siehe auch  
 [Vorgehensweise: Festlegen von Haltepunkten in Workflows \(Vorgängerversion\)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)