---
title: 'Iactivescriptprofilercallback:: onfunctionenter | Microsoft-Dokumentation'
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
ms.openlocfilehash: 6157638353712d6f376fa1eb46a68980b493a5c3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571684"
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
Benachrichtigt das Profiler-Objekt, dass die Skript-Engine im Begriff ist, einen Funktions aufrut auszuführen, der kein Dokumentobjektmodell (DOM) aufruft.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnFunctionEnter(  
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
 Bei Dom-aufrufen Ruft die Skript-Engine " [IActiveScriptProfilerCallback2:: onfunctionenterbyname](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) " anstelle von "`IActiveScriptProfilerCallback::OnFunctionEnter`" auf. Dies liegt an der großen Anzahl von eindeutigen Methoden und Eigenschaften im Dom.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [IActiveScriptProfilerCallback-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)