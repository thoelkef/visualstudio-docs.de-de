---
title: 'Iactivescriptprofilercallback:: scriptkompiliert | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: f7252134fc86bfd63b74a181b18327212a1b2dc1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571663"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Benachrichtigt das Profiler-Objekt, dass die Skript-Engine ein Skript kompiliert hat. Diese Methode wird für jedes Skript aufgerufen, das kompiliert wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parameter  
 `scriptId`  
 in Die eindeutige ID des Skripts, das kompiliert wurde. Diese ID wird von der Skript-Engine zugewiesen.  
  
 `type`  
 in Der Typ des Skripts, das kompiliert wurde. Die Werte werden in der [PROFILER_SCRIPT_TYPE-Enumeration](../../winscript/reference/profiler-script-type-enumeration.md)definiert.  
  
 `pIDebugDocumentContext`  
 in Falls verfügbar, ein Zeiger auf eine `IUnknown`-Schnittstelle, die der Profiler für einen [idebugdocumentcontext-Schnittstellen](../../winscript/reference/idebugdocumentcontext-interface.md) Zeiger Abfragen muss. Andernfalls ist der Wert NULL.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Rückgabewert dieser Methode wird von der Skript-Engine ignoriert.  
  
## <a name="remarks"></a>Hinweise  
 Die Skript-Engine kann den Dokument Kontext nur dann bereitstellen, wenn dies vom Host unterstützt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerCallback-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)