---
title: 'Idiaenumdebugstreams:: Clone | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Clone method
ms.assetid: e85ec592-de97-4f95-a774-1623315ba415
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e22f7fffa3b1eab0726b47b8b4d8a23c91804b2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875350"
---
# <a name="idiaenumdebugstreamsclone"></a>IDiaEnumDebugStreams::Clone
Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Clone (   
   IDiaEnumDebugStreams** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppenum`  
 [out] Gibt eine [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md) Objekt, das ein Duplikat des Enumerators enthält. Die Datenströme werden nicht dupliziert werden, nur den Enumerator.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)