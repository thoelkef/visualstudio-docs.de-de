---
title: 'Vorgehensweise: Festlegen eines Threadnamens in verwaltetem Code | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
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
helpviewer_keywords:
- Thread.Name property
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a921fcdcd19114842e026f1ebc3bcb699e200f89
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256100"
---
# <a name="how-to-set-a-thread-name-in-managed-code"></a>Gewusst wie: Festlegen eines Threadnamens in verwaltetem Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Benennen von Threads ist in allen Editionen von Visual Studio möglich. Benennen von Threads ist nützlich für das Verfolgen von Threads in der **Threads** Fenster. Da die **Threads** nicht in den Visual Studio Express-Editionen verfügbar ist, ist ein kleines Hilfsprogramm Benennen von Threads in Express-Editionen.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Gewusst wie: Festlegen eines Threadnamens in nativem Code](../debugger/how-to-set-a-thread-name-in-native-code.md)



