---
title: IActiveScriptProfilerControl::StopProfiling | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerControl.StopProfiling
apilocation: scrobj.dll
ms.assetid: 23b46ed6-a398-44c0-bc49-bf122e697cfe
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63d837b0f7a59b1e3efc832c4d98cb7dcab5447c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrolstopprofiling"></a>IActiveScriptProfilerControl::StopProfiling
Beendet die profilerstellung auf dem Skriptmodul. Diese Methode ruft [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) für die Profilerobjekt und gibt dann frei.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT StopProfiling(  
    [in] HRESULT hrShutdownReason);  
```  
  
#### <a name="parameters"></a>Parameter  
 `hrShutdownReason`  
 [in] Das HRESULT, das als Parameter an übergeben werden die [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) -Methode des Profiler-Objekts.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein HRESULT zurück. Folgende Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Die profilerstellung ist nicht aktiviert.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerControl-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol-interface.md)