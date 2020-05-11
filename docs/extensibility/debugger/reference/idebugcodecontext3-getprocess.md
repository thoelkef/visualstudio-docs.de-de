---
title: IDebugCodeContext3::GetProcess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3::GetProcess
ms.assetid: e082e494-2255-4d9d-a5a9-6dadd904bea8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8d169f86548e97d4bb745e1ba91f39782de97cbc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734174"
---
# <a name="idebugcodecontext3getprocess"></a>IDebugCodeContext3::GetProcess
Ruft einen Verweis auf die Schnittstelle des Debugprozesses ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetProcess(
    IDebugProcess2 **ppProcess
);
```

```csharp
public int GetProcess(
    out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>Parameter
`ppProcess`\
[out] Verweis auf die Debugprozessschnittstelle.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese Methode für ein **CDebugCodeContext-Objekt** implementiert wird, das die [IDebugBeforeSymbolSearchEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) verfügbar macht.

```cpp
HRESULT CDebugCodeContext::GetProcess(IDebugProcess2** ppProcess)
{
    HRESULT hr = S_OK;
    CComPtr<CDebugEngine> pEngine;
    CComPtr<IDebugPort2> pPort2;

    IfFalseGo( ppProcess, E_INVALIDARG );
    *ppProcess = NULL;

    IfFalseGo( m_pProgram, E_FAIL );
    IfFailGo( ((CDebugProgram *)m_pProgram)->GetEngine(&pEngine) );
    IfFailGo( pEngine->GetSDMProcess(ppProcess) );

Error:

    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)
