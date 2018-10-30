---
title: 'Idiasymbol:: Get_oemsymbolid | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_oemSymbolId method
ms.assetid: 187801f0-bd82-4c5b-9fae-8eeb1a4ac0ce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3b15cbfc289a88059960603159db3a7d57fd011
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917166"
---
# <a name="idiasymbolgetoemsymbolid"></a>IDiaSymbol::get_oemSymbolId
Ruft die ID-Wert des Symbols für Originalgerätehersteller (OEM) ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_oemSymbolId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt an, die einer OEMs intern zugewiesene symbol-ID  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="remarks"></a>Hinweise  
 Der Bezeichner ist ein eindeutiger Wert erstellt, das DIA SDK alle Symbole als eindeutig kennzeichnen.  
  
 Diese Eigenschaft gilt nur für Symbole mit einem [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Typ `SymTagCustomType`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)