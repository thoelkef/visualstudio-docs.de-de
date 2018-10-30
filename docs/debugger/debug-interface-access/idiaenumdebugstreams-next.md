---
title: 'Idiaenumdebugstreams:: Next | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Next method
ms.assetid: eb8eae5a-be27-45f4-a7bd-6e4ef0652385
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5fc8bfcbf9d95e838648d8923c01cc9b145ed9bd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916221"
---
# <a name="idiaenumdebugstreamsnext"></a>IDiaEnumDebugStreams::Next
Ruft eine angegebene Anzahl von Debug-Streams in der Enumerationsfolge ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Next (   
   ULONG                     celt,   
   IDiaEnumDebugStreamData** rgelt,  
   ULONG*                    pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 celt  
 [in] **T**die Anzahl der Debug-Streams in der Enumerator abgerufen werden sollen.  
  
 rgelt  
 [out] Gibt ein Array von [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) Objekte, die das Debuggen stellt streams abgerufen wird.  
  
 pceltFetched  
 [out] Gibt die Anzahl der Debug-Streams zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn sind keine weitere Datenströme. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)