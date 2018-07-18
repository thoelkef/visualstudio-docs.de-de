---
title: Wie wird festgestellt, ob Zeiger eine Speicheradresse zerstören? | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8965ec268e5d236b9a33e5c3e8acfa35e51dcdb3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31479311"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Wie wird festgestellt, ob Zeiger eine Speicheradresse zerstören?
## <a name="problem-description"></a>Problembeschreibung  
 Vermutlich wird der Speicher an der Adresse 0x00408000 von einem Zeiger des Programms zerstört. Wie kann festgestellt werden, was dort geschieht?  
  
## <a name="solution"></a>Lösung  
  
#### <a name="check-for-heap-corruption"></a>Überprüfen des Heaps auf Beschädigungen  
  
-   Ein Speicherschaden ist eigentlich die Folge einer Heapbeschädigung. Verwenden Sie in diesem Fall das Global Flags-Dienstprogramm (gflags.exe) oder "pageheap.exe". Finden Sie unter [ http://support.microsoft.com/default.aspx?scid=kb; En-us; 286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).  
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>So finden Sie die geänderte Stelle der Speicheradresse  
  
1.  Legen Sie einen Datenhaltepunkt bei 0x00408000 fest. Finden Sie unter [festlegen ein Haltepunkts für datenänderungen (nur systemeigener C++-)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only).  
  
2.  Wenn der Haltepunkt erreicht wird, verwenden Sie die **Arbeitsspeicher** Fenster zum Anzeigen des Speichers Inhalt beginnend mit 0 x 00408000 fest. Weitere Informationen finden Sie unter [Fenster "Arbeitsspeicher"](../debugger/memory-windows.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von systemeigenem Code häufig gestellte Fragen](../debugger/debugging-native-code-faqs.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)