---
title: 'Idiasymbol:: Get_ishotpatchable | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaSymbol::get_isHotpatchable method
ms.assetid: b7b6f490-1cf2-4a68-9237-b152dac84d3c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c33c26ba9c46d5ae4183cec60a01052af50f30b2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915905"
---
# <a name="idiasymbolgetishotpatchable"></a>IDiaSymbol::get_isHotpatchable
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Flag, der angibt, ob das Modul kompiliert wurde, mit der [/hotpatch (Erstellen eines Hotpatch-fähigen Abbildes)](http://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798) Compilerschalter.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_isHotpatchable(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pFlag`  
 [out] Gibt `TRUE` gibt zurück, wenn das Modul, andernfalls "heiß"-patchfähigen ist, `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder den Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft ist verfügbar, aus der `SymTagCompilandDetails` sprachsymboltyps fort (finden Sie unter [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)).  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|DIA-SDK 8.0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)



