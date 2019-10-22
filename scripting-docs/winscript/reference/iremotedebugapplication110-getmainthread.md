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
ms.openlocfilehash: ff99c43f633da8454eb5fa32463886877e06ed72
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574122"
---
# <a name="iremotedebugapplication110getmainthread"></a>IRemoteDebugApplication110::GetMainThread
Gibt den Haupt Thread für Hosts zurück, die [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)aufrufen; andernfalls wird E_FAIL zurückgegeben.  
  
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