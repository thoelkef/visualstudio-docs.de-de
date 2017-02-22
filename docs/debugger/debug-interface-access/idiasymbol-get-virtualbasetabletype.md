---
title: "IDiaSymbol::get_virtualBaseTableType | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "IDiaSymbol::get_virtualBaseTableType-Methode"
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_virtualBaseTableType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Typ eines virtuellen Basistabellenzeigers ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_virtualBaseTableType(  
   IDiaSymbol *pRetVal  
};  
```  
  
#### Parameter  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`pRetVal`|\[out\]  Gibt ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekt zurück, das den Typ der Basistabelle angibt.|  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Hinweise  
 Ein virtueller Basistabellen`vbtptr`\(Zeiger\) ist ein ausgeblendeter Zeiger in vtable  [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], der Vererbung von virtuellen Basisklasse behandelt.  `vbtptr` unterschiedlicher Größe kann je nach den geerbten Klassen verfügen.  
  
 Diese Methode gibt ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekt zurück, das verwendet werden kann, um die Größe des vbtptr zu bestimmen.  
  
## Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|------------------|  
|Header:|dia2.h|  
|Version:|DIA SDK v8.0|  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)