---
title: 'Iactivescriptprofilercallback:: functionkompiliert | Microsoft-Dokumentation'
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
ms.openlocfilehash: a17ce7548a6524df6911cdf952393020472b88ed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576474"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Benachrichtigt das Profiler-Objekt, dass die Skript-Engine beim Kompilieren eines Skripts eine Funktion gefunden hat.  
  
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
 in Die eindeutige ID der Funktion. Diese ID wird von der Skript-Engine zugewiesen.  
  
 `scriptId`  
 in Die eindeutige ID des Skripts, zu dem die Funktion gehört.  
  
 `pwszFunctionName`  
 in Der Name der Funktion oder NULL für eine anonyme Funktion.  
  
 `pwszFunctionNameHint`  
 in Der Rückschluss Name der Funktion oder NULL, wenn die Skript-Engine keinen Namen ableiten kann.  
  
 `pIDebugDocumentContext`  
 in Falls verfügbar, der Zeiger auf eine `IUnknown`-Schnittstelle, die der Profiler für einen [idebugdocumentcontext-Schnittstellen](../../winscript/reference/idebugdocumentcontext-interface.md) Zeiger Abfragen muss. Andernfalls NULL.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Rückgabewert dieser Methode wird von der Skript-Engine ignoriert.  
  
## <a name="remarks"></a>Hinweise  
 Die Skript-Engine kann den Dokument Kontext nur dann bereitstellen, wenn dies vom Host unterstützt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerCallback-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)