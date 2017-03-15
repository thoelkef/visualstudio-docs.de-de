---
title: "IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt alle Zugriffstastenzeigertagwerte zurück, die zur AMPzugriffstasten\-Stubfunktion einer C\+\+\-Datei entsprechen.  
  
## Syntax  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### Parameter  
 `cnt`  
 \[\] in die Größe des Ausgabearrays `pPointerTags`.  
  
 `pcnt`  
 \[out\] die Anzahl der Zugriffstastenzeigertags in der C\+\+\-AMPzugriffstasten\-Stubfunktion.  
  
 `pPointerTags`  
 \[out\] Arrayzeiger A `DWORD`, der mit den Zugriffstastenzeigertagwerten in der C\+\+\-AMPzugriffstasten\-Stubfunktion gefüllt ist.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## Hinweise  
 Diese Methode wird bei einer `IDiaSymbol`\-Schnittstelle aufgerufen, die zur AMPzugriffstasten\-Stubfunktion in C\+\+ entspricht.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)