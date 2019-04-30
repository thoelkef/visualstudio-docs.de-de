---
title: IActiveScriptProfilerCallback::OnFunctionEnter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionEnter
apilocation:
- scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b8410fba08c1799d88532266c022d811c9553fd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993383"
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
Benachrichtigt den Profilerobjekt, das die Skript-Engine einen Funktionsaufruf, der keinem Aufruf in das Document Objekt Model (DOM) ist, ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnFunctionEnter(  
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
 Für DOM-Aufrufe, die Skript-Engine ruft [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) anstelle von `IActiveScriptProfilerCallback::OnFunctionEnter`. Dies ist aufgrund der großen Anzahl von eindeutigen Methoden und Eigenschaften im DOM.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [IActiveScriptProfilerCallback-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)