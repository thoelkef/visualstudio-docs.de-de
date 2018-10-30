---
title: 'Idiasymbol:: Get_hfafloat | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hfaFloat method
ms.assetid: 73ddcffe-cdac-4b03-be42-82ef985d17ee
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ae61d8c4c82eb8e0493574fc8469355f07f6a796
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900240"
---
# <a name="idiasymbolgethfafloat"></a>IDiaSymbol::get_hfaFloat
Ruft ein Flag, das angibt, ob ein benutzerdefinierten Typ (UDT) homogene Gleitkomma (zu HFA) Aggregatdaten von Typ "float" enthält.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_hfaFloat(   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt `TRUE` , wenn der UDT zu HFA-Daten des Typs "float"; enthält andernfalls `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)