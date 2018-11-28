---
title: 'Gewusst wie: Prozedurschritt aus verwaltetem Code, wenn systemeigene Rahmen im Aufruflistenfenster fehlen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: e5c671f93e20da108a9fd1069a0950f52ef00da9
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388568"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Gewusst wie: Ausführen von verwaltetem Code bis zum Rücksprung, wenn systemeigene Rahmen im Aufruflistenfenster fehlen

Wenn der Code systemeigene Rahmen enthält, die im Fenster Anrufliste** nicht angezeigt werden, kann das Ausführen von verwaltetem Code bis zum Rücksprung zu unerwarteten Ergebnissen führen. Sie können dieses Problem umgehen, indem Sie anstelle von Ausführung bis Rücksprung** einen Haltepunkt verwenden.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Einstellungen zurücksetzen](../ide/environment-settings.md#reset-settings).

## <a name="step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>So führen Sie verwalteten Code bis zum Rücksprung aus, wenn systemeigene Rahmen in der Aufrufliste fehlen

1.  Legen Sie im nativen Code nach dem Aufruf an den verwalteten Code einen Positionshaltepunkt fest.

2.  Wählen Sie im Menü Debuggen **die Option Weiter**.

     Sobald der verwaltete Aufruf fertig gestellt wurde, wird die Ausführung am Haltepunkt im nativen Code beendet.

## <a name="see-also"></a>Siehe auch

- [Gewusst wie: Verwenden des Fensters „Aufrufliste“](../debugger/how-to-use-the-call-stack-window.md)