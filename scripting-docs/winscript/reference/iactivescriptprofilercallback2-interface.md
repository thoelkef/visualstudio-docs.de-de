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
ms.openlocfilehash: b0a0df287db477c5bf768798f200ea0d97de6d1e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63385943"
---
# <a name="iactivescriptprofilercallback2-interface"></a>IActiveScriptProfilerCallback2-Schnittstelle
Bietet Methoden, die von der Skript-Engine verwendet werden, um eine Profilerobjekt zu benachrichtigen, wenn (DOKUMENTOBJEKTMODELL) Ereignisse auftreten. Diese Schnittstelle wird von der Profilerobjekt implementiert.  
  
## <a name="methods"></a>Methoden  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Benachrichtigt den Profilerobjekt, das die Skript-Engine vor sich geht einen DOM-Funktionsaufruf ausgeführt.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Benachrichtigt den Profiler, dass die Ausführung eines Funktionsaufrufs DOM-Objekt, das die Skript-Engine-abgeschlossen wird.|  
  
## <a name="remarks"></a>Hinweise  
 Die `IActiveScriptProfilerCallback2` Schnittstelle, die erstmalig in Internet Explorer 9.  
  
 Benachrichtigung von Funktionsaufrufen, die keine Aufrufe in das DOM sind erfolgt über die [IActiveScriptProfilerCallback-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
> Rufen Sie die folgenden Methoden zum Hinzufügen der Möglichkeit zum Starten und Beenden der profilerstellung, wenn ein Skript ausgeführt wird. Sie können mit diesen Methoden, die vollständige Aufrufliste abrufen, wenn [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] beim Starten oder Beenden der profilerstellung ausgeführt wird.  
> 
> - Rufen Sie [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) dem Profiler benachrichtigt, dass Sie die profilerstellung gestartet wurde.  
>   - Rufen Sie [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) dem Profiler benachrichtigt, dass Sie bald profilerstellung beendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Profilerschnittstelle](../../winscript/reference/active-script-profiler-interfaces.md)