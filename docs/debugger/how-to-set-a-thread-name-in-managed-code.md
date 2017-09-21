---
title: "Gewusst wie: Festlegen eines Threadnamens in verwaltetem Code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen [Visual Studio], Threads"
  - "Threadnamen"
  - "Thread.Name-Eigenschaft"
  - "Threading [Visual Studio], Namen"
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# Gewusst wie: Festlegen eines Threadnamens in verwaltetem Code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Benennen von Threads ist in allen Editionen von Visual Studio möglich.  Das Benennen von Threads ist hilfreich beim Verfolgen von Threads im Fenster **Threads**.  Da das Fenster **Threads** in Visual Studio Express\-Editionen nicht verfügbar ist, ist in Express\-Editionen ein kleines Hilfsprogramm für das Benennen von Threads verfügbar.  
  
 Um einen Threadnamen in verwaltetem Code festzulegen, verwenden Sie die <xref:System.Threading.Thread.Name%2A>\-Eigenschaft.  
  
## Beispiel  
  
```  
Public Class Needle  
    ' This method will be called when the thread is started.  
    Sub Baz()  
        Console.WriteLine("Needle Baz is running on another thread")  
    End Sub  
End Class  
  
Sub Main()  
    Console.WriteLine("Thread Simple Sample")  
    Dim oNeedle As New Needle()  
   ' Create a Thread object.   
    Dim oThread As New System.Threading.Thread(AddressOf oNeedle.Baz)  
    ' Set the Thread name to "MainThread".  
    oThread.Name = "MainThread"  
    ' Starting the thread invokes the ThreadStart delegate  
    oThread.Start()  
End Sub  
```  
  
## Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Gewusst wie: Festlegen eines Threadnamens in systemeigenem Code](../debugger/how-to-set-a-thread-name-in-native-code.md)