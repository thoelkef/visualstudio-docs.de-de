---
title: 'IRemoteDebugApplication110:: getmainthread | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetMainThread
ms.assetid: 9982acc9-3d35-4dcf-8ca9-662469de4072
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8e4ae024429702f3268a01c1e2e1fb4b40294d8
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985289"
---
# <a name="iremotedebugapplication110getmainthread"></a>IRemoteDebugApplication110::GetMainThread
Gibt den Haupt Thread für Hosts zurück, die [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite)aufrufen; andernfalls wird E_FAIL zurückgegeben.  
  
> [!IMPORTANT]
> Die [iremotedebuapplication-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md) wird von PDM v 11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetMainThread([out] IRemoteDebugApplicationThread **ppThread);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppThread`  
 vorgenommen Die Haupt- [iremotedebugapplicationthread-Schnittstelle](../../winscript/reference/iremotedebugapplicationthread-interface.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Iremotedebuapplication-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110-Schnittstelle](../../winscript/reference/iremotedebugapplication110-interface.md)