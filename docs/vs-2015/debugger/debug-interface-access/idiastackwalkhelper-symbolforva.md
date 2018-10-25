---
title: 'Idiastackwalkhelper:: Symbolforva | Microsoft-Dokumentation'
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
- IDiaStackWalkHelper::symbolForVA method
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a3478fb9d32bdda53c74de4d7c49a805fe72c9db
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889515"
---
# <a name="idiastackwalkhelpersymbolforva"></a>IDiaStackWalkHelper::symbolForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ab, das Symbol, das die angegebene virtuelle Adresse enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT symbolForVA(   
   ULONGLONG     va,  
   IDiaSymbol**  ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `va`  
 [in] Die virtuelle Adresse, die im angeforderten Symbol enthalten ist. Das Symbol muss eine `SymTagFunctionType` (ein Wert aus der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Enumeration).  
  
 `ppSymbol`  
 [out] Ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt, das Symbol an der angegebenen Adresse darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



