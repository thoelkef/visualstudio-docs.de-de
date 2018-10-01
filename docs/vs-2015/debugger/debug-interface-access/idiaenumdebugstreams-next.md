---
title: 'Idiaenumdebugstreams:: Next | Microsoft-Dokumentation'
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
- IDiaEnumDebugStreams::Next method
ms.assetid: eb8eae5a-be27-45f4-a7bd-6e4ef0652385
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 572d8b26244dea02a51a9ff009f871c8cff0ab8c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515867"
---
# <a name="idiaenumdebugstreamsnext"></a>IDiaEnumDebugStreams::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiaenumdebugstreams:: Next](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumdebugstreams-next).  
  
Ruft eine angegebene Anzahl von Debug-Streams in der Enumerationsfolge ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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



