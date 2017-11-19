---
title: IActiveScriptProfilerControl2::PrepareProfilerStop | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptProfilerControl2::PrepareProfilerStop
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78078cd874be1d7d3d169be2d3d70e65866be3fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Benachrichtigt den Profiler, dass Sie für alle anwendbaren Skriptmodule profilerstellung beenden möchten. Mithilfe dieser Methode können Sie die vollständige Aufrufliste abrufen, wenn [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ausgeführt wird, wenn Sie die profilerstellung beenden.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>Parameter  
 Die Methode keine Parameter annimmt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein HRESULT zurück. Folgende Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Profilerstellung konnte nicht gestartet werden.|  
|`S_FALSE`|Profilerstellung wurde beendet, wenn ein Skript nicht ausgeführt wurde.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Die profilerstellung ist nicht aktiviert.|  
  
## <a name="remarks"></a>Hinweise  
 Aufrufen von `IActiveScriptProfilerControl2::PrepareProfilerStop` wird sichergestellt, dass Ereignisse für Funktionen in der Aufrufliste gesendet werden. Diese Methode muss aufgerufen werden, bevor Sie die profilerstellung auf alle Skriptmodul, die auf der Registerkarte "aktuelle" beenden. Die Methode kann für alle Skriptmodul aufgerufen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [IActiveScriptProfilerControl2-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)