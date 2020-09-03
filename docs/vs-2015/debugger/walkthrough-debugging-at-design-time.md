---
title: 'Exemplarische Vorgehensweise: Debuggen zur Entwurfszeit | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54466cc3561c194199bbad2b35cd00433da2b0f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149427"
---
# <a name="walkthrough-debugging-at-design-time"></a>Exemplarische Vorgehensweise: Debuggen zur Entwurfszeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können das **direkt** Fenster in Visual Studio verwenden, um eine Funktion oder Unterroutine auszuführen, während die Anwendung nicht ausgeführt wird. Wenn die Funktion oder die Unterroutine einen Haltepunkt enthält, unterbricht Visual Studio die Ausführung an der entsprechenden Stelle. Sie können dann die Debuggerfenster verwenden, um den Programmzustand zu überprüfen. Diese Funktion wird „Debuggen zur Entwurfszeit“ genannt.  
  
 Die folgende Prozedur veranschaulicht, wie Sie dieses Feature verwenden können.  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>So erreichen Sie Haltepunkte über das Direktfenster  
  
1. Fügen Sie den folgenden Code in eine Visual Basic-Konsolenanwendung ein:  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2. Legen Sie einen Haltepunkt an der Zeile `s="Add BreakPoint Here"` fest.  
  
3. Geben Sie im **direkt** Fenster Folgendes ein: `?MyFunction<enter>`  
  
4. Stellen Sie sicher, dass der Haltepunkt erreicht wurde und dass die Aufrufliste korrekt ist.  
  
5. Klicken Sie im Menü **Debuggen** auf **weiter**, und überprüfen Sie, ob Sie sich noch im Entwurfs Modus befinden.  
  
6. Geben Sie im **direkt** Fenster Folgendes ein: `?MyFunction<enter>`  
  
7. Geben Sie im **direkt** Fenster Folgendes ein: `?MySub<enter>`  
  
8. Stellen Sie sicher, dass Sie den Breakpoint erreichen, und überprüfen Sie den Wert der statischen Variablen im Fenster "lokal" `i` . **Locals** Sie sollte den Wert 3 haben.  
  
9. Überprüfen Sie, dass die Aufrufliste korrekt ist.  
  
10. Klicken Sie im Menü **Debuggen** auf **weiter**, und überprüfen Sie, ob Sie sich noch im Entwurfs Modus befinden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugger-Sicherheit](../debugger/debugger-security.md)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)
