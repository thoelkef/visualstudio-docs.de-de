---
title: 'Idiasymbol:: Get_thunkordinal | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f8af5be5e094d01d5015fdd181be6d7348d6ff68
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520444"
---
# <a name="idiasymbolgetthunkordinal"></a>IDiaSymbol::get_thunkOrdinal
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiasymbol:: Get_thunkordinal](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-thunkordinal).  
  
Ruft den Thunk-Typ, der eine Funktion ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt einen Wert aus der [THUNK_ORDINAL-Enumeration](../../debugger/debug-interface-access/thunk-ordinal.md) -Enumeration, die den Thunk-Typ, der eine Funktion angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft gilt nur, wenn das Symbol als ein [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Wert `SymTagThunk`.  
  
 Ein "Thunk" ist ein Codeabschnitt, der einen 16-Bit-Adressraum (als einen segmentierten Adressraum bezeichnet) bis ein Arbeitsspeicher von 32-Bit-Adressraum (auch bekannt als flache Adressraum) konvertiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [THUNK_ORDINAL-Enumeration](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)



