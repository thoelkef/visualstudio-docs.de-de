---
title: "IDiaSymbol::findInlineFramesByAddr | Microsoft Docs"
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
ms.assetid: 36a122e6-f27e-40cd-9784-cdaf279e1905
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::findInlineFramesByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine Enumeration ab, die einem Client ermöglicht, um alle inline Frames auf einer angegebenen Adresse zu durchlaufen.  
  
## Syntax  
  
```cpp#  
HRESULT findInlineFramesByAddr (   
   DWORD             isect,  
   DWORD             offset,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Parameter  
 `isect`  
 \[in\] Gibt die Abschnittskomponente der Adresse an.  
  
 `offset`  
 \[in\] Gibt die Offsetkomponente der Adresse an.  
  
 `ppResult`  
 \[out\] `IDiaEnumSymbols` enthält ein Objekt, das die Liste von Rahmen enthält, die abgerufen werden.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)