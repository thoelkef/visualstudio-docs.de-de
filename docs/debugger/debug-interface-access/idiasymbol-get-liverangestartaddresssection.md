---
title: "IDiaSymbol::get_liveRangeStartAddressSection | Microsoft Docs"
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
helpviewer_keywords: 
  - "IDiaSymbol::get_liveRangeStartAddressSection"
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_liveRangeStartAddressSection
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt den Teil der Startadresse des Bereichs Bereich zurück, in dem das lokale Symbol gültig ist.  
  
## Syntax  
  
```cpp#  
HRESULT get_liveRangeStartAddressSection (   
   DWORD* section  
);  
```  
  
#### Parameter  
 `section`  
 \[out\]  Gibt den Bereich des Startadressen Bereichs zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
> [!NOTE]
>  Ein zurückgegebener Fehlercode bedeutet, dass das Symbol nicht aktive Bereichs Informationen verfügt.  
  
## Hinweise  
 Die Adresse, die von den Abschnitt und den Offset gebildet wird, ist der Anfang des Bereichs, in dem das Symbol gültig ist.  
  
 Um den Offset Teil der Adresse abzurufen, verwenden Sie [IDiaSymbol::get\_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md).  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia100.dll  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)