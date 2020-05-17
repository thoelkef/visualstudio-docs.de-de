---
title: Fortsetzen der Ausführung nach einer Ausnahme | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7be214a950c8cc93d986f97834a848bd9ab824e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745647"
---
# <a name="continuing-execution-after-an-exception"></a>Fortfahren mit der Ausführung nach einer Ausnahme
Wenn der Debugger die Ausführung aufgrund einer Ausnahme unterbricht, wird standardmäßig die **Ausnahme-Hilfe** angezeigt. Wenn Sie die **Ausnahme-Hilfe** im Dialogfeld **Optionen** deaktiviert haben, wird der **Ausnahmen-Assistant** (C# oder Visual Basic) oder das Dialogfeld **Ausnahme** (C++) angezeigt.

 Wird das **Ausnahme-Hilfe** angezeigt, können Sie versuchen, das Problem zu beheben, das die Ausnahme verursacht hat.

## <a name="managed-and-native-code"></a>Verwalteter und nativer Code
 In verwaltetem und nativem Code kann die Ausführung nach einem Ausnahmefehler im gleichen Thread fortgesetzt werden. Die **Ausnahmen-Hilfe** entlädt die Aufrufliste bis an den Punkt, an dem die Ausnahme ausgelöst wurde.

## <a name="mixed-code"></a>Gemischter Code
 Wenn beim Debuggen gemischten Codes (systemeigener und verwalteter Code) ein Ausnahmefehler auftritt, verhindern Einschränkungen des Betriebssystems das Entladen der Aufrufliste. Sollten Sie versuchen, die Aufrufliste über das Kontextmenü neu zu laden, erhalten Sie die Fehlermeldung, dass der Debugger beim Debuggen von gemischtem Code keine Entladung aus einer unbehandelten Ausnahme vornehmen kann.

## <a name="see-also"></a>Siehe auch

- [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md)