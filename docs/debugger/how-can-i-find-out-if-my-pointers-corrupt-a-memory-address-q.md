---
title: "Wie wird festgestellt, ob Zeiger eine Speicheradresse zerst&#246;ren? | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
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
  - "C++"
helpviewer_keywords: 
  - "Adressen, Zeiger beschädigen Speicheradresse"
  - "Beschädigte Speicheradresse"
  - "Debuggen [C++], Speicherbeschädigung"
  - "Speicheradressenbeschädigung durch Zeiger"
  - "Speicher, Beschädigung"
  - "Zeiger, Beschädigen von Speicheradressen"
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Wie wird festgestellt, ob Zeiger eine Speicheradresse zerst&#246;ren?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Problembeschreibung  
 Vermutlich wird der Speicher an der Adresse 0x00408000 von einem Zeiger des Programms zerstört.  Wie kann festgestellt werden, was dort geschieht?  
  
## Lösung  
  
#### Überprüfen des Heaps auf Beschädigungen  
  
-   Ein Speicherschaden ist eigentlich die Folge einer Heapbeschädigung.  Verwenden Sie in diesem Fall das Global Flags\-Dienstprogramm \(gflags.exe\) oder "pageheap.exe".  Weitere Informationen erhalten Sie unter [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;de\-de;286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).  
  
#### So finden Sie die geänderte Stelle der Speicheradresse  
  
1.  Legen Sie einen Datenhaltepunkt bei 0x00408000 fest.  Weitere Informationen erhalten Sie unter [Festlegen eines Haltepunkts für Datenänderungen \(nur systemeigener C\+\+\-Code\)](../debugger/using-breakpoints.md#BKMK_Set_a_data_change_breakpoint__native_C___only_).  
  
2.  Zeigen Sie den Speicherinhalt bei Erreichen eines Haltepunkts im Fenster **Speicher** ab Adresse 0x00408000 an.  Weitere Informationen finden Sie unter [Fenster "Arbeitsspeicher"](../debugger/memory-windows.md).  
  
## Siehe auch  
 [FAQs zum Debuggen von systemeigenem Code](../debugger/debugging-native-code-faqs.md)   
 [Debuggen von systemeigenem Code](../debugger/debugging-native-code.md)