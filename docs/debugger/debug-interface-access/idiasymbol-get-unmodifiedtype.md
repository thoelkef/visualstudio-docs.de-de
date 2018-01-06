---
title: 'Idiasymbol:: Get_unmodifiedtype | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_unmodifiedType method
ms.assetid: bf914dc0-ff84-4f5d-9f75-1733b17f3be0
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 552a1588b4ea1b4e5bc1cbc4d7ce87233dc74ea8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetunmodifiedtype"></a>IDiaSymbol::get_unmodifiedType
Ruft den ursprünglichen Typ für dieses Symbol ab. Verwenden in folgenden Fällen die [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) auf einen Typ festgelegt ist.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_unmodifiedType(   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt eine [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt, das den ursprünglichen Typ dieses Symbols darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Ein Rückgabewert von `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="remarks"></a>Hinweise  
 Der aktuelle Typ ist eine Änderung des ursprünglichen zurückgegebenen Typs. Der ursprüngliche Typ für ein Symbol kann zuerst Abrufen des Typs des Symbols, und klicken Sie dann befragen zurückgegebenen Typ für den ursprünglichen Typ ermittelt werden. Beachten Sie, dass einige Symbole möglicherweise nicht über einen geänderten Typ des ursprünglichen Typs.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)