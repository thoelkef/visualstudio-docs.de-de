---
title: "IDiaSession::findInlineesByName | Microsoft Docs"
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
ms.assetid: 9860336d-f703-4ecb-bfc4-3f5beb175a76
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findInlineesByName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine Enumeration ab, die einem Client ermöglicht, durch die Zeilennummerninformationen aller Inlinefunktionen zu durchlaufen, die einen angegebenen Namen übereinstimmen.  
  
## Syntax  
  
```cpp#  
HRESULT findInlineesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parameter  
 `name`  
 \[in\] gibt den Namen an, der für Vergleiche zu verwenden.  
  
 `option`  
 \[in\] Gibt die Vergleichsoptionen an, die auf Namenssuchen angewendet werden sollen.  Werte aus der [NameSearchOptions Enumeration](../../debugger/debug-interface-access/namesearchoptions.md)\-Enumeration können einzeln oder in Kombination verwendet werden.  
  
 `ppResult`  
 \[out\] [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) gibt ein Objekt zurück, das eine Liste der Zeilennummern enthält, die abgerufen wurden.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)