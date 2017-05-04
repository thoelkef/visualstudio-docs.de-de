---
title: "IActiveScriptProfilerCallback2-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2-Schnittstelle"
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptProfilerCallback2-Schnittstelle
Stellt Methoden bereit, die durch das Skriptmodul verwendet werden, um ein Profilerobjekt benachrichtigt, wenn Ereignisse des Dokumentobjektmodells \(Document Object Model\) auftreten.  Diese Schnittstelle wird durch das Profilerobjekt implementiert.  
  
## Methoden  
  
|Methode|Description|  
|-------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Benachrichtigt das Profilerobjekt, dass das Skriptmodul einen DOM\-Funktionsaufruf ausgeführt wird.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Benachrichtigt das Profilerobjekt, das das Skriptmodul darin, das einen DOM\-Funktionsaufruf Ausführen beendet wird.|  
  
## Hinweise  
 Die `IActiveScriptProfilerCallback2`\-Schnittstelle erstmals freigegeben mit Internet Explorer 9.  
  
 Benachrichtigung von Funktionsaufrufen, die nicht Aufrufe in das DOM sind, wird von [IActiveScriptProfilerCallback\-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md) bereitgestellt.  
  
> [!NOTE]
>  Um die Möglichkeit hinzuzufügen Profilerstellung starten und beenden wann ein Skript ausgeführt wird, rufen Sie die folgenden Methoden an.  Mit diesen Methoden, erhalten Sie die vollständige Aufrufliste, wenn [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ausgeführt wird, wenn Sie die Profilerstellung starten oder beenden.  
>   
>  -   Rufen Sie [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) an, um den Profiler zu benachrichtigen, dass Sie die Profilerstellung gestartet haben.  
> -   Rufen Sie [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) an, um den Profiler zu benachrichtigen, dass Sie bald beenden ein Profil zu erstellen.  
  
## Siehe auch  
 [Active Script Profiler\-Schnittstelle](../../winscript/reference/active-script-profiler-interfaces.md)