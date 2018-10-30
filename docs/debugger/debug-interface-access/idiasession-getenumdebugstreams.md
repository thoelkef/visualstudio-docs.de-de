---
title: 'Idiasession:: Getenumdebugstreams | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumDebugStreams method
ms.assetid: d294954b-80e9-476c-b9f0-5ca6fd575f68
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 53eb0765b7a3d9ed5fb23c0b1d8880eeca390159
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818796"
---
# <a name="idiasessiongetenumdebugstreams"></a>IDiaSession::getEnumDebugStreams
Ruft eine aufgelistete Sequenz von Debug-Datenströme.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT getEnumDebugStreams (   
   IDiaEnumDebugStreams** ppEnumDebugStreams  
)  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppEnumDebugStreams`  
 [out] Gibt eine [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md) -Objekt, das eine Liste von Debug-Streams enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)