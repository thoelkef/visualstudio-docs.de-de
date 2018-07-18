---
title: PROFILER_SCRIPT_TYPE-Enumeration | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_SCRIPT_TYPE
apilocation:
- scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 279969ec0b50f705e39d2e29e700adc1e833ead3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734120"
---
# <a name="profilerscripttype-enumeration"></a>PROFILER_SCRIPT_TYPE-Enumeration
Legt den Typ des Skripts fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## <a name="members"></a>Member  
  
|Member|Beschreibung|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|Gibt die vom Benutzer erstellter Skriptcode.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Gibt den Code, der während der Ausführung dynamisch generiert wird.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Gibt den Skripttyp für systemeigene Funktionen und Objekte, die vom Skriptmodul definiert sind.|  
|PROFILER_SCRIPT_TYPE_DOM|Gibt einen Aufruf in den (DOKUMENTOBJEKTMODELL) von Internet Explorer, z. B. einen Aufruf der `document.getElementById` Methode.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script Profiler-Konstanten, Enumerationen und Strukturen](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)