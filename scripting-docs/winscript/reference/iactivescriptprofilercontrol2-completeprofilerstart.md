---
title: 'IActiveScriptProfilerControl2:: completeprofilerstart | Microsoft-Dokumentation'
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
ms.openlocfilehash: f0230ecb480792b5b24b7375f5b95926735d0a61
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571555"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Benachrichtigt den Profiler, dass Sie die Profilerstellung für alle anwendbaren Skript-Engines gestartet haben. Wenn Sie diese Methode verwenden, können Sie die gesamte-Abruf Stapel abrufen, wenn [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ausgeführt wird, wenn Sie mit der Profilerstellung beginnen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>Parameter  
 Die Methode nimmt keine Parameter an.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein HRESULT zurück. Folgende Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Die Profilerstellung kann nicht gestartet werden.|  
|`S_FALSE`|Die Profilerstellung wurde gestartet, als das Skript nicht ausgeführt wurde.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Die Profilerstellung ist nicht aktiviert. Es wurde kein Rückruf festgelegt.|  
|`E_OUTOFMEMORY`|Die-Rückruf Stapel kann nicht abgerufen werden, weil nicht genügend Arbeitsspeicher verfügbar ist.|  
  
## <a name="remarks"></a>Hinweise  
 Durch Aufrufen von `IActiveScriptProfilerControl2::CompleteProfilerStart` wird sichergestellt, dass Ereignisse für Funktionen, die bereits in der aufrufenden Stapel vorhanden sind Diese Methode muss aufgerufen werden, nachdem die Profilerstellung für eine beliebige Skript-Engine auf der aktuellen Registerkarte gestartet wurde. Die-Methode kann für jede Skript-Engine aufgerufen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)