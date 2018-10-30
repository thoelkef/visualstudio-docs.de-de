---
title: 'Idiasymbol:: Get_isstripped | Microsoft-Dokumentation'
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
- IDiaSymbol::get_isStripped method
ms.assetid: cc2c4a0b-ab9f-4b79-a8ff-a3badb0405d6
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c927a3213816c9f452b5c64796b2baaa6563f4ea
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847720"
---
# <a name="idiasymbolgetisstripped"></a>IDiaSymbol::get_isStripped
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft-Flag gibt an, ob private Symbole aus der Symboldatei entfernt wurden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_isStripped(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pFlag`  
 [out] Gibt `TRUE` wenn private Symbole aus der Symboldatei; entfernt wurden, andernfalls `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft ist verfügbar, aus der `SymTagExe` sprachsymboltyps fort (finden Sie unter [Exe](../../debugger/debug-interface-access/exe.md)).  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|DIA-SDK 8.0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)



