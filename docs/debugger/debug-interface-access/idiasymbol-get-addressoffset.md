---
title: "IDiaSymbol::get_addressOffset | Microsoft Docs"
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
  - "IDiaSymbol::get_addressOffset-Methode"
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_addressOffset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Offset in einem Adressenplatzes ab.  Verwenden Sie diese Option, wenn [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md) zu `LocIsStatic`festgelegt ist.  
  
## Syntax  
  
```cpp#  
HRESULT get_addressOffset (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt den Offset in einem Adressenplatzes zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Hinweise  
 Für die statischen Member in einem externen DLL, ist der Offset, der von dieser Methode zurückgegeben wird, 0, während diese Methode auf Abrufen der virtuelle Adresse des Members beruht.  Virtuelle Adressen sind nur gültig, wenn die [IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)\-Methode in der [IDiaSession](../../debugger/debug-interface-access/idiasession.md)\-Schnittstelle mit einem Parameter ungleich 0 \(null\) aufgerufen wurde, der die Ladeadresse der DLL angibt.  
  
 Um den Abschnitt Teil einer Adresse abzurufen, rufen Sie die [IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)\-Methode auf.  
  
## Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|------------------|  
|Header:|dia2.h|  
|Version:|DIA SDK v7.0|  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md)   
 [IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)