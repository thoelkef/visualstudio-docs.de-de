---
title: Neues im Debugger in Visual Studio 2017 | Microsoft Docs
ms.custom: 
ms.date: 03/07/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "81"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a08c56ae60822e6d4183e5789c68cbe383b4dd5
ms.sourcegitcommit: 2c7f48ad6073a81fa927568793633f26cc1f0b15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2017
---
# <a name="whats-new-for-the-debugger-in-includevsdev15miscincludesvsdev15mdmd"></a>Neues im Debugger in[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Der Debugger enthält die folgenden neuen Features:

- Neues in 15.5, die **Momentaufnahme Debugger** eine Momentaufnahme Ihrer Anwendungen in Produktion aufgenommen, wenn Code, der Sie interessiert sind, ausgeführt. Um anzuweisen, den Debugger an eine Momentaufnahme zu erstellen, legen Sie Snappoints und Logpoints im Code. Der Debugger können Sie sehen, genau, Einzelheiten ohne Auswirkungen auf Ihre produktionsanwendung Datenverkehr. Der Momentaufnahme-Debugger können Sie die Zeit, um Probleme zu beheben, die in produktionsumgebungen auftreten benötigt, den Nachrichtendurchsatz stark senken.

    Momentaufnahmesammlung steht für die folgenden Web-apps in Azure App Service ausgeführt wird:

    * ASP.NET-Anwendungen unter .NET Framework 4.6.1 oder höher.
    * ASP.NET Core-Anwendungen, die auf .NET Core 2.0 oder höher auf Windows ausgeführt wird.

    Weitere Informationen finden Sie unter [live ASP.NET-apps, die mit der Snapshot-Debugger Debuggen](../debugger/debug-live-azure-applications.md).

- Neu in 15.5 nur in Visual Studio Enterprise **IntelliTrace Schritt hinten** automatisch Schritt Ereignis wird eine Momentaufnahme der Anwendung auf jedem haltepunktereignissen und den Debugger. Die erfassten Momentaufnahmen können Sie zurückkehren zum vorherigen Haltepunkte oder Schritte und den Status der Anwendung anzeigen, wie dies in der Vergangenheit war. IntelliTrace Schritt Back kann sparen Sie Zeit, wenn Sie möchten, finden in den vorherigen Anwendungszustand aber nicht angezeigt werden sollen, Debuggen neu starten, oder erstellen Sie die gewünschte app-Status erneut.

    Sie können navigieren und Anzeigen von Momentaufnahmen mithilfe der **Schritt rückwärts** und **Schritt vorwärts** Schaltflächen in der Debug-Symbolleiste. Diese Schaltflächen navigieren, die Ereignisse, die in der **Ereignisse** Registerkarte der **Diagnosetools** Fenster.

    ![Schrittweise rückwärts und Vorwärts-Schaltflächen](../debugger/media/intellitrace-step-back-icons-description.png  "Schritt rückwärts und Vorwärts-Schaltflächen")

    Weitere Informationen finden Sie unter der [Anzeigen von Momentaufnahmen mithilfe von IntelliTrace Schritt hinten](../debugger/how-to-use-intellitrace-step-back.md) Seite.

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