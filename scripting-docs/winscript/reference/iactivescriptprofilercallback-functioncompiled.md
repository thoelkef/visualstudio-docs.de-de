---
title: IActiveScriptProfilerCallback::FunctionCompiled | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.FunctionCompiled
apilocation:
- scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a039f7a682babebdccad276adce55e69bb8e0bc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993318"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Benachrichtigt dem Profiler-Objekt, das die Skript-Engine-eine Funktion auftreten, wenn Sie ein Skript zu kompilieren.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parameter  
 `functionId`  
 [in] Die eindeutige ID der Funktion. Diese ID wird von der Skript-Engine zugewiesen.  
  
 `scriptId`  
 [in] Die eindeutige ID des Skripts, das die Funktion gehört.  
  
 `pwszFunctionName`  
 [in] Der Name der Funktion, oder Null für eine anonyme Funktion.  
  
 `pwszFunctionNameHint`  
 [in] Der abgeleitete Name der Funktion, oder Null, wenn das Skriptmodul nicht über einen beliebigen Namen ableitet.  
  
 `pIDebugDocumentContext`  
 [in] Falls verfügbar, der Zeiger auf ein `IUnknown` -Schnittstelle, die der Profiler für die Abfrage muss eine [IDebugDocumentContext-Schnittstelle](../../winscript/reference/idebugdocumentcontext-interface.md) Zeiger. Andernfalls NULL.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Rückgabewert dieser Methode wird von der Skript-Engine ignoriert.  
  
## <a name="remarks"></a>Hinweise  
 Die Skript-Engine kann den Dokumentenkontext bereitstellen, nur dann, wenn dies vom Host unterstützt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerCallback-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)