---
title: "IDiaSymbol::findInlineeLines | Microsoft Docs"
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
ms.assetid: 56ba4bc0-8f96-47c2-8b18-332b4e7c2d91
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::findInlineeLines
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine Enumeration ab, die einem Client ermöglicht, durch die Zeilennummerninformationen aller Funktionen direkt oder indirekt zu durchlaufen, die inline sind, in diesem Symbol.  
  
## Syntax  
  
```cpp#  
HRESULT findInlineeLines (   
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parameter  
 `ppResult`  
 \[out\] `IDiaEnumLineNumbers` enthält ein Objekt, das die Liste von Zeilennummern enthält, die abgerufen werden.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)