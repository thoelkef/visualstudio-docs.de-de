---
title: IActiveScriptProfilerCallback-Schnittstelle | Microsoft Docs
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
ms.openlocfilehash: f4dc4b9d4e3b1f83a37e64e3a85387fd378d3ca7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724580"
---
# <a name="iactivescriptprofilercallback-interface"></a>IActiveScriptProfilerCallback-Schnittstelle
Enthält Methoden, die vom Skriptmodul verwendet werden, um ein Objekt des Profilers zu benachrichtigen, wenn Ereignisse auftreten. Diese Schnittstelle wird durch das Profilerobjekt implementiert.  
  
## <a name="methods"></a>Methoden  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Wird aufgerufen, um das Profilerobjekt zu initialisieren, wenn die profilerstellung auf einem Skriptmodul gestartet wird.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Wird aufgerufen, um freizugeben, und das Profilerobjekt freigeben, wenn für ein Skriptmodul der profilerstellung beenden.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Benachrichtigt dem Profiler-Objekt, das das Skript-engine-das Skript kompiliert.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Benachrichtigt den Profiler, Objekt, das das Skript-engine-Funktion gefunden, beim Kompilieren eines Skripts.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Benachrichtigt den Profilerobjekt, das Skriptmodul einen Funktionsaufruf auszuführen, der kein Aufruf in das Document Objekt Model (DOM) ist.|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Benachrichtigt den Profiler, dass das Objekt, das Skriptmodul beendet die Ausführung einer Funktion aufrufen, die kein Aufruf in das DOM ist|  
  
## <a name="remarks"></a>Hinweise  
 Benachrichtigung über Funktionsaufrufe in das Document Objekt Model (DOM) erfolgt durch die [IActiveScriptProfilerCallback2-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
>  Rufen Sie die folgenden Methoden zum Hinzufügen der Möglichkeit zum Starten und Beenden der profilerstellung beim Ausführen eines Skripts. Mithilfe dieser Methoden können Sie die vollständige Aufrufliste abrufen, wenn [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] beim Starten oder Beenden der profilerstellung ausgeführt wird.  
>   
>  -   Rufen Sie [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) dem Profiler benachrichtigt, dass Sie die profilerstellung gestartet haben.  
> -   Rufen Sie [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) dem Profiler benachrichtigt, dass Sie bald profilerstellung beendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Profilerschnittstelle](../../winscript/reference/active-script-profiler-interfaces.md)