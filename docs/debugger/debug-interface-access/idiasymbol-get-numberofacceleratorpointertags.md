---
title: "IDiaSymbol::get_numberOfAcceleratorPointerTags | Microsoft Docs"
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
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_numberOfAcceleratorPointerTags
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt die Anzahl der Zugriffstastenzeigertags in der AMP\-Stubfunktion einer C\+\+\-Datei zurück.  
  
## Syntax  
  
```cpp  
HRESULT get_numberOfAcceleratorPointerTags(   
   DWORD* count);  
```  
  
#### Parameter  
 `count`  
 \[out\] markiert Ein Zeiger auf `DWORD`, der die Anzahl der Zugriffstastenzeigers enthält, in der AMP\-Stubfunktion in C\+\+.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## Hinweise  
 Diese Methode wird bei einer `IDiaSymbol`\-Schnittstelle aufgerufen, die zur AMPzugriffstasten\-Stubfunktion in C\+\+ entspricht.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)