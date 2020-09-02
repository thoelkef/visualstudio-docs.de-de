---
title: 'Vorgehensweise: Festlegen eines Threadnamens in verwaltetem Code | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Thread.Name property
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b800fbd2f39d75f110a059c70b87a203eb72e7d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157668"
---
# <a name="how-to-set-a-thread-name-in-managed-code"></a>Vorgehensweise: Festlegen eines Threadnamens in verwaltetem Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Benennen von Threads ist in allen Editionen von Visual Studio möglich. Das Benennen von Threads ist hilfreich beim Verfolgen von Threads im Fenster **Threads**. Da das **Thread Fenster in** den Visual Studio Express-Editionen nicht verfügbar ist, hat die Thread Benennung in Express-Editionen wenig Dienstprogramm.  
  
 Um einen Threadnamen in verwaltetem Code festzulegen, verwenden Sie die <xref:System.Threading.Thread.Name%2A>-Eigenschaft.  
  
## <a name="example"></a>Beispiel  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [How to: Festlegen eines Threadnamens in nativem Code](../debugger/how-to-set-a-thread-name-in-native-code.md)
