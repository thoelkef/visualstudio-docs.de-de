---
title: Zurückkehren zur Funktion, die MFC aufgerufen hat, wenn angehalten | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8430c1814e83dbd8410b0f172a15d879bb221cf3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54956674"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Vorgehensweise: Zurückkehren zur Funktion, die MFC aufgerufen hat, wenn angehalten

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

Wenn Sie zum Anhalten des Programms im Menü **Debuggen** den Befehl **Unterbrechen** verwendet haben, sich jetzt in MFC befinden und sicher sind, dass das Problem in Ihrem Code liegt, können Sie mithilfe des Fensters „Aufrufliste“ zu Ihrer Funktion zurücknavigieren. Weitere Informationen finden Sie unter [Vorgehensweise: Use the Call Stack Window (Vorgehensweise: Verwenden des Fensters Aufrufliste)](../debugger/how-to-use-the-call-stack-window.md).

Manchmal wird der Code in der Meldungsverteilschleife unterbrochen. In diesem Fall ist kein Benutzercode in der Aufrufliste vorhanden. Um diesen Fehler zu vermeiden, können Haltepunkte (möglicherweise mit Bedingungen und Trefferanzahl) anstelle des Befehls **Unterbrechen** verwendet werden. Weitere Informationen finden Sie unter [Breakpoints and Tracepoints](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583).

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>Navigieren Sie zu der Funktion, die von der MFC aufgerufen wurde

-   Verwenden Sie das Fenster **Aufrufliste**.

## <a name="see-also"></a>Siehe auch

- [FAQs zum Debuggen von nativem Code](../debugger/debugging-native-code-faqs.md)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)