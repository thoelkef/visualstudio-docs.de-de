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
ms.openlocfilehash: d557fc0ec056cac22603338f95920e5c721f67dd
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637281"
---
# <a name="continuing-execution-after-an-exception"></a>Fortfahren mit der Ausführung nach einer Ausnahme
Wenn der Debugger die Ausführung aufgrund einer Ausnahme unterbrochen wird, wird Ihnen die **Ausnahmen-Hilfe**, in der Standardeinstellung. Wenn Sie deaktiviert haben die **Ausnahmen-Hilfe** in die **Optionen** im Dialogfeld wird Ihnen die **Ausnahmen-Assistent** (C# oder Visual Basic) oder die  **Ausnahme** (Dialogfeld) (C++).

 Wenn die **Ausnahmehilfsprogramm** angezeigt wird, können Sie versuchen, das Problem zu beheben, die die Ausnahme verursacht hat.

## <a name="managed-and-native-code"></a>Verwalteter und nativer Code
 In verwaltetem und nativem Code können Sie Ausführung nach einem Ausnahmefehler im gleichen Thread fortsetzen. Die **Ausnahmehilfsprogramm** entlädt die Aufrufliste zu dem Punkt, in dem die Ausnahme ausgelöst wurde.

## <a name="mixed-code"></a>Gemischter Code
 Wenn beim Debuggen gemischten Codes (systemeigener und verwalteter Code) ein Ausnahmefehler auftritt, verhindern Einschränkungen des Betriebssystems das Entladen der Aufrufliste. Sollten Sie versuchen, die Aufrufliste über das Kontextmenü neu zu laden, erhalten Sie die Fehlermeldung, dass der Debugger beim Debuggen von gemischtem Code keine Entladung aus einer unbehandelten Ausnahme vornehmen kann.

## <a name="see-also"></a>Siehe auch

- [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md)