---
title: "CV_call_e | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "CV_call_e-Enumeration"
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CV_call_e
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt die Aufrufkonvention für eine Funktion an.  
  
> [!NOTE]
>  Nur die am häufigsten verwendeten Enumerationswerte werden hier dokumentiert.  Die Vollerhebung ist in der cvconst.h\-Headerdatei verfügbar.  
  
## Syntax  
  
```cpp#  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## Elements  
 CV\_CALL\_NEAR\_C  
 Gibt eine FUNCTION\-rufend Konvention Using a in der Nähe von rechts nach links abgelegt werden soll.  Die aufrufende Funktion löscht den Stapel.  
  
 CV\_CALL\_NEAR\_FAST  
 Gibt eine FUNCTION\-rufend Konvention Using a abgelegt werden soll der Nähe von links nach rechts und Registrierungen an.  Die aufgerufene Funktion verwendet die Summe der Bytes Parameter, um den Stapel zu löschen.  
  
 CV\_CALL\_NEAR\_STD  
 Gibt eine FUNCTION\-rufend Konvention mit einem Aufruf einer standardmäßigen schließende abgelegt werden soll \(von rechts nach links\).  
  
 CV\_CALL\_NEAR\_SYS  
 Gibt eine FUNCTION\-rufend Konvention mithilfe eines Systemaufrufs schließende an.  
  
 CV\_CALL\_THISCALL  
 Gibt eine FUNCTION\-rufend Konvention mit `this` Aufrufs an \(`this` Zeiger in Registern übergeben\).  
  
 CV\_CALL\_CLRCALL  
 Gibt eine FUNCTION\-rufend Konvention an, die von der Common Language Runtime \(CLR\) verwendet wird \(auch als verwalteter Code aufrufkonvention\).  
  
## Hinweise  
 Die Werte in dieser Enumeration werden von einem Aufruf der [IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)\-Methode zurückgegeben.  
  
## Anforderungen  
 Header: cvconst.h  
  
## Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)