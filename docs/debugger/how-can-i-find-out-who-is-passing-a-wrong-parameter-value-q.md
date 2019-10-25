---
title: Ermitteln, wer einen falschen Parameterwert übergibt | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.parameters
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42884cd6498f00cfe2df2d0396ff9ea6b03c2f98
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734238"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Wie wird festgestellt, woher der falsche Parameterwert stammt?
## <a name="problem-description"></a>Problembeschreibung
 An eine Funktion wird der falsche Parameterwert übergeben. Diese Funktion wird von mehreren Stellen aus aufgerufen. Wie kann festgestellt werden, woher der falsche Wert stammt?

## <a name="solution"></a>Lösung

#### <a name="to-resolve-this-problem"></a>So beheben Sie dieses Problem

1. Legen Sie am Anfang der Funktion einen Positionshaltepunkt fest.

2. Klicken Sie mit der rechten Maustaste auf den Haltepunkt, und wählen Sie **Bedingung** aus.

3. Aktivieren Sie im Dialogfeld **Bedingung für Haltepunkt** das Kontrollkästchen **Bedingung**. Siehe [Erweiterte Breakpoints](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

4. Geben Sie einen Ausdruck, z. B. `Var==3`, in das Textfeld ein, wobei `Var` der Name des Parameters ist, der den falschen Wert enthält, und `3` der übergebene falsche Wert.

5. Aktivieren Sie das Optionsfeld **is True** (ist TRUE), und klicken Sie auf die Schaltfläche **OK**.

6. Führen Sie nun das Programm erneut aus. Der Haltepunkt bewirkt, dass das Programm am Funktionsanfang anhält, sobald `Var` den Wert `3` hat.

7. Im Fenster Aufrufliste sehen Sie die aufrufende Funktion und können zu ihrem Quellcode navigieren. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden des Fensters "aufrufsstapel](../debugger/how-to-use-the-call-stack-window.md)".

## <a name="see-also"></a>Siehe auch
- [FAQs zum Debuggen von nativem Code](../debugger/debugging-native-code-faqs.md)
- [Breakpoints](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)