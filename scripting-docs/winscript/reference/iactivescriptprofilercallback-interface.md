---
title: "IActiveScriptProfilerCallback-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IActiveScriptProfilerCallback-Schnittstelle
Stellt Methoden bereit, die durch das Skriptmodul verwendet werden, um ein Profilerobjekt benachrichtigt, wenn Ereignisse auftreten.  Diese Schnittstelle wird durch das Profilerobjekt implementiert.  
  
## Methoden  
  
|Methode|Description|  
|-------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Wird aufgerufen, um das Profilerobjekt zu initialisieren, wenn ein Profil erstellen auf einem Skriptmodul gestartet wird.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Wird aufgerufen, um das Profilerobjekt, wenn die Profilerstellung freizugeben auf einem Skriptmodul beendet wird.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Benachrichtigt das Profilerobjekt, dass das Skriptmodul das Skript kompilierte.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Benachrichtigt das Profilerobjekt, dass das Skriptmodul eine Funktion antraf, als, ein Skript kompilieren.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Benachrichtigt das Profilerobjekt, dass das Skriptmodul im Begriff ist, einen Funktionsaufruf auszuführen, der kein Aufruf des DOM\- \(Document Object Model\) ist.|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Benachrichtigt das Profilerobjekt, das das Skriptmodul darin, das einen Funktionsaufruf ausgeführt wird, beendet wird, der kein Aufruf in das DOM ist.|  
  
## Hinweise  
 Benachrichtigung von Funktionsaufrufen in das Dokumentobjektmodell \(DOM\) wird von [IActiveScriptProfilerCallback2\-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback2-interface.md) bereitgestellt.  
  
> [!NOTE]
>  Um die Möglichkeit hinzuzufügen Profilerstellung starten und beenden wann ein Skript ausgeführt wird, rufen Sie die folgenden Methoden an.  Mit diesen Methoden, erhalten Sie die vollständige Aufrufliste, wenn [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ausgeführt wird, wenn Sie die Profilerstellung starten oder beenden.  
>   
>  -   Rufen Sie [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) an, um den Profiler zu benachrichtigen, dass Sie die Profilerstellung gestartet haben.  
> -   Rufen Sie [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) an, um den Profiler zu benachrichtigen, dass Sie bald beenden ein Profil zu erstellen.  
  
## Siehe auch  
 [Active Script Profiler\-Schnittstelle](../../winscript/reference/active-script-profiler-interfaces.md)