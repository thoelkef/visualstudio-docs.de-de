---
title: Neues im Debugger in Visual Studio 2017 | Microsoft-Dokumentation
ms.date: 01/22/2018
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
ms.openlocfilehash: fbc48fdc93feebf2f78b6d11ae2b7cc744c46f98
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269734"
---
# <a name="whats-new-for-the-debugger-in-includevsdev15miscincludesvsdev15mdmd"></a>Neues im Debugger in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Der Debugger diese Funktionen sind neu:

- Neues in Version 15.5: Der **Momentaufnahmedebugger** erstellt eine Momentaufnahme Ihrer Apps, die sich in der Produktion befinden, wenn Code ausgeführt wird, der für Sie von Interesse ist. Legen Sie Andockpunkte und Protokollpunkte in Ihrem Code fest, um den Debugger anzuweisen, eine Momentaufnahme zu erstellen. Der Debugger zeigt Fehler ohne Auswirkungen auf den Datenverkehr Ihrer Produktionsanwendung an. Der Momentaufnahmedebugger kann Sie dabei unterstützen, die Zeit zum Beheben von Fehlern, die in Produktionsumgebungen auftreten, erheblich zu reduzieren.

    Die Momentaufnahmensammlung ist für folgende Web-Apps verfügbar, die in Azure App Service ausgeführt werden:

  * ASP.NET-Apps, die in .NET Framework 4.6.1 oder höher ausgeführt werden.
  * ASP.NET Core-Apps, die in .NET Core 2.0 oder höher unter Windows ausgeführt werden.

    Weitere Informationen finden Sie unter [Debug live ASP.NET apps using the Snapshot Debugger (Debuggen von ASP.NET-Live-Apps mithilfe des Momentaufnahmedebuggers)](../debugger/debug-live-azure-applications.md).

- Neues in Version 15.5 in Visual Studio Enterprise nur **IntelliTrace Rückschritt** automatisch eine Momentaufnahme Ihrer Anwendung in jedem Breakpoint und Debuggerschritt Schrittereignis. Durch die erfassten Momentaufnahmen können Sie zu vorherigen Haltepunkten oder Schritten zurückkehren und sich den Zustand der Anwendung so anzeigen lassen, wie er zuvor war. Mit dem IntelliTrace-Feature „Step-back“ können Sie Zeit sparen, wenn Sie den vorherigen Zustand der Anwendung anzeigen oder diesen wiederherstellen, aber das Debuggen nicht erneut starten möchten.

    Sie können Momentaufnahmen anzeigen und durch diese navigieren, indem Sie die Schaltflächen **Schritt zurück** und **Schritt vor** in der Debugsymbolleiste verwenden. Mit diesen Schaltflächen können Sie durch die Ereignisse navigieren, die in der Registerkarte **Ereignisse** des Fensters **Diagnosetools** angezeigt werden.

    ![Schaltflächen „Schritt zurück“ und „Schritt vorwärts“](../debugger/media/intellitrace-step-back-icons-description.png  "Step Backward and Step Forward buttons")

    Weitere Informationen finden Sie auf der Seite [Inspect previous app states using IntelliTrace (Untersuchen vorheriger App-Zustände mithilfe von IntelliTrace)](../debugger/view-historical-application-state.md).

- Die **Ausnahmehilfsprogramm** der Ausnahmen-Assistent ersetzt und wird in einem nicht-modales Dialogfeld, in dem der Fehler aufgetreten ist. Die **Ausnahmehilfsprogramm** bietet schnelleren Zugriff auf alle inneren Ausnahmen, die zusätzliche Analyse durch den Debugger (falls verfügbar) und sofortigen Zugriff auf die **Ausnahmeeinstellungen** für die Ausnahme. Die Ausnahmen-Hilfe können auch in eine Gleitkommazahl Ansicht gezogen werden, wenn es etwas, die Sie benötigen blockiert, finden Sie unter.

    Z. B. eine **"NullReferenceException"** zeigt jetzt die Variable, die die null-Verweis (zusätzliche Informationen).

    ![Ausnahmen-Hilfe des Debuggers](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Weitere Informationen finden Sie im Blogbeitrag [Using the New Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) (Verwenden der neuen Ausnahmen-Hilfe in Visual Studio).

- Sie können jetzt ausführen, um eine einzige Zeile Code während der Unterbrechung im Debugger durch Auswählen der **Ausführung bis hier ausführen** grüner Pfeil (Sie finden das Symbol beim Zeigen auf eine einzige Zeile Code). Dadurch werden temporäre Haltepunkte festgelegt werden muss.

    ![Debugger die Ausführung bis Klick](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- Können Sie Bedingungen festlegen, von Ausnahmen in der **Ausnahmeeinstellungen** Dialogfeld (Sie erreichen dies, indem die **Bearbeiten einer Bedingung** Symbol in das Dialogfeld "Ausnahmeeinstellungen" oder mit der rechten Maustaste auf die die Ausnahme.) Derzeit unterstützte Bedingungen umfassen die Namen der Module zum ein- oder ausschließen, für die Ausnahme.

    ![Bedingungen für eine Ausnahme](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- Das Dialogfeld eine neue Suchfunktion, mit denen Sie den Prozess schnell zu identifizieren, dem Sie zum Anfügen enthält benötigen an Prozess anfügen.

    ![Suche in an den Prozess anhängen](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

Weitere Informationen zu diesen neuen Funktionen finden Sie unter den [Anmerkungen zu dieser Version [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](/visualstudio/releasenotes/vs2017-relnotes#debuggingdiag).

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.md)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)