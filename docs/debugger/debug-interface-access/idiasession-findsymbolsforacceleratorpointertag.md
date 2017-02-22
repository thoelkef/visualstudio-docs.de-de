---
title: "IDiaSession::findSymbolsForAcceleratorPointerTag | Microsoft Docs"
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
ms.assetid: 95fd5e7a-c637-437e-b369-c864eef733c2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findSymbolsForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt eine Enumeration von Symbolen für die Variablen zurückgegeben, dass der angegebene Tagwert in der übergeordneten Zugriffstastenstubfunktion entspricht.  
  
## Syntax  
  
```cpp#  
HRESULT findSymbolsForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### Parameter  
 `parent`  
 \[\] in ein IDiaSymbol, das der zu durchsuchenden Zugriffstastenstubentspricht Funktion.  
  
 `tagValue`  
 \[\] in der Zeigertagwert.  
  
 `ppResult`  
 \[out\] Ein Zeiger auf einen `IDiaEnumSymbols`\-Schnittstellenzeiger, der mit dem Ergebnis initialisiert wird.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)