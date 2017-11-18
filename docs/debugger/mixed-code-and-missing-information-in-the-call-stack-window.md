---
title: Gemischter Code und fehlende Daten im Aufruflistenfenster | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97c7cd3588edbb7b07c5eaed25df07c882805d73
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Gemischter Code und fehlende Daten im Fenster "Aufrufliste"
Da es zwischen den Aufruflisten von verwaltetem Code und nativem Code Unterschiede gibt, kann der Debugger bei vermischten Codetypen nicht immer die vollständige Aufrufliste anzeigen. Wenn systemeigener Code verwalteten Code aufruft, Sie können folgende abweichungen in der **Aufrufliste** Fenster:  
  
-   Der systemeigene Rahmen direkt über den verwalteten Code möglicherweise fehlt die **Aufrufliste** Fenster. Weitere Informationen finden Sie unter [wie: Ausführen bis Rücksprung verwaltetem Code, wenn systemeigene Rahmen im Aufruflistenfenster fehlen](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
-   Für außerhalb des Debuggers gestartete Anwendungen mit gemischtem Modus der **Aufrufliste** Fenster kann nur den verwalteten Code angezeigt, und keiner der systemeigenen Rahmen werden angezeigt.  
  
 Beide Fälle treten relativ selten ein. In den meisten Fällen, in denen verwalteter Code durch systemeigenen Code aufgerufen wird, werden die Aufruflisten richtig angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Verwenden des Fensters „Aufrufliste“](../debugger/how-to-use-the-call-stack-window.md)