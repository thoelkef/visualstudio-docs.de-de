---
title: "IDiaSymbol::get_length | Microsoft Docs"
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
  - "IDiaSymbol::get_length-Methode"
ms.assetid: cc62f028-d195-4fbf-93bc-10b08bef52d2
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSymbol::get_length
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Anzahl der Bits oder Bytes des Arbeitsspeichers für das Objekt ab, auf das dieses Symbol dargestellt wird.  
  
## Syntax  
  
```cpp#  
HRESULT get_length (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt die Anzahl der Bytes oder Bits des Arbeitsspeichers für das Objekt zurück, das durch dieses Symbol dargestellt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Hinweise  
 Wenn [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md) des Symbols `LocIsBitField`ist, wird die Länge von dieser Methode zurückgegeben in Bits. Andernfalls ist die Länge in Bytes für alle anderen Speicherort Typen.  
  
## Beispiel  
  
```cpp#  
IDiaSymbol* pSymbol;  
ULONGLONG   length;  
pSymbol->get_length( &length );  
```  
  
## Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|------------------|  
|Header:|dia2.h|  
|Version:|DIA SDK v7.0|  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType\-Enumeration](../../debugger/debug-interface-access/locationtype.md)