---
title: 'Idiasymbol:: Get_scoped | Microsoft-Dokumentation'
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
- IDiaSymbol::get_scoped method
ms.assetid: 588163f7-958e-4072-bf66-db5c5f07d3cb
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d40a4116eb950710be181a3b5ca4ca0f8e6c367
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513366"
---
# <a name="idiasymbolgetscoped"></a>IDiaSymbol::get_scoped
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiasymbol:: Get_scoped](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-scoped).  
  
Ruft ein Flag, das angibt, ob der benutzerdefinierte Datentyp in einen nicht-globalen lexikalischen Gültigkeitsbereich angezeigt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_scoped (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt `TRUE` , wenn der benutzerdefinierte Datentyp in einen nicht-globalen lexikalischen Gültigkeitsbereich; angezeigt wird, andernfalls `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



