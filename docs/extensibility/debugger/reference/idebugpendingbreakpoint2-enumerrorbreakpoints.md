---
title: IDebugPendingBreakpoint2::EnumErrorBreakpoints | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::EnumErrorBreakpoints
helpviewer_keywords:
- IDebugPendingBreakpoint2::EnumErrorBreakpoints method
- EnumErrorBreakpoints method
ms.assetid: 2f9a9720-c1ac-4430-8f28-200d85360452
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3030eb1a272b7142d942c05d3320c67c51f2bd90
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872181"
---
# <a name="idebugpendingbreakpoint2enumerrorbreakpoints"></a>IDebugPendingBreakpoint2::EnumErrorBreakpoints
Ruft eine Liste aller Fehler Haltepunkte, die von diesem ausstehender Haltepunkt geführt haben.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumErrorBreakpoints( 
   BP_ERROR_TYPE                 bpErrorType,
   IEnumDebugErrorBreakpoints2** ppEnum
);
```

```csharp
int EnumErrorBreakpoints( 
   enum_BP_ERROR_TYPE              bpErrorType,
   out IEnumDebugErrorBreakpoints2 ppEnum
);
```

#### <a name="parameters"></a>Parameter
 `bpErrorType`

 [in] Eine Kombination von Werten aus der [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) -Enumeration, die wählt den Typ von Fehlern, die aufgelistet werden.

 `ppEnum`

 [out] Gibt eine [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) -Objekt, das eine Liste der enthält [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) Objekte.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Gibt `E_BP_DELETED` , wenn der Haltepunkt gelöscht wurde.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine einfache `CPendingBreakpoint` -Objekt, das macht die [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) Schnittstelle.

```cpp
HRESULT CPendingBreakpoint::EnumErrorBreakpoints(
   BP_ERROR_TYPE bpErrorType,
   IEnumDebugErrorBreakpoints2** ppEnum)
{
   HRESULT hr;

   // Verify that the passed IEnumDebugErrorBreakpoints2 interface pointer
   // is valid.
   if (ppEnum)
   {
      // Verify that the pending breakpoint has not been deleted. If
      // deleted, then return hr = E_BP_DELETED.
      if (m_state.state != PBPS_DELETED)
      {
         // Verify that this error is not a warning.
         // All errors supported by this DE are errors, not warnings.
         if (IsFlagSet(bpErrorType, BPET_TYPE_ERROR) && m_pErrorBP)
         {
            // Get the error breakpoint.
            CComPtr<IDebugErrorBreakpoint2> spErrorBP;
            hr = m_pErrorBP->QueryInterface(&spErrorBP);
            assert(hr == S_OK);
            if (hr == S_OK)
            {
               // Create the error breakpoint enumerator.
               CComObject<CEnumDebugErrorBreakpoints>* pErrorEnum;
               hr = CComObject<CEnumDebugErrorBreakpoints>::CreateInstance(&pErrorEnum);
               assert(hr == S_OK);
               if (hr == S_OK)
               {
                  // Initialize the enumerator of error breakpoints with
                  // the IDebugErrorBreakpoint2 information.
                  IDebugErrorBreakpoint2* rgpErrorBP[] = { spErrorBP.p };
                  hr = pErrorEnum->Init(rgpErrorBP, &(rgpErrorBP[1]), NULL, AtlFlagCopy);
                  if (hr == S_OK)
                  {
                     // Verify that the passed IEnumDebugErrorBreakpoints2
                     // interface can be queried by the created
                     // CEnumDebugErrorBreakpoints object.
                     hr = pErrorEnum->QueryInterface(ppEnum);
                     assert(hr == S_OK);
                  }

                  // Otherwise, delete the CEnumDebugErrorBreakpoints
                  // object.
                  if (FAILED(hr))
                  {
                     delete pErrorEnum;
                  }
               }
            }
         }
         else
         {
            hr = S_FALSE;
         }
      }
      else
      {
         hr = E_BP_DELETED;
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
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)