---
title: IDebugCodeContext3::GetModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3::GetModule
ms.assetid: 8e4317b8-8255-486c-a896-a68ed94f8aa1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 20e4bbc32aef11c91e4f5c642bb48acb26633fe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734197"
---
# <a name="idebugcodecontext3getmodule"></a>IDebugCodeContext3::GetModule
Ruft einen Verweis auf die Schnittstelle des Debugmoduls ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetModule(
    IDebugModule2 **ppModule
);
```

```csharp
public int GetModule(
    out IDebugModule2 ppModule
);
```

## <a name="parameters"></a>Parameter
`ppModule`\
[out] Verweis auf die Debugmodulschnittstelle.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese Methode für ein **CDebugCodeContext-Objekt** implementiert wird, das die [IDebugBeforeSymbolSearchEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) verfügbar macht.

```cpp
HRESULT CDebugCodeContext::GetModule(IDebugModule2** ppModule)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;

    IfFalseGo( ppModule, E_INVALIDARG );
    *ppModule = NULL;

    IfFailGo( this->GetModule(&pModule) );
    IfFailGo( pModule->QueryInterface(IID_IDebugModule2, (void**) ppModule) );

Error:

    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)
