---
title: "IDiaSymbol::get_addressSection | Microsoft Docs"
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
  - "IDiaSymbol::get_addressSection-Methode"
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_addressSection
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Bereich in einem Adressenplatzes ab.  Verwenden Sie diese Option, wenn [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md) zu `LocIsStatic`festgelegt ist.  
  
## Syntax  
  
```cpp#  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt den Bereich in einem Adressenplatzes zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Hinweise  
 Für die statischen Member in einem externen DLL, ist der Abschnitt, der von dieser Methode zurückgegeben wird, 0, während diese Methode auf Abrufen der virtuelle Adresse des Members beruht.  Virtuelle Adressen sind nur gültig, wenn die [IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)\-Methode in der [IDiaSession](../../debugger/debug-interface-access/idiasession.md)\-Schnittstelle mit einem Parameter ungleich 0 \(null\) aufgerufen wurde, der die Ladeadresse der DLL angibt.  
  
 Um den Offset Teil einer Adresse abzurufen, rufen Sie die [IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)\-Methode auf.  
  
## Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|------------------|  
|Header:|dia2.h|  
|Version:|DIA SDK v7.0|  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md)