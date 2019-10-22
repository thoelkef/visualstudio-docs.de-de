---
title: Iactivescriptprofilercontrol-Schnittstelle | Microsoft-Dokumentation
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
ms.openlocfilehash: ef127e3a4463d112b9ea424702fb2650c80cce7d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571597"
---
# <a name="iactivescriptprofilercontrol-interface"></a>IActiveScriptProfilerControl-Schnittstelle
Implementiert von der Skript-Engine, die die Profilerstellung unterstützt. In der Regel implementiert ein Objekt, das den `IActiveScriptProfilerControl` implementiert, auch die [IActiveScript](../../winscript/reference/iactivescript.md) -Schnittstelle. In diesem Fall können Sie ein Handle für die `IActiveScriptProfilerControl`-Schnittstelle abrufen, indem Sie die `IUnknown::QueryInterface`-Methode für das-Objekt aufrufen. Die-Schnittstelle stellt die erforderlichen Methoden zum Beenden und Starten der Profilerstellung für die Skript-Engine bereit.  
  
## <a name="methods"></a>Methoden  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Startet die Profilerstellung für die Skript-Engine.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Legt die Profiler-Ereignis Maske in der Skript-Engine fest.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Beendet die Profilerstellung für die Skript-Engine.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Profilerschnittstelle](../../winscript/reference/active-script-profiler-interfaces.md)