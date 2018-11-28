---
title: 'Vorgehensweise: Zurückkehren zur Funktion, die MFC aufgerufen hat, wenn angehalten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af8856a4356a829b37a4a624b86f7b29dd965f9c
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389457"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Gewusst wie: Zurückkehren zur Funktion, die MFC aufgerufen hat, wenn die Ausführung angehalten wurde

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Einstellungen zurücksetzen](../ide/environment-settings.md#reset-settings).

Wenn Sie zum Abbrechen des Programms im Menü Debuggen **den Befehl Unterbrechen** verwendet haben, sich jetzt in MFC befinden und sicher sind, dass das Problem in Ihrem Code liegt, können sie mithilfe des Fensters "Aufrufliste" zu Ihrer Funktion zurück navigieren. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden Sie das Fenster "Aufrufliste"](../debugger/how-to-use-the-call-stack-window.md).

Manchmal wird der Code in der Meldungsverteilschleife unterbrochen. In diesem Fall ist kein Benutzercode in der Aufrufliste vorhanden. Um diesen Fehler zu vermeiden, können Haltepunkte (möglicherweise mit Bedingungen und Trefferanzahl) anstelle des Befehls Unterbrechen** verwendet werden. Weitere Informationen finden Sie unter [Breakpoints and Tracepoints](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583).

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>Navigieren Sie zu der Funktion, die von der MFC aufgerufen wurde

-   Verwenden Sie das Fenster Aufrufliste **.

## <a name="see-also"></a>Siehe auch

- [FAQs zum Debuggen von nativem Code](../debugger/debugging-native-code-faqs.md)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)