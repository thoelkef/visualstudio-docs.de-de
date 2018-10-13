---
title: 'Vorgehensweise: Debuggen von ASP.NET-basierten Workflows (Vorgängerversion) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: b9da40b0b40216fc36ea45b199ecde9c6dc4a89d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236885"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Vorgehensweise: Debuggen von ASP.NET-basierten Workflows (Vorgängerversion)
In diesem Thema wird das Debuggen von [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-basierten [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen in der Vorgängerversion von [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] beschrieben, die auf [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] oder [!INCLUDE[wfd1](../includes/wfd1-md.md)] abzielen.  
  
 Sie können Legacyworkflows debuggen, die in ASP.NET gestartet wurden, oder Legacyworkflows, die durch Anhängen an den Prozess, in dem der Workflow gehostet ist, als Webdienst veröffentlicht wurden.  
  
### <a name="to-debug-an-aspnet-based-workflow"></a>So debuggen Sie einen ASP.NET-basierten Workflow  
  
1.  Aktivieren Sie das Debuggen für die ASP.NET-Anwendung durch Festlegen von **debug = "true"** in der Datei "Web.config".  
  
2.  Legen Sie die Workflowbibliothek als Startprojekt fest, und legen Sie dann Haltepunkte auf dem Workflow fest.  
  
3.  Geben Sie die URL der Standardwebseite in den workflowprojekteigenschaften **Debuggen** Option **Start Browser mit externer URL** Textfeld.  
  
4.  Wählen Sie **an den Prozess anhängen** auf die **Debuggen** Menü.  
  
5.  Wählen Sie den Prozess aus eine Verbindung mit der **verfügbare Prozesse** Liste.  
  
     Hängen Sie an den w3wp.exe-, den webdev.webserver- oder den aspnet_wp-Prozess an, an dem der Workflow gehostet ist.  
  
6.  Klicken Sie auf **wählen** neben der **Anhängen an** Textfeld.  
  
     Die **Codetyp auswählen** Dialogfeld wird angezeigt.  
  
7.  Wählen Sie **diese Codetypen debuggen** , und wählen Sie **Workflow**.  
  
8.  Klicken Sie auf **OK**.  
  
9. Klicken Sie auf **Anfügen**aus.  
  
10. Öffnen Sie die Standardwebseite in einem Browser, und starten Sie den Workflow.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen des Visual Studio-Debuggers für Windows Workflow Foundation (Vorgängerversion)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Vorgehensweise: Festlegen von Haltepunkten in Workflows (Vorgängerversion)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)