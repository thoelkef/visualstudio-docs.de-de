---
title: IActiveScriptProfilerCallback2-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25f9616497192659df67feedfe16bd9ea0c5e3b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577302"
---
# <a name="iactivescriptprofilercallback2-interface"></a>IActiveScriptProfilerCallback2-Schnittstelle
Stellt Methoden bereit, die von der Skript-Engine zum Benachrichtigen eines Profiler-Objekts verwendet werden, wenn Dokumentobjektmodell (DOM)-Ereignisse auftreten. Diese Schnittstelle wird vom Profiler-Objekt implementiert.  
  
## <a name="methods"></a>Methoden  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Benachrichtigt das Profiler-Objekt, dass die Skript-Engine einen Dom-Funktions aufruflauf ausführen wird.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Benachrichtigt das Profiler-Objekt, dass die Skript-Engine die Ausführung eines DOM-Funktions Aufrufes beendet hat.|  
  
## <a name="remarks"></a>Hinweise  
 Die `IActiveScriptProfilerCallback2`-Schnittstelle, die zuerst mit Internet Explorer 9 veröffentlicht wurde.  
  
 Die Benachrichtigung über Funktionsaufrufe, die nicht im Dom aufgerufen werden, wird von der [iactivescriptprofilercallback-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)bereitgestellt.  
  
> [!NOTE]
> Um die Möglichkeit zum Starten und Beenden der Profilerstellung beim Ausführen eines Skripts hinzuzufügen, müssen Sie die folgenden Methoden abrufen. Wenn Sie diese Methoden verwenden, können Sie die gesamte-Abruf Stapel abrufen, wenn [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ausgeführt wird, wenn Sie die Profilerstellung starten oder beenden.  
> 
> - Nennen Sie [IActiveScriptProfilerControl2:: completeprofilerstart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) , um den Profiler zu benachrichtigen, dass Sie mit der Profilerstellung begonnen haben.  
>   - Wenden Sie sich an [IActiveScriptProfilerControl2::P eneprofilerstoppt](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) , um den Profiler zu benachrichtigen, dass Sie die Profilerstellung bald abbrechen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Profilerschnittstelle](../../winscript/reference/active-script-profiler-interfaces.md)