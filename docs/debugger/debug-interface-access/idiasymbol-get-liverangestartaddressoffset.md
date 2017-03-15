---
title: "IDiaSymbol::get_liveRangeStartAddressOffset | Microsoft Docs"
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
  - "IDiaSymbol::get_liveRangeStartAddressOffset"
ms.assetid: f5b28914-0a14-4b22-8259-59d7f97ee610
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_liveRangeStartAddressOffset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt den Offset Teil der Startadresse des Bereichs zurück, in dem das lokale Symbol gültig ist.  
  
## Syntax  
  
```cpp#  
HRESULT get_liveRangeStartAddressOffset (   
   DWORD* offset  
);  
```  
  
#### Parameter  
 `offset`  
 \[out\]  Gibt den Offset des Startadressen Bereichs zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
> [!NOTE]
>  Ein zurückgegebener Fehlercode bedeutet, dass das Symbol nicht aktive Bereichs Informationen verfügt.  
  
## Hinweise  
 Die Adresse, die von den Abschnitt und den Offset gebildet wird, ist der Anfang des Bereichs, in dem das Symbol gültig ist.  
  
 So legen Sie den Abschnitt Teil der Adresse abzurufen, verwenden Sie [IDiaSymbol::get\_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md).  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia100.dll  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)