---
title: 'Vorgehensweise: Reagieren auf den Just-In-Time-Debugger | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 05/23/17
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5cec8887ddf2023a8abd08f409b93f47efdc7001
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155567"
---
# <a name="how-to-respond-to-the-just-in-time-debugger"></a>Vorgehensweise: Reagieren auf den Just-In-Time-Debugger

Die Aktionen, die Sie abwartet, wenn Sie sehen, dass die Just-in-Time-Debugger Dialogfeld abhängig sind, auf was Sie tun möchten:

#### <a name="if-you-want-to-fix-or-debug-the-error-visual-studio-users"></a>Wenn Sie verwenden möchten, zu beheben oder Debuggen des Fehlers (Visual Studio-Benutzer)

- Sie benötigen [Visual Studio installiert](http://visualstudio.microsoft.com) um die ausführliche Informationen zum Fehler anzuzeigen und zu debuggen. Weitere Informationen finden Sie unter [Debuggen mithilfe des Just-in-Time-Debuggers](../debugger/debug-using-the-just-in-time-debugger.md). Wenn Sie nicht den Fehler beheben, und beheben Sie die app, wenden Sie sich an den Besitzer der app, um den Fehler zu beheben.

#### <a name="if-you-want-to-prevent-the-just-in-time-debugger-dialog-box-from-appearing"></a>Sollten Sie verhindern, dass das Dialogfeld "Just-in-Time-Debugger" angezeigt wird

Sie können dafür sorgen, um zu verhindern, dass die Just-in-Time-Debugger-Dialogfeld angezeigt werden. Wenn die app über den Fehler behandelt, können Sie normalerweise die app ausführen.

1. (Web-apps) Wenn Sie eine Web-app ausführen möchten, können Sie das Debuggen von Skripts deaktivieren.

    Deaktivieren Sie für Internet Explorer oder Microsoft Edge das Skriptdebuggen in das Dialogfeld "Internetoptionen" aus. Sie erreichen die Einstellungen von der **Systemsteuerung** > **Netzwerk und Internet** > **Internetoptionen** (die genauen Schritte hängen Ihre Version von Windows und Ihren Browser).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

    Öffnen Sie dann erneut die Webseite, in dem Sie den Fehler gefunden. Wenn diese Einstellung ändern, das Problem nicht behebt, wenden Sie sich an den Besitzer der Web-app, um das Problem zu beheben.

3. (Visual Studio-Benutzer) Wenn Sie Visual Studio installiert haben (oder bei es zuvor installiert und entfernt es), [deaktivieren Sie Just-in-Time-Debuggen](../debugger/debug-using-the-just-in-time-debugger.md) und führen Sie die app erneut aus.

    > [!IMPORTANT]
    > Wenn Sie, Just-in-Time deaktivieren-Debuggen und die app einen Ausnahmefehler (Fehler), Sie werden entweder ein Standardfehler-Dialogfeld angezeigt, stattdessen oder trifft die app Absturz oder aufhängen führt, wird. Die app wird normalerweise nicht ausgeführt, bis der Fehler, (durch Sie oder der Besitzer der app behoben wurde).

2. (ASP.NET und IIS) Wenn Sie eine ASP.NET Web-app in IIS hosten, deaktivieren Sie die serverseitige debugging.

    Im IIS-Manager mit der rechten Maustaste des Serverknoten und wählen Sie **wechseln Sie zur Ansicht "Features"**. Wählen Sie im Abschnitt ASP.NET **.NET Kompilierung** und stellen Sie sicher, dass Sie auswählen, **"false"** als das Debug-Verhalten (die Schritte unterscheiden sich in älteren Versionen von IIS).

## <a name="see-also"></a>Siehe auch
 [Debugger – Grundlagen](../debugger/debugger-basics.md)
