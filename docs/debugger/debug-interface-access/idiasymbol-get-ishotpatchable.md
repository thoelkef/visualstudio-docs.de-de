---
title: "IDiaSymbol::get_isHotpatchable | Microsoft Docs"
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
  - "IDiaSymbol::get_isHotpatchable-Methode"
ms.assetid: b7b6f490-1cf2-4a68-9237-b152dac84d3c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_isHotpatchable
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Flag ab, das angibt, ob das Modul mit dem [\/hotpatch \(Erstellen eines Hotpatch\-fähigen Abbildes\)](/visual-cpp/build/reference/hotpatch-create-hotpatchable-image) Compilerschalter kompiliert wurde.  
  
## Syntax  
  
```cpp#  
HRESULT get_isHotpatchable(  
   BOOL *pFlag  
);  
```  
  
#### Parameter  
 `pFlag`  
 \[out\]  Gibt `TRUE` zurück, wenn das Modul heiß\-patchable ist. andernfalls gibt `FALSE`zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Hinweise  
 Diese Eigenschaft ist vom Typ `SymTagCompilandDetails` Symbol verfügbar \(siehe [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)\).  
  
## Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|------------------|  
|Header:|dia2.h|  
|Version:|DIA SDK v8.0|  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)