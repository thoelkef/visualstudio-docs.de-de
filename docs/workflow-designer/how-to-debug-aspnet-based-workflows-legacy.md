---
title: "Vorgehensweise: Debuggen von ASP.NET-basierten Workflows (Vorg&#228;ngerversion) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "ASP.NET-Workflows, Debuggen"
  - "ASP.NET, Debuggen von Workflows"
  - "Debuggen von Workflows, ASP.NET-Workflows"
  - "Debuggen, ASP.NET-Workflows"
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Vorgehensweise: Debuggen von ASP.NET-basierten Workflows (Vorg&#228;ngerversion)
In diesem Thema wird das Debuggen von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-basierten [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]\-Anwendungen in der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] beschrieben, die auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen.  
  
 Sie können Legacyworkflows debuggen, die in ASP.NET gestartet wurden, oder Legacyworkflows, die durch Anhängen an den Prozess, in dem der Workflow gehostet ist, als Webdienst veröffentlicht wurden.  
  
### So debuggen Sie einen ASP.NET\-basierten Workflow  
  
1.  Aktivieren Sie Debuggen für die ASP.NET\-Anwendung, indem Sie **debug \= true** in der Datei web.config festlegen.  
  
2.  Legen Sie die Workflowbibliothek als Startprojekt fest, und legen Sie dann Haltepunkte auf dem Workflow fest.  
  
3.  Geben Sie die URL der Standardwebseite in das Textfeld **Browser mit externer URL starten** der Option **Debuggen** für die Workflowprojekteigenschaften ein.  
  
4.  Wählen Sie im Menü **Debuggen** die Option **An den Prozess anhängen** aus.  
  
5.  Wählen Sie den Prozess, an den angehängt werden soll, aus der Liste **Verfügbare Prozesse** aus.  
  
     Hängen Sie an den w3wp.exe\-, den webdev.webserver\- oder den aspnet\_wp\-Prozess an, an dem der Workflow gehostet ist.  
  
6.  Klicken Sie neben dem Textfeld **Anhängen an** auf **Auswählen**.  
  
     Das Dialogfeld **Codetyp auswählen** wird aufgerufen.  
  
7.  Wählen Sie **Diese Codetypen debuggen** aus, und wählen Sie dann **Workflow**.  
  
8.  Klicken Sie auf **OK**.  
  
9. Klicken Sie auf **Anfügen**.  
  
10. Öffnen Sie die Standardwebseite in einem Browser, und starten Sie den Workflow.  
  
## Siehe auch  
 [Aufrufen des Visual Studio\-Debuggers für Windows Workflow Foundation \(Vorgängerversion\)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Vorgehensweise: Festlegen von Haltepunkten in Workflows \(Vorgängerversion\)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)