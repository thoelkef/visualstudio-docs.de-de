---
title: IActiveScriptProfilerControl2::CompleteProfilerStart | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::CompleteProfilerStart
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36a1f5d6a1401e2860b65a29c8e383627e83c6be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993023"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Benachrichtigt den Profiler an, Sie begonnen haben, die profilerstellung auf allen anwendbaren Skript-Engines. Mithilfe dieser Methode können Sie die vollständige Aufrufliste abrufen, wenn [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] wird ausgeführt, wenn Sie mit der profilerstellung beginnen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>Parameter  
 Die Methode ist keine Parameter annimmt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein HRESULT zurück. Folgende Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Die profilerstellung kann nicht gestartet werden.|  
|`S_FALSE`|Die profilerstellung wurde gestartet, wenn ein Skript nicht ausgeführt wurde.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Die profilerstellung ist nicht aktiviert. Kein Rückruf es wurde festgelegt.|  
|`E_OUTOFMEMORY`|Die Aufrufliste kann nicht abgerufen werden, aufgrund einer Out-of-Memory-Bedingung.|  
  
## <a name="remarks"></a>Hinweise  
 Aufrufen von `IActiveScriptProfilerControl2::CompleteProfilerStart` wird sichergestellt, dass Ereignisse für Funktionen bereits in der Aufrufliste gesendet werden. Diese Methode muss aufgerufen werden, nach der profilerstellung beginnt, auf jedem Skript-Engine, die auf der aktuellen Registerkarte ist. Die Methode kann für alle Skript-Engine aufgerufen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)