---
title: Neuerungen beim Debugger in Visual Studio 2017 | Microsoft-Dokumentation
titleSuffix: ''
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
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 130387fedce065948ebe09ea605e32cf89ad820b
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71210587"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2017"></a>Neues im Debugger in Visual Studio 2017

Der Debugger umfasst die folgenden neuen Features:

- Neu in Version 15,5: der **Momentaufnahmedebugger** erstellt eine Momentaufnahme ihrer in-Production-apps, wenn der Code, der für Sie von Interesse ist, ausgeführt wird. Legen Sie Andockpunkte und Protokollpunkte in Ihrem Code fest, um den Debugger anzuweisen, eine Momentaufnahme zu erstellen. Der Debugger zeigt Fehler ohne Auswirkungen auf den Datenverkehr Ihrer Produktionsanwendung an. Der Momentaufnahmedebugger kann Sie dabei unterstützen, die Zeit zum Beheben von Fehlern, die in Produktionsumgebungen auftreten, erheblich zu reduzieren.

    Die Momentaufnahmensammlung ist für folgende Web-Apps verfügbar, die in Azure App Service ausgeführt werden:

  * ASP.NET-Apps, die in .NET Framework 4.6.1 oder höher ausgeführt werden.
  * ASP.NET Core-Apps, die in .NET Core 2.0 oder höher unter Windows ausgeführt werden.

    Weitere Informationen finden Sie unter [Debug live ASP.NET apps using the Snapshot Debugger (Debuggen von ASP.NET-Live-Apps mithilfe des Momentaufnahmedebuggers)](../debugger/debug-live-azure-applications.md).

- Neu in Version 15,5 nur in Visual Studio Enterprise: das **IntelliTrace-Step-Back** erstellt automatisch eine Momentaufnahme Ihrer Anwendung bei jedem Breakpoint-und Debugger-Schritt-Ereignis. Durch die erfassten Momentaufnahmen können Sie zu vorherigen Haltepunkten oder Schritten zurückkehren und sich den Zustand der Anwendung so anzeigen lassen, wie er zuvor war. Mit dem IntelliTrace-Feature „Step-back“ können Sie Zeit sparen, wenn Sie den vorherigen Zustand der Anwendung anzeigen oder diesen wiederherstellen, aber das Debuggen nicht erneut starten möchten.

    Sie können Momentaufnahmen anzeigen und durch diese navigieren, indem Sie die Schaltflächen **Schritt zurück** und **Schritt vor** in der Debugsymbolleiste verwenden. Mit diesen Schaltflächen können Sie durch die Ereignisse navigieren, die in der Registerkarte **Ereignisse** des Fensters **Diagnosetools** angezeigt werden.

    ![Schaltflächen „Schritt zurück“ und „Schritt vorwärts“](../debugger/media/intellitrace-step-back-icons-description.png  "Step Backward and Step Forward buttons")

    Weitere Informationen finden Sie auf der Seite [Inspect previous app states using IntelliTrace (Untersuchen vorheriger App-Zustände mithilfe von IntelliTrace)](../debugger/view-historical-application-state.md).

- Das **Exception** -Hilfsprogramm ersetzt den Ausnahmen-Assistenten und wird in einem nicht modalen Dialogfeld angezeigt, in dem der Fehler aufgetreten ist. Das **Exception** -Hilfsprogramm bietet einen schnelleren Zugriff auf alle inneren Ausnahmen, eine zusätzliche Analyse durch den Debugger (falls verfügbar) und unmittelbaren Zugriff auf die **Ausnahme Einstellungen** für die Ausnahme. Die Ausnahmen-Hilfsobjekte können auch in eine Gleit Komma Ansicht gezogen werden, wenn Sie etwas blockiert, das Sie sehen müssen.

    Beispielsweise zeigt eine **NullReferenceException** nun die Variable mit dem NULL-Verweis an (zusätzliche Informationen).

    ![Ausnahme Unterstützung des Debuggers] (../debugger/media/dbg-exception-helper.png "Dbgexceptionhelper")

    Weitere Informationen finden Sie im Blogbeitrag [Using the New Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) (Verwenden der neuen Ausnahmen-Hilfe in Visual Studio).

- Sie können nun bis zu einer Codezeile ausführen, während Sie im Debugger angehalten wird, indem Sie das Symbol **Ausführung bis zu** diesem grünen Pfeil ausführen auswählen (das Symbol wird angezeigt, während Sie auf eine Codezeile zeigen). Dadurch entfällt die Notwendigkeit, temporäre Haltepunkte festzulegen.

    ![Debugger-ausführen bis Klick] (../debugger/media/dbg-run-to-click.png "Dbgrunper Click")

- Sie können Bedingungen für Ausnahmen im Dialogfeld **Ausnahme Einstellungen** festlegen (Sie können hierzu das Symbol **Bedingung bearbeiten** im Dialogfeld Ausnahme Einstellungen oder das Kontextmenü der Ausnahme verwenden.) Zu den derzeit unterstützten Bedingungen gehören die Modulnamen, die für die Ausnahme eingeschlossen oder ausgeschlossen werden sollen.

    ![Bedingungen für eine Ausnahme] (../debugger/media/dbg-conditional-exception.png "Dbgconditionalexception")

- Das Dialogfeld an den Prozess anhängen enthält eine neue Suchfunktion, mit der Sie den Prozess, den Sie anfügen müssen, schneller identifizieren können.

    ![In Anfügen an den Prozess suchen] (../debugger/media/dbg-attach-to-process-search.png "Dbgattachtoprocess Search")

Weitere Informationen zu diesen neuen Features finden Sie in den [Anmerkungen zu dieser [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]Version von ](/visualstudio/releasenotes/vs2017-relnotes).

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.yml)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)