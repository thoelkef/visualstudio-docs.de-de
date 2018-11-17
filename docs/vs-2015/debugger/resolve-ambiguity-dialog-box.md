---
title: Auflösen Mehrdeutigkeit (Dialogfeld) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.Disambig
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Resolve Ambiguity dialog box
- debugger, Resolve Ambiguity dialog box
- debugging [C++], resolving ambiguity
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13458279d1970bd1b398a0de6e74b34b0b3a99a0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807581"
---
# <a name="resolve-ambiguity-dialog-box"></a>Mehrdeutigkeit auflösen (Dialogfeld)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



