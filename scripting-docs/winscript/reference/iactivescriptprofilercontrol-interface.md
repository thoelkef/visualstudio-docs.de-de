---
title: "IActiveScriptProfilerControl-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptProfilerControl-Schnittstelle
Durch das Skriptmodul, das Profilerstellung unterstützt.  In der Regel implementiert ein Objekt, das `IActiveScriptProfilerControl` auch implementiert, die [IActiveScript](../../winscript/reference/iactivescript.md)\-Schnittstelle.  In diesem Fall können Sie ein Handle zur `IActiveScriptProfilerControl`\-Schnittstelle erhalten, indem Sie die `IUnknown::QueryInterface`\-Methode für das Objekt aufrufen.  Die Schnittstelle stellt die erforderlichen Methoden für das Beenden und Starten der Profilerstellung auf dem Skriptmodul bereit.  
  
## Methoden  
  
|Methode|Description|  
|-------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|beginnt, die auf dem Skriptmodul ein Profil erstellen.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Legt die Profilerereignismaske im Skriptmodul fest.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Beenden, die auf dem Skriptmodul ein Profil erstellen.|  
  
## Siehe auch  
 [Active Script Profiler\-Schnittstelle](../../winscript/reference/active-script-profiler-interfaces.md)