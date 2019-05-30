---
title: Schritt von C# code, wenn systemeigene Rahmen in der Aufrufliste nicht
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 15169fb1cdbba554ee2066f3123ded8c60f7408f
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263374"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Vorgehensweise: Ausführen von verwaltetem Code bis zum Rücksprung, wenn native Frames im Aufruflistenfenster fehlen

Wenn der Code native Frames enthält, die im Fenster **Aufrufliste** nicht angezeigt werden, kann das Ausführen von verwaltetem Code bis zum Rücksprung zu unerwarteten Ergebnissen führen. Sie können dieses Problem umgehen, indem Sie anstelle von **Ausführung bis Rücksprung** einen Haltepunkt verwenden.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

## <a name="step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>So führen Sie verwalteten Code bis zum Rücksprung aus, wenn native Frames in der Aufrufliste fehlen

1. Legen Sie im nativen Code nach dem Aufruf an den verwalteten Code einen Positionshaltepunkt fest.

2. Wählen Sie im Menü **Debuggen** die Option **Weiter** aus.

     Sobald der verwaltete Aufruf fertig gestellt wurde, wird die Ausführung am Haltepunkt im systemeigenen Code beendet.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Use the Call Stack Window (Vorgehensweise: Verwenden des Fensters Aufrufliste)](../debugger/how-to-use-the-call-stack-window.md)