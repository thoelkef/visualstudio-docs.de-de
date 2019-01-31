---
title: Auflösen Mehrdeutigkeit (Dialogfeld) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.Disambig
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Resolve Ambiguity dialog box
- debugger, Resolve Ambiguity dialog box
- debugging [C++], resolving ambiguity
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2cad82add5d397991f2c3e7532bbbf2559f9819e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033065"
---
# <a name="resolve-ambiguity-dialog-box"></a>Mehrdeutigkeit auflösen (Dialogfeld)
Das Dialogfeld `Resolve Ambiguity` wird angezeigt, wenn die anzuzeigende Position vom Debugger nicht ausgewählt werden kann. Wenn Sie beispielsweise C++-Vorlagen verwenden, können Sie aus einer einzigen Funktionsvorlage mehrere Funktionen erstellen. Wenn der Debugger an einer Quellcodeposition in der Vorlage anhält und Sie auf `Go To Disassembly` klicken, bietet der Debugger mehrere Möglichkeiten. Jede aus der Vorlage erstellte Funktion hat einen eigenen Disassemblycode, und der Debugger weiß nicht, welcher Code angezeigt werden soll. Im Dialogfeld `Resolve Ambiguity` können Sie die gewünschte Position aus einer Liste aller entsprechenden Positionen auswählen.  
  
 `Choose the specific location`  
 Es werden alle dem Befehl entsprechenden Positionen aufgeführt.  
  
 `Address`  
 Die Speicheradressen für die einzelnen Funktionen werden angezeigt.  
  
 `Function`  
 Der Name der jeweiligen Funktion wird angezeigt.  
  
 `Module`  
 Das Modul (EXE oder DLL), das den Objektcode für die Funktion enthält, wird angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdrücke im Debugger](../debugger/expressions-in-the-debugger.md)