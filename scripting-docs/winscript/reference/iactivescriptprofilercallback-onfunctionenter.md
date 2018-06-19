---
title: IActiveScriptProfilerCallback::OnFunctionEnter | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d9af9dc5ce1f4cb0eb5c328c90c20184111afd9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724600"
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
Benachrichtigt den Profilerobjekt, das Skriptmodul einen Funktionsaufruf auszuführen, der kein Aufruf in das Document Objekt Model (DOM) ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT OnFunctionEnter(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>Parameter  
 `scriptId`  
 [in] Die eindeutige ID des Skripts, die die Funktion gehört. Diese ID wird vom Skriptmodul zugewiesen.  
  
 `functionId`  
 [in] Die eindeutige ID der Funktion. Diese ID wird vom Skriptmodul zugewiesen.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Rückgabewert dieser Methode wird vom Skriptmodul ignoriert.  
  
## <a name="remarks"></a>Hinweise  
 DOM-Aufrufe, erfordert das Skriptmodul [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) anstelle von `IActiveScriptProfilerCallback::OnFunctionEnter`. Dies ist aufgrund der großen Anzahl von eindeutigen Methoden und Eigenschaften im DOM.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [IActiveScriptProfilerCallback-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)