---
title: Neues im Debugger in Visual Studio 2017 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0bcd44da88279f042469356a97bce7f369e1190
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="whats-new-for-the-debugger-in-includevsdev15miscincludesvsdev15mdmd"></a>Neues im Debugger in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Der Debugger enthält die folgenden neuen Features:

- Neues in 15.5, die **Momentaufnahme Debugger** eine Momentaufnahme Ihrer Anwendungen in Produktion aufgenommen, wenn Code, der Sie interessiert sind, ausgeführt. Legen Sie Andockpunkte und Protokollpunkte in Ihrem Code fest, um den Debugger anzuweisen, eine Momentaufnahme zu erstellen. Der Debugger zeigt Fehler ohne Auswirkungen auf den Datenverkehr Ihrer Produktionsanwendung an. Der Momentaufnahmedebugger kann Sie dabei unterstützen, die Zeit zum Beheben von Fehlern, die in Produktionsumgebungen auftreten, erheblich zu reduzieren.

    Die Momentaufnahmensammlung ist für folgende Web-Apps verfügbar, die in Azure App Service ausgeführt werden:

    * ASP.NET-Apps, die in .NET Framework 4.6.1 oder höher ausgeführt werden.
    * ASP.NET Core-Apps, die in .NET Core 2.0 oder höher unter Windows ausgeführt werden.

    Weitere Informationen finden Sie unter [live ASP.NET-apps, die mit der Snapshot-Debugger Debuggen](../debugger/debug-live-azure-applications.md).

- Neu in 15.5 nur in Visual Studio Enterprise **IntelliTrace Schritt hinten** automatisch Schritt Ereignis wird eine Momentaufnahme der Anwendung auf jedem haltepunktereignissen und den Debugger. Durch die erfassten Momentaufnahmen können Sie zu vorherigen Haltepunkten oder Schritten zurückkehren und sich den Zustand der Anwendung so anzeigen lassen, wie er zuvor war. Mit dem IntelliTrace-Feature „Step-back“ können Sie Zeit sparen, wenn Sie den vorherigen Zustand der Anwendung anzeigen oder diesen wiederherstellen, aber das Debuggen nicht erneut starten möchten.

    Sie können Momentaufnahmen anzeigen und durch diese navigieren, indem Sie die Schaltflächen **Schritt zurück** und **Schritt vor** in der Debugsymbolleiste verwenden. Mit diesen Schaltflächen können Sie durch die Ereignisse navigieren, die in der Registerkarte **Ereignisse** des Fensters **Diagnosetools** angezeigt werden.

    ![Schrittweise rückwärts und Vorwärts-Schaltflächen](../debugger/media/intellitrace-step-back-icons-description.png  "Schritt rückwärts und Vorwärts-Schaltflächen")

    Weitere Informationen finden Sie auf der Seite [View snapshots using IntelliTrace step-back (Anzeigen von Momentaufnahmen mithilfe des IntelliTrace-Features „Step-back“)](../debugger/how-to-use-intellitrace-step-back.md).

- Die **Ausnahmen-Hilfe** Ausnahmen-Assistent ersetzt und wird in ein nicht modales Dialogfeld, in dem der Fehler aufgetreten ist. Die **Ausnahmen-Hilfe** bietet schnelleren Zugriff auf alle inneren Ausnahmen, die zusätzliche Analyse durch den Debugger (falls vorhanden) und die unmittelbaren Zugriff auf die **Ausnahmeeinstellungen** für die Ausnahme. Ausnahmen-Hilfe kann auch in eine Gleitkommazahl Ansicht gezogen werden, wenn es etwas, die Sie benötigen blockiert wird, finden Sie unter.

    Z. B. eine **NullReferenceException** zeigt jetzt die Variable, die null-Verweis (Zusatzinformationen) aufweist.

    ![Ausnahmen-Hilfe des Debuggers](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Weitere Informationen finden Sie im Blogbeitrag [Using the New Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) (Verwenden der neuen Ausnahmen-Hilfe in Visual Studio).

- Sie können jetzt ausführen, zu einer Zeile des Codes im Debugger anhalten, durch Auswahl der **hier ausgeführt** grünen Pfeil (angezeigt, das Symbol "Wenn Sie mit dem Mauszeiger auf eine Codezeile). Hierdurch entfällt die Notwendigkeit temporäre Haltepunkte festgelegt.

    ![Der Debugger ausgeführt wird, klicken Sie auf](../debugger/media/dbg-run-to-click.png "DbgRunToClick") 

- Können Sie Bedingungen festlegen, bei Ausnahmen, die in der **Ausnahmeeinstellungen** (Dialogfeld) (hierzu können Sie mithilfe der **Bedingung bearbeiten** Symbol im Dialogfeld Ausnahmeeinstellungen oder indem Sie mit der rechten Maustaste auf die Diese Ausnahme.) Derzeit unterstützte Bedingungen umfassen die Modul-Namen einschließen oder ausschließen, für die Ausnahme.

    ![Bedingungen für eine Ausnahme](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- Fügen Sie den Prozess im Dialogfeld eine neue Funktion für die Suche enthält, mit denen Sie den Prozess schnell zu identifizieren, dem zum Anfügen müssen.

    ![Suchen Sie im an den Prozess anhängen](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch") 

Weitere Informationen zu diesen neuen Funktionen finden Sie unter der [Versionshinweise für [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#debuggingdiag).
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/index.md)  
 [Debugger – Featuretour](../debugger/debugger-feature-tour.md)