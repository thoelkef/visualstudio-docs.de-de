---
title: 'Workflow-Designer - Vorgehensweise: Debuggen von ASP.NET-basierten Workflows (Vorgängerversion)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 7bf16a6a88c5d4cd063f1c32ca846031d8b2588d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Vorgehensweise: Debuggen von ASP.NET-basierten Workflows (Vorgängerversion)

Dieses Thema beschreibt das Debuggen von ASP.NET-basierten Windows Workflow Foundation (WF)-Anwendungen, die entweder das .NET Framework Version 3.5 auf oder die WinFX in älteren Windows Workflow-Designer.

Sie können Legacyworkflows debuggen, die in ASP.NET gestartet wurden, oder Legacyworkflows, die durch Anhängen an den Prozess, in dem der Workflow gehostet ist, als Webdienst veröffentlicht wurden.

## <a name="to-debug-an-aspnet-based-workflow"></a>So debuggen Sie einen ASP.NET-basierten Workflow

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

- [Aufrufen des Visual Studio-Debuggers für Windows Workflow Foundation (Vorgängerversion)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
- [Vorgehensweise: Festlegen von Haltepunkten in Workflows (Vorgängerversion)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)
- [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)