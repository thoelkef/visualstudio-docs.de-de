---
title: IActiveScriptProfilerControl-Schnittstelle | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0d598302ae78ca0b2a1e7c1f94c949800378a2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724670"
---
# <a name="iactivescriptprofilercontrol-interface"></a>IActiveScriptProfilerControl-Schnittstelle
Implementiert das Skriptmodul, das profilerstellung unterstützt. In der Regel ein Objekt, implementiert die `IActiveScriptProfilerControl` implementiert außerdem die [IActiveScript](../../winscript/reference/iactivescript.md) Schnittstelle. In diesem Fall erhalten Sie ein Handle für die `IActiveScriptProfilerControl` Schnittstelle durch Aufrufen der `IUnknown::QueryInterface` -Methode für das Objekt. Die Schnittstelle enthält die erforderlichen Methoden für das Skriptmodul für die profilerstellung starten und beenden.  
  
## <a name="methods"></a>Methoden  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Mit der profilerstellung auf das Skriptmodul beginnt.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Legt den Profiler Event Maske in das Skriptmodul fest.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Beendet die profilerstellung auf dem Skriptmodul.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Profilerschnittstelle](../../winscript/reference/active-script-profiler-interfaces.md)