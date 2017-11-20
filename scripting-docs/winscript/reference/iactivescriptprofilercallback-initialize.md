---
title: IActiveScriptProfilerCallback::Initialize | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.Initialize
apilocation: scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82e599ae94f422352706a0ec6cd9387bfa6799f2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackinitialize"></a>IActiveScriptProfilerCallback::Initialize
Wird aufgerufen, um das Profilerobjekt zu initialisieren, wenn die profilerstellung auf einem Skriptmodul gestartet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwContext`  
 [in] Eine 4-Byte-Wert, der übergeben wird [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md).  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein HRESULT zurück. Folgende Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn die Methode das Profilerobjekt nicht initialisieren kann, sollte es einen Fehler-HRESULT auf das Skriptmodul benachrichtigen zurückgeben. In diesem Fall sollte das Skriptmodul direkt aufrufen [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md), übergeben Sie das HRESULT im Parameter und lassen Sie anschließend das Profilerobjekt.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerCallback-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)