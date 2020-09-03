---
title: 'Vorgehensweise: Debuggen von ASP.NET-basierten Workflows (Legacy) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3bed38f5229cb489f663878759517480b48302c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668657"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Vorgehensweise: Debuggen von ASP.NET-basierten Workflows (Vorgängerversion)
In diesem Thema wird das Debuggen von [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-basierten [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen in der Vorgängerversion von [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] beschrieben, die auf [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] oder [!INCLUDE[wfd1](../includes/wfd1-md.md)] abzielen.

 Sie können Legacyworkflows debuggen, die in ASP.NET gestartet wurden, oder Legacyworkflows, die durch Anhängen an den Prozess, in dem der Workflow gehostet ist, als Webdienst veröffentlicht wurden.

### <a name="to-debug-an-aspnet-based-workflow"></a>So debuggen Sie einen ASP.NET-basierten Workflow

1. Aktivieren Sie das Debugging für die ASP.NET-Anwendung, indem Sie **Debug = true** in der web.config-Datei festlegen.

2. Legen Sie die Workflowbibliothek als Startprojekt fest, und legen Sie dann Haltepunkte auf dem Workflow fest.

3. Geben Sie im Textfeld Workflow Projekteigenschaften **Debugoption** **Browser mit externer URL starten** die URL der Standard Webseite ein.

4. Wählen Sie im Menü **Debuggen** die Option **an den Prozess anhängen** .

5. Wählen Sie den Prozess aus, an den Sie in der Liste **Verfügbare Prozesse** anhängen möchten.

     Hängen Sie an den w3wp.exe-, den webdev.webserver- oder den aspnet_wp-Prozess an, an dem der Workflow gehostet ist.

6. Klicken Sie neben dem Textfeld **Anhängen an auf** **auswählen** .

     Das Dialogfeld **Codetyp auswählen** wird angezeigt.

7. Wählen Sie **Diese Codetypen debuggen** und **Workflow**aus.

8. Klicken Sie auf **OK**.

9. Klicken Sie auf **Anfügen**aus.

10. Öffnen Sie die Standardwebseite in einem Browser, und starten Sie den Workflow.

## <a name="see-also"></a>Weitere Informationen
 [Aufrufen des Visual Studio-Debuggers für Windows Workflow Foundation (Legacy)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) Gewusst [wie: Festlegen von Haltepunkten in Workflows (Legacy)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [Debuggen von Legacy Workflows](../workflow-designer/debugging-legacy-workflows.md)