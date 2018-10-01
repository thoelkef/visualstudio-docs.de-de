---
title: 'Exemplarische Vorgehensweise: Debuggen zur Entwurfszeit | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd63fca37bbb55f99ecb99a18596c128451bd807
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516059"
---
# <a name="walkthrough-debugging-at-design-time"></a>Exemplarische Vorgehensweise: Debuggen zur Entwurfszeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Exemplarische Vorgehensweise: Debuggen zur Entwurfszeit](https://docs.microsoft.com/visualstudio/debugger/walkthrough-debugging-at-design-time).  
  
Sie können Visual Studio **direkt** Fenster aus, um eine Funktion oder Unterroutine ausführen, während die Anwendung nicht ausgeführt wird. Wenn die Funktion oder die Unterroutine einen Haltepunkt enthält, unterbricht Visual Studio die Ausführung an der entsprechenden Stelle. Sie können dann die Debuggerfenster verwenden, um den Programmzustand zu überprüfen. Dieses Feature wird "Debuggen zur Entwurfszeit" genannt.  
  
 Die folgende Prozedur veranschaulicht, wie Sie dieses Feature verwenden können.  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>So erreichen Sie Haltepunkte über das Direktfenster  
  
1.  Fügen Sie den folgenden Code in eine Visual Basic-Konsolenanwendung ein:  
  
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
  
2.  Legen Sie einen Haltepunkt an der Zeile `s="Add BreakPoint Here"` fest.  
  
3.  Geben Sie Folgendes in die **direkt** Fenster: `?MyFunction<enter>`  
  
4.  Stellen Sie sicher, dass der Haltepunkt erreicht wurde und dass die Aufrufliste korrekt ist.  
  
5.  Auf der **Debuggen** Menü klicken Sie auf **Weiter**, und stellen Sie sicher, dass Sie immer noch im Entwurfsmodus sind.  
  
6.  Geben Sie Folgendes in die **direkt** Fenster: `?MyFunction<enter>`  
  
7.  Geben Sie Folgendes in die **direkt** Fenster: `?MySub<enter>`  
  
8.  Stellen Sie sicher, dass Sie den Haltepunkt, und überprüfen Sie den Wert der statischen Variablen `i` in die **"lokal"** Fenster. Sie sollte den Wert 3 haben.  
  
9. Überprüfen Sie, dass die Aufrufliste korrekt ist.  
  
10. Auf der **Debuggen** Menü klicken Sie auf **Weiter**, und stellen Sie sicher, dass Sie immer noch im Entwurfsmodus sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)



