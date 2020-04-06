---
title: IDebugBreakpointErrorEvent2::GetErrorBreakpoint | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
helpviewer_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
ms.assetid: e5acfd19-ac17-47f3-a31a-b2aa8baca36d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe22f18d4574ffde48cea975bff8d8f5801ca465
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735075"
---
# <a name="idebugbreakpointerrorevent2geterrorbreakpoint"></a>IDebugBreakpointErrorEvent2::GetErrorBreakpoint
Ruft ein [IDebugErrorBreakpoint2-Objekt](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) ab, das den Grund beschreibt, warum ein Haltepunkt nicht gebunden wurde.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetErrorBreakpoint( 
    IDebugErrorBreakpoint2** ppErrorBP
);
```

```csharp
int GetErrorBreakpoint( 
    out IDebugErrorBreakpoint2 ppErrorBP
);
```

## <a name="parameters"></a>Parameter
`ppErrorBP`\
[out] Gibt ein [IDebugErrorBreakpoint2-Objekt](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) zurück, das die Warnung oder den Fehler beschreibt.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Nachdem `IDebugErrorBreakpoint2` die Schnittstelle abgerufen wurde, rufen Sie die [GetBreakpointResolution-Methode](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) auf, um ein [IDebugErrorBreakpointResolution2-Objekt](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) abzurufen. Anschließend kann die [GetResolutionInfo-Methode](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) verwendet werden, um einen ungültigen Speicherort, einen ungültigen Ausdruck oder Gründe zu ermitteln, warum der ausstehende Haltepunkt nicht gebunden wurde, z. B. Code, der noch nicht geladen wurde, usw.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese Methode für ein **CBreakpointSetDebugEventBase-Objekt** implementiert wird, das die [IDebugBreakpointErrorEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) verfügbar macht.

```cpp
STDMETHODIMP CBreakpointErrorDebugEventBase::GetErrorBreakpoint(
    IDebugErrorBreakpoint2 **ppbp)
{
    HRESULT hRes = E_FAIL;

    if ( ppbp )
    {
        if ( m_pError )
        {
            *ppbp = m_pError;

            m_pError->AddRef();

            hRes = S_OK;
        }
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
