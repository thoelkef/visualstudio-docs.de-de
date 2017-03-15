---
title: "Ausnahmebehandlung (Visual Studio-SDK) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK]-Ausnahmebehandlung"
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Ausnahmebehandlung (Visual Studio-SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Folgenden beschreibt den Prozess, der auftritt, wenn Ausnahmen ausgelöst werden.  
  
## Ausnahmebehandlungs\-Prozess  
  
1.  Wenn zuerst eine Ausnahme ausgelöst wurde, aber bevor sie vom Ausnahmehandler im Programm behandelt wird, das gedebuggt wird, sendet das Debugmodul \(Debuggen\) DE [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) auf den Manager der Sitzung \(SDM\) als aufhörendes Ereignis.  `IDebugExceptionEvent2` wird gesendet, wenn nur die Einstellungen für die Ausnahme angegeben wird \(im Dialogfeld Ausnahmen Debug Paket\) angeben, dass der Benutzer für Ausnahmebenachrichtigungen \(erste Chance\) beendet werden soll.  
  
2.  Das SDM ruft [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) an, dass die Eigenschaft der Ausnahme ab.  
  
3.  Das Debuggen von Paket wird [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) an, um festzustellen, welche Optionen, um sich dem Benutzer anzuzeigen.  
  
4.  Das Debuggen von Paket fragt den Benutzer, wie die Ausnahme behandelt, indem ein Dialogfeld Ausnahmen der ersten Chance geöffnet.  
  
5.  Wenn Benutzer beschließt, um fortzufahren, ruft das SDM [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)an.  
  
    -   Wenn die Methode S\_OK zurückgibt, ruft [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)an.  
  
         \- oder \-  
  
         Wenn die Methode S\_FALSE zurückgegeben wird, kann das Programm, das gedebuggt wird, eine zweiten Chance, die Ausnahme zu behandeln.  
  
6.  Wenn das Programm, das gedebuggt wird, keinen Handler für eine Ausnahme der zweiten Chance hat, sendet DE `IDebugExceptionEvent2` um SDM als **EVENT\_SYNCHRONIZATION\_STOP**.  
  
7.  Das Debuggen von Paket fragt den Benutzer, wie die Ausnahme behandelt, indem ein Dialogfeld Ausnahmen der ersten Chance geöffnet.  
  
8.  Das Debuggen von Paket wird [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) an, um festzustellen, welche Optionen, um sich dem Benutzer anzuzeigen.  
  
9. Das Debuggen von Paket fragt den Benutzer, wie die Ausnahme behandelt, indem eine Ausnahme der zweiten Chance Dialogfeld geöffnet.  
  
10. Wenn die Methode S\_OK zurückgibt, ruft `IDebugExceptionEvent2::PassToDebuggee`an.  
  
## Siehe auch  
 [Aufrufen von Debugger\-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)