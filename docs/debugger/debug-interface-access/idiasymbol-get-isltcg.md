---
title: 'Idiasymbol:: Get_isltcg | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_isLTCG method
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9be567714b30eea80579836b2a596bbf4f872e3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetisltcg"></a>IDiaSymbol::get_isLTCG
Ruft ein Flag, das angibt, ob die [Compiland](../../debugger/debug-interface-access/compiland.md) verknüpft wurde mit den Linkerschalter [/LTCG (Link-Time Code Generation)](/cpp/build/reference/ltcg-link-time-code-generation), unterstützt die Optimierung des gesamten Programms. Diese Option gilt nur für verwalteten Code.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_iSLTCG(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pFlag  
 [out] Gibt `TRUE` Wenn die `compiland` wurde mit den Linkerschalter/LTCG verknüpft ist, andernfalls `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Ein Rückgabewert von `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|DIA-SDK 8.0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)