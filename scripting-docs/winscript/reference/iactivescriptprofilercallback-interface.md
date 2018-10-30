---
title: IActiveScriptProfilerCallback-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2511b3e622dfa977c0ed05212203ad59fb0e71bd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912618"
---
# <a name="iactivescriptprofilercallback-interface"></a>IActiveScriptProfilerCallback-Schnittstelle
Bietet Methoden, die von der Skript-Engine verwendet werden, um eine Profilerobjekt zu benachrichtigen, wenn Ereignisse auftreten. Diese Schnittstelle wird von der Profilerobjekt implementiert.  
  
## <a name="methods"></a>Methoden  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Wird aufgerufen, um das Profilerobjekt zu initialisieren, wenn die profilerstellung einer Skript-Engine gestartet wurde.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Wird aufgerufen, um kostenlose und das Profilerobjekt frei, wenn auf eine Skript-Engine die profilerstellung beendet wird.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Benachrichtigt den Profiler an, dass Objekt, das die Skript-Engine-das Skript kompiliert.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Benachrichtigt dem Profiler-Objekt, das die Skript-Engine-eine Funktion auftreten, wenn Sie ein Skript zu kompilieren.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Benachrichtigt den Profilerobjekt, das die Skript-Engine einen Funktionsaufruf, der keinem Aufruf in das Document Objekt Model (DOM) ist, ausgeführt wird.|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Benachrichtigt den Profiler, dass das Objekt, dass die Skript-Engine beendet die Ausführung einer Funktion aufrufen, keinen Aufruf in das DOM ist|  
  
## <a name="remarks"></a>Hinweise  
 Benachrichtigung über Funktionsaufrufe in das Document Objekt Model (DOM) erfolgt über die [IActiveScriptProfilerCallback2-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
>  Rufen Sie die folgenden Methoden zum Hinzufügen der Möglichkeit zum Starten und Beenden der profilerstellung, wenn ein Skript ausgeführt wird. Sie können mit diesen Methoden, die vollständige Aufrufliste abrufen, wenn [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] beim Starten oder Beenden der profilerstellung ausgeführt wird.  
> 
> - Rufen Sie [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) dem Profiler benachrichtigt, dass Sie die profilerstellung gestartet wurde.  
>   -   Rufen Sie [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) dem Profiler benachrichtigt, dass Sie bald profilerstellung beendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Profilerschnittstelle](../../winscript/reference/active-script-profiler-interfaces.md)