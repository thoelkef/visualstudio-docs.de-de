---
title: Iactivescriptprofilercallback-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ae520dcb36e00dfaba8702db6294a5a47484b0a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571716"
---
# <a name="iactivescriptprofilercallback-interface"></a>IActiveScriptProfilerCallback-Schnittstelle
Stellt Methoden bereit, die von der Skript-Engine zum Benachrichtigen eines Profiler-Objekts beim Auftreten von Ereignissen verwendet werden. Diese Schnittstelle wird vom Profiler-Objekt implementiert.  
  
## <a name="methods"></a>Methoden  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Wird aufgerufen, um das profilerobjekt zu initialisieren, wenn die Profilerstellung für eine Skript-Engine gestartet wird.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Wird aufgerufen, um das profilerobjekt freizugeben und freizugeben, wenn die Profilerstellung für eine Skript-Engine beendet wurde|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Benachrichtigt das Profiler-Objekt, dass die Skript-Engine das Skript kompiliert hat.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Benachrichtigt das Profiler-Objekt, dass die Skript-Engine beim Kompilieren eines Skripts eine Funktion gefunden hat.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Benachrichtigt das Profiler-Objekt, dass die Skript-Engine im Begriff ist, einen Funktions aufrut auszuführen, der kein Dokumentobjektmodell (DOM) aufruft.|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Benachrichtigt das Profiler-Objekt, dass die Skript-Engine das Ausführen eines Funktions Aufrufes beendet hat, der kein Dom-Aufrufvorgang ist.|  
  
## <a name="remarks"></a>Hinweise  
 Die Benachrichtigung von Funktionsaufrufen in der Dokumentobjektmodell (DOM) wird von der [IActiveScriptProfilerCallback2-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback2-interface.md)bereitgestellt.  
  
> [!NOTE]
> Um die Möglichkeit zum Starten und Beenden der Profilerstellung beim Ausführen eines Skripts hinzuzufügen, müssen Sie die folgenden Methoden abrufen. Wenn Sie diese Methoden verwenden, können Sie die gesamte-Abruf Stapel abrufen, wenn [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ausgeführt wird, wenn Sie die Profilerstellung starten oder beenden.  
> 
> - Nennen Sie [IActiveScriptProfilerControl2:: completeprofilerstart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) , um den Profiler zu benachrichtigen, dass Sie mit der Profilerstellung begonnen haben.  
>   - Wenden Sie sich an [IActiveScriptProfilerControl2::P eneprofilerstoppt](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) , um den Profiler zu benachrichtigen, dass Sie die Profilerstellung bald abbrechen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Profilerschnittstelle](../../winscript/reference/active-script-profiler-interfaces.md)