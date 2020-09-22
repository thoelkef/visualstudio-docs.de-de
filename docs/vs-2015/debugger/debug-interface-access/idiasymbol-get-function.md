---
title: 'Idiasymmetribol:: get_function | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_function method
ms.assetid: 48b3a318-3211-410f-8570-c02ee210f0a5
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e5248f94fed23a894fb1c7e988043f44bb27b7a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840875"
---
# <a name="idiasymbolget_function"></a>IDiaSymbol::get_function
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Flag ab, das angibt, ob das öffentliche Symbol auf eine Funktion verweist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_function (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt einen zurück `TRUE` , wenn das Symbol auf eine Funktion verweist; andernfalls wird zurückgegeben `FALSE` .  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der- `S_FALSE` oder-Fehlercode zurückgegeben.  
  
> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|BESCHREIBUNG|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|Dia SDK v 7.0|  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
