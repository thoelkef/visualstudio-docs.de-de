---
title: PROFILER_SCRIPT_TYPE-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: e08583f9bb914adfbd144715646991c6070f3f32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574571"
---
# <a name="profiler_script_type-enumeration"></a>PROFILER_SCRIPT_TYPE-Enumeration
Legt den Typ des Skripts fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
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
|PROFILER_SCRIPT_TYPE_USER|Gibt den Benutzer geschriebenen Skriptcode an.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Gibt Skriptcode an, der während der Ausführung dynamisch generiert wird.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Gibt den Skripttyp für Native Funktionen und Objekte an, die von der Skript-Engine definiert werden.|  
|PROFILER_SCRIPT_TYPE_DOM|Gibt einen-Dokumentobjektmodell (DOM) von Internet Explorer an, z. b. einen aufzurufenden `document.getElementById`-Methode.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script Profiler-Konstanten, Enumerationen und Strukturen](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)