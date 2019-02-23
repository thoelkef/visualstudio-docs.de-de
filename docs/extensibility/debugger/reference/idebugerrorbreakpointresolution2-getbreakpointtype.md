---
title: IDebugErrorBreakpointResolution2::GetBreakpointType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpointResolution2::GetBreakpointType
helpviewer_keywords:
- IDebugErrorBreakpointResolution2::GetBreakpointType
ms.assetid: 0bdb1152-4752-4464-ae7c-6d666dc293b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a733a600c8e8f3e346ffffdac306982c88994709
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707678"
---
# <a name="idebugerrorbreakpointresolution2getbreakpointtype"></a>IDebugErrorBreakpointResolution2::GetBreakpointType
Ruft den Haltepunkttyp ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetBreakpointType(
    BP_TYPE* pBPType
);
```

```csharp
int GetBreakpointType(
    out enum_BP_TYPE pBPType
);
```

#### <a name="parameters"></a>Parameter
`pBPType`

 [out] Gibt einen Wert aus der [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) Enumeration, die den Typ des Haltepunkts beschreibt.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
Diese Methode gibt den Typ des Haltepunkts, die nicht zu binden, muss ein Fehlerereignis-Haltepunkt.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine einfache `CDebugErrorBreakpointResolution` -Objekt, das macht die [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) Schnittstelle.

```
HRESULT CDebugErrorBreakpointResolution::GetBreakpointType(BP_TYPE* pBPType)
{
    HRESULT hr;

    if (pBPType)
    {
        // Set default BP_TYPE.
        *pBPType = BPT_NONE;

        // Check if the BPERESI_BPRESLOCATION flag is set in BPERESI_FIELDS.
        if (IsFlagSet(m_bpErrorResolutionInfo.dwFields, BPERESI_BPRESLOCATION))
        {
            // Set the new BP_TYPE.
            *pBPType = m_bpErrorResolutionInfo.bpResLocation.bpType;
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
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
