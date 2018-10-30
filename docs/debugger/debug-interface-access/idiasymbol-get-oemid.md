---
title: 'Idiasymbol:: Get_oemid | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_oemId method
ms.assetid: c472830f-c3eb-46ab-9498-cd637763d241
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8208d146284926ce7ec3375e8416210eeb5d214c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875254"
---
# <a name="idiasymbolgetoemid"></a>IDiaSymbol::get_oemId
Ruft die ID-Wert für das Symbol des Originalgerätehersteller (OEM) ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_oemId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt einen eindeutigen Wert, der einen OEM identifiziert.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft gilt nur für Symbole mit einem [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Typ `SymTagCustomType`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)