---
title: Active Script Profiler Schnittstellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ab8a1f0d-393c-4d6a-94c1-d5b8aa76788c
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e85d511bfeec2ddda4b68b0297b18ac541949a4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160562"
---
# <a name="active-script-profiler-interfaces"></a>Active Script Profiler-Schnittstelle
Active Script-Profilerschnittstellen geben Ihnen die Möglichkeit, Profilerstellungsereignisse von der [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Engine zu empfangen.  
  
 Die Headerdatei "activprof.h" stellt die Schnittstellen bereit, die in diesem Abschnitt aufgeführt werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 Die folgenden Schnittstellen aktivieren die Profilerstellung:  
  
- [IActiveScriptProfilerControl-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol-interface.md)  
  
- [IActiveScriptProfilerControl2-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)  
  
- [IActiveScriptProfilerControl3-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol3-interface.md)  
  
- [IActiveScriptProfilerControl5-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol5-interface.md)  
  
- [IActiveScriptProfilerCallback-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)  
  
- [IActiveScriptProfilerCallback2-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback2-interface.md)  
  
- [IActiveScriptProfilerCallback3-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback3-interface.md)  
  
- [IActiveScriptProfilerHeapEnum-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)  
  
  Der folgende Abschnitt führt die Enumerationen auf, die für die Profilerstellung verwendet werden:  
  
- [Konstanten, Enumerationen und Strukturen für den Active Script-Profiler](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)  
  
> [!NOTE]
>  Die Active Script-Profilerschnittstellen waren erstmalig in Internet Explorer 8 enthalten. Die Schnittstellen `IActiveScriptProfilerControl2` und `IActiveScriptProfilerCallback2` waren erstmalig in Internet Explorer 9 enthalten. Die [IActiveScriptProfilerControl3 Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol3-interface.md), [IActiveScriptProfilerCallback3 Schnittstelle](../../winscript/reference/iactivescriptprofilercallback3-interface.md), und [IActiveScriptProfilerHeapEnum Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) Schnittstellen mit Internet Explorer 10 zuerst veröffentlicht. Die [IActiveScriptProfilerControl5 Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol5-interface.md) erschien mit Internet Explorer 11.  
>   
>  In Internet Explorer 8 und in Internet Explorer 9 verwendet nur die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Programmiersprache diese Schnittstellen, um Skriptprofilerstellung zu unterstützen.  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Script-Schnittstellenreferenz](../../winscript/reference/windows-script-interfaces-reference.md)