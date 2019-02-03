---
title: 'Idiaenumdebugstreams:: Get__newenum | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::get__NewEnum method
ms.assetid: 972372ff-abfc-4987-a302-7788fab90348
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f1f0b52a4400f2b7cba6911777c0f14bb218609
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972637"
---
# <a name="idiaenumdebugstreamsgetnewenum"></a>IDiaEnumDebugStreams::get__NewEnum
Ruft die <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> Version von diesem Enumerator.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pRetVal  
 [out] Gibt die `IUnknown` Schnittstelle, die darstellt der <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> Version von diesem Enumerator.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)