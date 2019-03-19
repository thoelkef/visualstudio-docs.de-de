---
title: IActiveScriptProfilerControl-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 86f4fb8dea97930f717800a14a27740b76eb6c2e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160757"
---
# <a name="iactivescriptprofilercontrol-interface"></a>IActiveScriptProfilerControl-Schnittstelle
Durch die Skript-Engine, die profilerstellung unterstützt implementiert. In der Regel auf ein Objekt, implementiert die `IActiveScriptProfilerControl` implementiert auch die [IActiveScript](../../winscript/reference/iactivescript.md) Schnittstelle. In diesem Fall erhalten Sie ein Handle für die `IActiveScriptProfilerControl` Schnittstelle durch Aufrufen der `IUnknown::QueryInterface` Methode für das Objekt. Die Schnittstelle enthält die erforderlichen Methoden für das Beenden und starten die profilerstellung auf die Skript-Engine.  
  
## <a name="methods"></a>Methoden  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Startet die profilerstellung auf die Skript-Engine.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Legt den Profiler Ereignismaske in die Skript-Engine fest.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Beendet die profilerstellung auf die Skript-Engine.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Profilerschnittstelle](../../winscript/reference/active-script-profiler-interfaces.md)