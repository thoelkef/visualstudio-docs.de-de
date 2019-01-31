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
ms.openlocfilehash: dc43ba24e821c00adb4efb64e4785e02dae31f28
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992554"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Gemischter Code und fehlende Daten im Fenster "Aufrufliste"
Da es zwischen den Aufruflisten von verwaltetem Code und nativem Code Unterschiede gibt, kann der Debugger bei vermischten Codetypen nicht immer die vollständige Aufrufliste anzeigen. Wenn verwalteter Code durch nativen Code aufgerufen wird, sind im Fenster **Aufrufliste** unter Umständen folgende Abweichungen festzustellen:  
  
- Es kann vorkommen, dass der native Rahmen direkt über dem verwalteten Code im Fenster **Aufrufliste** fehlt. Weitere Informationen finden Sie unter [Vorgehensweise: Ausführen von verwaltetem Code bis zum Rücksprung, wenn native Frames im Aufruflistenfenster fehlen](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
- Für außerhalb des Debuggers gestartete Anwendungen mit gemischtem Code wird im Fenster **Aufrufliste** unter Umständen keiner der nativen Rahmen, sondern nur der verwaltete Code angezeigt.  
  
  Beide Fälle treten relativ selten ein. In den meisten Fällen, in denen verwalteter Code durch systemeigenen Code aufgerufen wird, werden die Aufruflisten richtig angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Use the Call Stack Window (Vorgehensweise: Verwenden des Fensters Aufrufliste)](../debugger/how-to-use-the-call-stack-window.md)