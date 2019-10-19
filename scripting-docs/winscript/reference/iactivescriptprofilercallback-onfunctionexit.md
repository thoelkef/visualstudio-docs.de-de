---
title: 'Iactivescriptprofilercallback:: onfunctionexit | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionExit
apilocation:
- scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87801b7873e43498031264ff4719fb47eca99f40
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571680"
---
# <a name="iactivescriptprofilercallbackonfunctionexit"></a>IActiveScriptProfilerCallback::OnFunctionExit
Benachrichtigt das Profiler-Objekt, dass die Skript-Engine das Ausführen eines Funktions Aufrufes beendet hat, der kein Aufrufe der Dokumentobjektmodell (DOM) ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>Parameter  
 `scriptId`  
 in Die eindeutige ID des Skripts, zu dem die Funktion gehört. Diese ID wird von der Skript-Engine zugewiesen.  
  
 `functionId`  
 in Die eindeutige ID der Funktion. Diese ID wird von der Skript-Engine zugewiesen.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Rückgabewert dieser Methode wird von der Skript-Engine ignoriert.  
  
## <a name="remarks"></a>Hinweise  
 Bei Dom-aufrufen Ruft die Skript-Engine " [IActiveScriptProfilerCallback2:: onfunctionexitbyname](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) " anstelle von "`IActiveScriptProfilerCallback::OnFunctionExit`" auf. Dies liegt an der großen Anzahl von eindeutigen Methoden und Eigenschaften im Dom.  
  
## <a name="see-also"></a>Siehe auch  
 [Iactivescriptprofilercallback:: onfunctionenter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)    
 [IActiveScriptProfilerCallback-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)