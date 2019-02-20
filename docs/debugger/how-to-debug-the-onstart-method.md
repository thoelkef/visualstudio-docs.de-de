---
title: 'Vorgehensweise: Debuggen der OnStart-Methode | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2cfd6153389bbfe9cbbd36f33f6a2e4384509297
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227060"
---
# <a name="how-to-debug-the-onstart-method"></a>Gewusst wie: Debuggen der OnStart-Methode
Sie können einen Windows-Dienst debuggen, indem Sie den Dienst starten und den Debugger an den Dienstprozess anfügen. Weitere Informationen finden Sie unter [How to: Debug Windows Service Applications](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Zum Debuggen der <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> -Methode eines Windows-Diensts müssen Sie den Debugger allerdings aus der Methode starten.

1. Fügen Sie am Anfang der <xref:System.Diagnostics.Debugger.Launch%2A> -Methode einen Aufruf von `OnStart()`hinzu.

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Starten Sie den Dienst (dazu können Sie `net start`oder das Fenster **Dienste** verwenden).

    Ein Dialogfeld ähnlich dem folgenden sollte angezeigt werden:

    ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")

3. Wählen Sie **Ja, \<Dienstname> debuggen** aus.

4. Wählen Sie im Fenster des Just-In-Time-Debuggers die Version von Visual Studio aus, die Sie zum Debuggen verwenden möchten.

    ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")

5. Eine neue Instanz von Visual Studio wird gestartet, und die Ausführung wird beim Erreichen der `Debugger.Launch()` -Methode beendet.

## <a name="see-also"></a>Siehe auch
[Debuggersicherheit](../debugger/debugger-security.md)  
[Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
