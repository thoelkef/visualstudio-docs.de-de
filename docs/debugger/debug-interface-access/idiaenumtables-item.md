---
title: "IDiaEnumTables::Item | Microsoft Docs"
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
helpviewer_keywords: 
  - "IDiaEnumTables::Item-Methode"
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaEnumTables::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine Tabelle mithilfe eines Indexes oder eines Titels ab.  
  
## Syntax  
  
```cpp#  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### Parameter  
 `index`  
 \[in\]  Index oder Name abgerufen werden soll [IDiaTable](../../debugger/debug-interface-access/idiatable.md) .  Wenn eine integrale Variante verwendet wird, muss sie `count`im Bereich von 0 bis \-1 liegen, wobei `count` wurde, aufgezeichnet von der [IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)\-Methode zurückgegeben wird.  
  
 `table`  
 \[out\]  Gibt ein [IDiaTable](../../debugger/debug-interface-access/idiatable.md)\-Objekt zurück, das die gewünschte Tabelle darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Wenn eine abweichende Zeichenfolgen angegeben wird, dann den Zeichenfolgennamen eine bestimmte Tabelle.  Der Name sollte einer der Tabellennamen, wie in [Konstanten \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)definiert.  
  
## Beispiel  
  
```cpp#  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## Siehe auch  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Konstanten \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)