---
title: IActiveScriptProfilerCallback::ScriptCompiled | Microsoft-Dokumentation
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
ms.openlocfilehash: bf653e5623506a68e6353e3d9f97077592e87941
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091506"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Benachrichtigt den Profiler, dass das Objekt, das die Skript-Engine-ein-Skript kompiliert. Diese Methode wird für jedes Skript aufgerufen, die kompiliert wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parameter  
 `scriptId`  
 [in] Die eindeutige ID des Skripts, das kompiliert wurde. Diese ID wird von der Skript-Engine zugewiesen.  
  
 `type`  
 [in] Der Typ des Skripts, das kompiliert wurde. Die Werte werden definiert [PROFILER_SCRIPT_TYPE-Enumeration](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 [in] Wenn möglich, ein Zeiger auf ein `IUnknown` -Schnittstelle, die der Profiler für die Abfrage muss eine [IDebugDocumentContext-Schnittstelle](../../winscript/reference/idebugdocumentcontext-interface.md) Zeiger. Dies wird, andernfalls null sein.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Rückgabewert dieser Methode wird von der Skript-Engine ignoriert.  
  
## <a name="remarks"></a>Hinweise  
 Die Skript-Engine kann den Dokumentenkontext bereitstellen, nur dann, wenn dies vom Host unterstützt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerCallback-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)