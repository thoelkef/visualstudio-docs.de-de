---
title: 'Idialoadcallback:: Notifyopendbg | Microsoft-Dokumentation'
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
- IDiaLoadCallback::NotifyOpenDBG method
ms.assetid: dbc4dcf0-4ace-4dce-9790-0fdaf3a23d3b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b28b6a6ce52fa278ce19f6cdc9ec4346770b6a3c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524133"
---
# <a name="idialoadcallbacknotifyopendbg"></a>IDiaLoadCallback::NotifyOpenDBG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idialoadcallback:: Notifyopendbg](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idialoadcallback-notifyopendbg).  
  
Wird aufgerufen, wenn eine Kandidat DBG-Datei geöffnet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT NotifyOpenDBG (   
   LPCOLESTR dbgPath,  
   HRESULT   resultCode  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dbgPath`  
 [in] Der vollständige Pfad der DBG-Datei.  
  
 `resultCode`  
 [in] Code, der den Erfolg angibt (`S_OK`) oder das Fehlschlagen der Last auf diese Datei angewendet.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Der Rückgabecode wird in der Regel ignoriert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)



