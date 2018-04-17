---
title: Stop-Anweisungen in Visual Basic | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81cec4d677ef6b88774b172ee63c0142b286a2c6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="stop-statements-in-visual-basic"></a>Stop-Anweisungen in Visual Basic
Die Stop-Anweisung in Visual Basic bietet eine Alternative zum Festlegen eines Haltepunktes. Wenn der Debugger auf eine Stop-Anweisung trifft, wird die Programmausführung unterbrochen (der Unterbrechungsmodus wird aktiviert). C#-Programmierer erzielen den gleichen Effekt mit einem Aufruf von System.Diagnostics.Debugger.Break.  
  
 Sie legen Stop-Anweisungen fest oder entfernen sie, indem Sie den Quellcode bearbeiten. Stop-Anweisungen können im Gegensatz zu Haltepunkten jedoch nicht mithilfe von Debuggerbefehlen definiert oder entfernt werden.  
  
 Anders als eine End-Anweisung setzt die Stop-Anweisung keine Variablen zurück und kehrt auch nicht zum Entwurfsmodus zurück. Um mit der Programmausführung fortzufahren, können Sie im Menü Debuggen die Option Weiter auswählen.  
  
 Beim Ausführen einer Visual Basic-Anwendung außerhalb des Debuggers bewirkt eine Stop-Anweisung, dass der Debugger gestartet wird, sofern das Just‑In‑Time-Debuggen aktiviert ist. Ist das Just-In-Time-Debuggen nicht aktiviert, verhält sich die Stop-Anweisung wie eine End-Anweisung und beendet die Ausführung. Da kein QueryUnload-Ereignis oder Unload-Ereignis auftritt, müssen alle Stop-Anweisungen aus der Releaseversion der Visual Basic-Anwendung entfernt werden. Weitere Informationen finden Sie unter [Just-in-Time-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Damit Sie Stop-Anweisungen nicht explizit entfernen müssen, können Sie die bedingte Kompilierung nutzen:  
  
```  
#If DEBUG Then  
   Stop  
#Else  
   ' Don't stop  
#End If  
```  
  
 Eine Alternative besteht darin, eine Assert-Anweisung anstelle der Stop-Anweisung zu verwenden. Durch eine Debug.Assert-Anweisung wird die Ausführung nur unterbrochen, wenn eine bestimmte Bedingung nicht erfüllt wird. Außerdem wird sie beim Erstellen einer Releaseversion automatisch entfernt. Weitere Informationen finden Sie unter [Assertionen in verwaltetem Code](../debugger/assertions-in-managed-code.md). Wenn Sie eine Assert-Anweisung benötigen, durch die die Ausführung in der Debugversion immer unterbrochen wird, verfahren Sie wie folgt:  
  
```  
Debug.Assert(false)  
```  
  
 Eine weitere Alternative ist die Verwendung der Debug.Fail-Methode:  
  
```  
Debug.Fail("a clever output string goes here")  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)