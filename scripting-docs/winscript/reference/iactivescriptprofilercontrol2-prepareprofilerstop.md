---
title: IActiveScriptProfilerControl2::P Analyse Profil erhalte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::PrepareProfilerStop
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24d4d73e0263882ad028ea66d3fac5e24f3af9ba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571444"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Benachrichtigt den Profiler, dass die Profilerstellung für alle anwendbaren Skript-Engines beendet werden soll. Wenn Sie diese Methode verwenden, können Sie die gesamte-Abruf Stapel abrufen, wenn [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ausgeführt wird, wenn Sie die Profilerstellung beenden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>Parameter  
 Die Methode nimmt keine Parameter an.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein HRESULT zurück. Folgende Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Die Profilerstellung konnte nicht gestartet werden.|  
|`S_FALSE`|Die Profilerstellung wurde beendet, als das Skript nicht ausgeführt wurde.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Die Profilerstellung ist nicht aktiviert.|  
  
## <a name="remarks"></a>Hinweise  
 Durch Aufrufen von `IActiveScriptProfilerControl2::PrepareProfilerStop` wird sichergestellt, dass Ereignisse für Funktionen in der aufrufenden Stapel gesendet werden. Diese Methode muss aufgerufen werden, bevor Sie die Profilerstellung für eine Skript-Engine, die sich auf der aktuellen Registerkarte befindet, beendet haben. Die-Methode kann für jede Skript-Engine aufgerufen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [IActiveScriptProfilerControl2-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)