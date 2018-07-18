---
title: IActiveScriptProfilerCallback::ScriptCompiled | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.ScriptCompiled
apilocation:
- scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ea1823087b323f2acc9b87edfce48bbe9f924bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724700"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Benachrichtigt dem Profiler-Objekt, das das Skript-engine-ein Skript kompiliert. Diese Methode wird für jedes Skript aufgerufen, das kompiliert wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parameter  
 `scriptId`  
 [in] Die eindeutige ID des Skripts, das kompiliert wurde. Diese ID wird vom Skriptmodul zugewiesen.  
  
 `type`  
 [in] Der Typ des Skripts, das kompiliert wurde. Die Werte werden definiert, [PROFILER_SCRIPT_TYPE-Enumeration](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 [in] Falls verfügbar, ein Zeiger auf ein `IUnknown` -Schnittstelle, die der Profiler für die Abfrage ausführen muss ein [IDebugDocumentContext-Schnittstelle](../../winscript/reference/idebugdocumentcontext-interface.md) Zeiger. Dies wird, andernfalls null sein.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Rückgabewert dieser Methode wird vom Skriptmodul ignoriert.  
  
## <a name="remarks"></a>Hinweise  
 Das Skriptmodul bieten den Dokumentenkontext, nur, wenn dies vom Host unterstützt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerCallback-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)