---
title: 'Idiasymbol:: Get_issplitted | Microsoft-Dokumentation'
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
- IDiaSymbol::get_isSplitted method
ms.assetid: ff160cf6-003b-4ef5-a406-20a7b287b2bf
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35cec389a55dd70dc2407384a34bd0ff0bf5e804
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512900"
---
# <a name="idiasymbolgetissplitted"></a>IDiaSymbol::get_isSplitted
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiasymbol:: Get_issplitted](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-issplitted).  
  
Ruft ein Flag, das angibt, ob das Datensymbol in eine Aggregation oder eine Auflistung von anderen Symbolen aufgeteilt wurde; der Compiler behandelt die Symbole als separate Entitäten, obwohl sie eigentlich Teil eines größeren Symbols sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT get_isSplitted(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pFlag`  
 [out] Gibt `TRUE` , wenn das Symbol in ein Aggregat von Symbolen; aufgeteilt wurde, andernfalls `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder den Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="remarks"></a>Hinweise  
 Die [idiasymbol:: Get_isaggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md) Methodenrückgabe `TRUE` für alle Symbole, die Teil eines Split-Symbols.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|DIA-SDK 8.0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)



