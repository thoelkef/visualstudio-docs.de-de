---
title: Wie wird festgestellt, ob Zeiger eine Speicheradresse zerstören? | Microsoft-Dokumentation
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
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c9d3a6c754aa200703c5f2a0ed2e458e08830a3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523675"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Wie wird festgestellt, ob Zeiger eine Speicheradresse zerstören?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Wo finde ich heraus, ob meine beschädigt Zeiger eine Speicheradresse?](https://docs.microsoft.com/visualstudio/debugger/how-can-i-find-out-if-my-pointers-corrupt-a-memory-address-q).  
  
Problembeschreibung  
 Vermutlich wird der Speicher an der Adresse 0x00408000 von einem Zeiger des Programms zerstört. Wie kann festgestellt werden, was dort geschieht?  
  
## <a name="solution"></a>Lösung  
  
#### <a name="check-for-heap-corruption"></a>Überprüfen des Heaps auf Beschädigungen  
  
-   Ein Speicherschaden ist eigentlich die Folge einer Heapbeschädigung. Verwenden Sie in diesem Fall das Global Flags-Dienstprogramm (gflags.exe) oder "pageheap.exe". Finden Sie unter [ http://support.microsoft.com/default.aspx?scid=kb; En-us; 286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).  
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>So finden Sie die geänderte Stelle der Speicheradresse  
  
1.  Legen Sie einen Datenhaltepunkt bei 0x00408000 fest. Finden Sie unter [festlegen ein Haltepunkts für datenänderungen (nur systemeigener C++-)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only).  
  
2.  Wenn der Haltepunkt erreicht wird, verwenden Sie die **Arbeitsspeicher** Fenster zum Anzeigen des Speichers zu Inhalt, beginnend bei 0 x 00408000 fest. Weitere Informationen finden Sie unter [Arbeitsspeicher Windows](../debugger/memory-windows.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von nativem Code häufig gestellte Fragen](../debugger/debugging-native-code-faqs.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)



