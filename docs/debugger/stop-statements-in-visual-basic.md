---
title: Anweisungen in Visual Basic Abbrechen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f9ab4ef453a921371ab7ef4f272cd0e38f4108a
ms.sourcegitcommit: 4d2620bee4688fb881e09a07ea4a264b99f0743e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322533"
---
# <a name="stop-statements-in-visual-basic"></a>Stop-Anweisungen in Visual Basic

Die Stop-Anweisung in Visual Basic bietet eine Alternative zum Festlegen eines Haltepunktes. Wenn der Debugger auf eine Stop-Anweisung trifft, wird die Programmausführung unterbrochen (der Unterbrechungsmodus wird aktiviert). C#Programmierer können die gleiche Wirkung erzielen, <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>indem Sie einen-Befehl verwenden.

Sie legen Stop-Anweisungen fest oder entfernen sie, indem Sie den Quellcode bearbeiten. Stop-Anweisungen können im Gegensatz zu Haltepunkten jedoch nicht mithilfe von Debuggerbefehlen definiert oder entfernt werden.

Anders als eine End-Anweisung setzt die Stop-Anweisung keine Variablen zurück und kehrt auch nicht zum Entwurfsmodus zurück. Um mit der Programmausführung fortzufahren, können Sie im Menü Debuggen die Option Weiter auswählen.

Wenn Sie eine Visual Basic Anwendung außerhalb des Debuggers ausführen, wird der Debugger durch eine Anweisung zum Beenden gestartet, wenn Just-in-Time-Debuggen aktiviert ist. Wenn Just-in-Time-Debuggen nicht aktiviert ist, verhält sich die End-Anweisung wie eine End-Anweisung und beendet die Ausführung. Da kein QueryUnload-Ereignis oder Unload-Ereignis auftritt, müssen alle Stop-Anweisungen aus der Releaseversion der Visual Basic-Anwendung entfernt werden. Weitere Informationen hierzu finden Sie unter [Just-In-Time-Debuggen](just-in-time-debugging-in-visual-studio.md).

 Damit Sie Stop-Anweisungen nicht explizit entfernen müssen, können Sie die bedingte Kompilierung nutzen:

```vb
#If DEBUG Then
   Stop
#Else
   ' Don't stop
#End If
```

Eine weitere Alternative ist die Verwendung <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> einer-Anweisung anstelle der Anweisung "Statement". Eine <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> -Anweisung unterbricht die Ausführung nur, wenn eine angegebene Bedingung nicht erfüllt wird. <xref:System.Diagnostics.Debug.Assert%2A>-Anweisungen werden automatisch entfernt, wenn Sie eine Releaseversion erstellen. Weitere Informationen finden Sie unter [Assertionen in verwaltetem Code](assertions-in-managed-code.md). Wenn Sie eine <xref:System.Diagnostics.Debug.Assert%2A> -Anweisung verwenden möchten, die die Ausführung in der Debugversion immer unterbricht, können Sie Folgendes tun:

```csharp
Debug.Assert(false);
```

```vb
Debug.Assert(False)
```

Eine weitere Alternative ist die Verwendung der <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> -Methode:

```csharp
Debug.Fail("a clever output string goes here");
```

```vb
Debug.Fail("a clever output string goes here")
```

## <a name="see-also"></a>Siehe auch

- [Debuggersicherheit](debugger-security.md)
- [C#-, F#- und Visual Basic-Projekttypen](debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Debuggen von verwaltetem Code](debugging-managed-code.md)
