---
title: "IDiaSession::findInlineeLinesByRVA | Microsoft Docs"
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
ms.assetid: 7a74d5ee-0dbf-47c0-92b4-47ec03b13ce9
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findInlineeLinesByRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine Enumeration ab, die einem Client ermöglicht, durch die Zeilennummerninformationen aller Funktionen direkt oder indirekt zu durchlaufen, die inline sind, durch das angegebene Symbol und Elemente innerhalb der angegebenen relativen virtuellen Adresse RVA \(\) enthalten ist.  
  
## Syntax  
  
```cpp#  
HRESULT findInlineeLinesByRVA (   
   IDiaSymbol*           parent,  
   DWORD                 rva,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parameter  
 `parent`  
 \[in \]Ein `IDiaSymbol`\-Objekt, das das übergeordnete Objekt darstellt.  
  
 `rva`  
 \[\] in gibt die Adresse als RVA an.  
  
 `length`  
 \[in\] gibt den Adressbereich, in Anzahl von Bytes an, die mit dieser Abfrage abzudecken.  
  
 `ppResult`  
 \[out\] `IDiaEnumLineNumbers` enthält ein Objekt, das die Liste von Zeilennummern enthält, die abgerufen werden.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)