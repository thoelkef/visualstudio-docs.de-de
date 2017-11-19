---
title: "Vorgehensweise: Debuggen von ASP.NET-basierten Workflows (Vorgängerversion) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0eb248f04119f8f0ad70b9a09a4fb22c73399233
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Vorgehensweise: Debuggen von ASP.NET-basierten Workflows (Vorgängerversion)
In diesem Thema wird das Debuggen von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-basierten [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]-Anwendungen in der Vorgängerversion von [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] beschrieben, die auf [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] oder [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] abzielen.  
  
 Sie können Legacyworkflows debuggen, die in ASP.NET gestartet wurden, oder Legacyworkflows, die durch Anhängen an den Prozess, in dem der Workflow gehostet ist, als Webdienst veröffentlicht wurden.  
  
### <a name="to-debug-an-aspnet-based-workflow"></a>So debuggen Sie einen ASP.NET-basierten Workflow  
  
1.  Aktivieren Sie das Debuggen für die ASP.NET-Anwendung durch Festlegen von **debug = "true"** in der Datei "Web.config".  
  
2.  Legen Sie die Workflowbibliothek als Startprojekt fest, und legen Sie dann Haltepunkte auf dem Workflow fest.  
  
3.  Geben Sie die URL der Standardwebseite in den workflowprojekteigenschaften **Debuggen** Option **Start Browser mit externer URL** Textfeld.  
  
4.  Wählen Sie **an den Prozess anhängen** auf die **Debuggen** Menü.  
  
5.  Wählen Sie den Prozess anfügen, aus der **verfügbare Prozesse** Liste.  
  
     Hängen Sie an den w3wp.exe-, den webdev.webserver- oder den aspnet_wp-Prozess an, an dem der Workflow gehostet ist.  
  
6.  Klicken Sie auf **wählen** neben der **Anhängen an** Textfeld.  
  
     Die **Codetyp auswählen** Dialogfeld wird angezeigt.  
  
7.  Wählen Sie **diese Codetypen debuggen** , und wählen Sie **Workflow**.  
  
8.  Klicken Sie auf **OK**.  
  
9. Klicken Sie auf **Anfügen**aus.  
  
10. Öffnen Sie die Standardwebseite in einem Browser, und starten Sie den Workflow.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Visual Studio-Debugger für Windows Workflow Foundation (Vorgängerversion)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Vorgehensweise: Festlegen von Haltepunkten in Workflows (Vorgängerversion)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)