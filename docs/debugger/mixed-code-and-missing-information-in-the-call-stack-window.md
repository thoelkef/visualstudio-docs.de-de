---
title: Gemischter Code und fehlende Daten im Aufruflistenfenster | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 025591ffea4d6746f87e5f1240cd226fa291d116
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703668"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Gemischter Code und fehlende Daten im Fenster "Aufrufliste"
Da es zwischen den Aufruflisten von verwaltetem Code und systemeigenen Code Unterschiede gibt, kann der Debugger bei vermischten Codetypen nicht immer die vollständige Aufrufliste anzeigen. Wenn verwalteter Code durch nativen Code aufgerufen wird, sind im Fenster **Aufrufliste** unter Umständen folgende Abweichungen festzustellen:

- Es kann vorkommen, dass der native Rahmen direkt über dem verwalteten Code im Fenster **Aufrufliste** fehlt. Weitere Informationen finden Sie unter [Vorgehensweise: Prozedurschritt aus verwaltetem Code, wenn systemeigene Rahmen im Aufruflistenfenster fehlen](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).

- Für außerhalb des Debuggers gestartete Anwendungen mit gemischtem Code wird im Fenster **Aufrufliste** unter Umständen keiner der nativen Rahmen, sondern nur der verwaltete Code angezeigt.

  Beide Fälle treten relativ selten ein. In den meisten Fällen, in denen verwalteter Code durch systemeigenen Code aufgerufen wird, werden die Aufruflisten richtig angezeigt.

## <a name="see-also"></a>Siehe auch
- [Gewusst wie: Verwenden des Fensters „Aufrufliste“](../debugger/how-to-use-the-call-stack-window.md)