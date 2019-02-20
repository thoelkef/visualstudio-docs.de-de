---
title: IDebugBreakpointResolution2::GetBreakpointType | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointResolution2::GetBreakpointType
helpviewer_keywords:
- IDebugBreakpointResolution2::GetBreakpointType
ms.assetid: 2b707fb9-f703-4c78-91bf-7434f57790a0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91d1321e99705bd4173edacb13c99223c10eb2d1
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413513"
---
# <a name="idebugbreakpointresolution2getbreakpointtype"></a>IDebugBreakpointResolution2::GetBreakpointType
Ruft den Typ des Haltepunkts durch diese Lösung dargestellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetBreakpointType( 
    BP_TYPE* pBPType
);
```

```csharp
int GetBreakpointType( 
    out enum_ BP_TYPE pBPType
);
```

#### <a name="parameters"></a>Parameter
`pBPType`  
[out] Gibt einen Wert aus der [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) -Enumeration, der den Typ des Haltepunkts angibt.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`; gibt andernfalls einen Fehlercode zurück. Gibt E_FAIL zurück, wenn die `bpResLocation` im zugehörigen Feld [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Struktur ist ungültig.

## <a name="remarks"></a>Hinweise
Der Haltepunkt kann z. B. einen Code oder ein Datenhaltepunkt sein.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine einfache `CDebugBreakpointResolution` -Objekt, das macht die [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) Schnittstelle.

```
HRESULT CDebugBreakpointResolution::GetBreakpointType(BP_TYPE* pBPType)
{
    HRESULT hr;

    if (pBPType)
    {
        // Set default BP_TYPE.
        *pBPType = BPT_NONE;

        // Check if the BPRESI_BPRESLOCATION flag is set in BPRESI_FIELDS.
        if (IsFlagSet(m_bpResolutionInfo.dwFields, BPRESI_BPRESLOCATION))
        {
            // Set the new BP_TYPE.
            *pBPType = m_bpResolutionInfo.bpResLocation.bpType;
            hr = S_OK;
        }
        else
        {
            hr = E_FAIL;
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Siehe auch
[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)  
[BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)  
[BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)  
[BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
