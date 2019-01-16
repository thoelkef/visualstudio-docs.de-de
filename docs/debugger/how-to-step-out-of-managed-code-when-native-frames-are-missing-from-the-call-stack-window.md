---
title: Schritt von C# code, wenn systemeigene Rahmen in der Aufrufliste fehlen | Microsoft-Dokumentation
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
manager: douge
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2759df7cc59f4d0167e1ef44dfb9cc65d16ba815
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867435"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Vorgehensweise: Ausführen von verwaltetem Code bis zum Rücksprung, wenn native Frames im Aufruflistenfenster fehlen

Wenn der Code native Frames enthält, die im Fenster **Aufrufliste** nicht angezeigt werden, kann das Ausführen von verwaltetem Code bis zum Rücksprung zu unerwarteten Ergebnissen führen. Sie können dieses Problem umgehen, indem Sie anstelle von **Ausführung bis Rücksprung** einen Haltepunkt verwenden.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

## <a name="step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>So führen Sie verwalteten Code bis zum Rücksprung aus, wenn native Frames in der Aufrufliste fehlen

1.  Legen Sie im nativen Code nach dem Aufruf an den verwalteten Code einen Positionshaltepunkt fest.

2.  Wählen Sie im Menü **Debuggen** die Option **Weiter** aus.

     Sobald der verwaltete Aufruf fertig gestellt wurde, wird die Ausführung am Haltepunkt im nativen Code beendet.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Use the Call Stack Window (Vorgehensweise: Verwenden des Fensters Aufrufliste)](../debugger/how-to-use-the-call-stack-window.md)