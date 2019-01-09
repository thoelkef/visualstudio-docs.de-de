---
title: IActiveScriptProfilerCallback::OnFunctionExit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: fb3f71e9a8a383e2362bacb17698f4eec58f464e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092201"
---
# <a name="iactivescriptprofilercallbackonfunctionexit"></a>IActiveScriptProfilerCallback::OnFunctionExit
Benachrichtigt den Profiler, dass das Objekt, dass die Skript-Engine beendet die Ausführung einer Funktion aufrufen, keinen Aufruf in das Document Objekt Model (DOM) ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>Parameter  
 `scriptId`  
 [in] Die eindeutige ID des Skripts, das die Funktion gehört. Diese ID wird von der Skript-Engine zugewiesen.  
  
 `functionId`  
 [in] Die eindeutige ID der Funktion. Diese ID wird von der Skript-Engine zugewiesen.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Rückgabewert dieser Methode wird von der Skript-Engine ignoriert.  
  
## <a name="remarks"></a>Hinweise  
 Für DOM-Aufrufe, die Skript-Engine ruft [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) anstelle von `IActiveScriptProfilerCallback::OnFunctionExit`. Dies ist aufgrund der großen Anzahl von eindeutigen Methoden und Eigenschaften im DOM.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)   
 [IActiveScriptProfilerCallback-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)