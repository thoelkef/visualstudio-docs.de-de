---
title: "IDiaSymbol::get_virtualTableShapeId | Microsoft Docs"
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
  - "IDiaSymbol::get_virtualTableShapeId-Methode"
ms.assetid: cbee9944-817a-4805-9c08-fac8e0da58b7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_virtualTableShapeId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den virtuellen form\-Symbol Tabellen Bezeichner des Symbols ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_virtualTableShapeId (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt die virtuelle Tabellenform\-Symbol ID des Symbols zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Hinweise  
 Der Bezeichner ist ein eindeutiger Wert, der vom DIA SDK erstellt wird, um alle Symbole zu markieren, wie eindeutig.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)