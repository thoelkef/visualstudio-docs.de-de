---
title: 'Idiasymbol:: Get_isltcg | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isLTCG method
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a799cf16dbf603f75cd810f9c249f4c0e8ba49ec
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
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